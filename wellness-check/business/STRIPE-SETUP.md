# Stripe Product Catalog Setup

**Phase 1: Consumer Plans Only** (Family focus)

---

## Product Structure in Stripe Dashboard

### Product 1: Wellness Check Free Tier
```
Product Name: Wellness Check - Free
Description: Basic wellness monitoring for 1 senior
Type: One-time (free, no recurring charge)
Metadata:
  - plan_type: free
  - max_seniors: 1
  - max_family_members: 1
  - features: basic_alerts
```

### Product 2: Wellness Check Family Plan
```
Product Name: Wellness Check - Family
Description: Premium wellness monitoring for families
Type: Recurring (subscription)

Pricing:
  - Monthly: $9.99/month
  - Annual: $99/year (save 17%)

Metadata:
  - plan_type: family
  - max_seniors: 2
  - max_family_members: 5
  - features: all
  - tier_level: 2
```

### Product 3: Wellness Check Premium Plan
```
Product Name: Wellness Check - Premium
Description: Unlimited wellness monitoring
Type: Recurring (subscription)

Pricing:
  - Monthly: $14.99/month
  - Annual: $149/year (save 17%)

Metadata:
  - plan_type: premium
  - max_seniors: unlimited
  - max_family_members: unlimited
  - features: all + health_data + smartwatch
  - tier_level: 3
```

---

## Stripe Pricing Object IDs (After Setup)

Once created in Stripe Dashboard, you'll get IDs like:

```
Free:        price_1Abc2Def3Ghi4Jkl  (one-time, $0)
Family-Mo:   price_2Mno3Pqr4Stu5Vwx  ($9.99/mo)
Family-Yr:   price_6Yza1Bcd2Efg3Hij  ($99/yr)
Premium-Mo:  price_4Klm5Nop6Qrs7Tuv  ($14.99/mo)
Premium-Yr:  price_8Wxy9Zab0Cde1Fgh  ($149/yr)
```

**Store these in your database config table:**

```sql
CREATE TABLE stripe_prices (
  id TEXT PRIMARY KEY,
  plan_type TEXT,         -- 'family' | 'premium'
  interval TEXT,          -- 'month' | 'year'
  amount_cents INT,       -- 999 | 9900 | 1499 | 14900
  currency TEXT,          -- 'usd'
  active BOOLEAN,         -- true
  created_at TIMESTAMPTZ  -- now()
);
```

---

## Customer Portal Setup

Enable Stripe Customer Portal for:
- ✅ Subscription management (upgrade/downgrade)
- ✅ Payment method updates
- ✅ Cancellation flows
- ✅ Invoice history

**Settings:**
- Allow plan updates: YES
- Allow cancellation: YES
- Proration behavior: Charge immediately on upgrade
- Display branded portal: YES (your logo, colors)

---

## Checkout Flow Architecture

### Free Trial → Paid Conversion

```
1. User signs up → Stripe Checkout (Free Tier)
   - No card required
   - 14-day trial on Family plan OR limited free tier

2. Trial ending (day 12) → Email notification
   - "Your trial ends in 2 days"
   - CTA: Add payment method to continue

3. User adds card → Subscription active
   - Webhook: customer.subscription.created
   - Database: update subscription status

4. Recurring billing → Automatic
   - Webhook: invoice.payment_succeeded
   - Log payment, update expires_at
```

### Upgrade Flow (Free → Family)

```
1. User clicks "Upgrade" in app
2. Redirect to Stripe Checkout (Family plan)
3. User enters payment info
4. Stripe redirects back to success URL
5. Webhook received: checkout.session.completed
6. Database updated: subscription active
```

### Downgrade Flow (Premium → Family)

```
1. User clicks "Change Plan" in Customer Portal
2. Selects Family plan
3. Proration calculated (credit for unused Premium time)
4. New charge: Family plan amount - credit
5. Plan changes at period end OR immediately (your choice)
```

---

## Webhook Handlers Needed

```typescript
// Critical webhooks for subscription lifecycle

checkout.session.completed     // New subscription started
customer.subscription.created  // Subscription activated
customer.subscription.updated  // Plan changed, cancelled, etc.
customer.subscription.deleted  // Cancelled
invoice.payment_succeeded      // Payment received
invoice.payment_failed         // Card declined
payment_intent.payment_failed  // Payment failed
```

**Handler Logic:**
```typescript
// Example: subscription.updated webhook

async function handleSubscriptionUpdate(event) {
  const subscription = event.data.object;
  const customerId = subscription.customer;
  
  // Find user by Stripe customer ID
  const user = await db.users.findByStripeId(customerId);
  
  if (subscription.status === 'active') {
    // Update plan, features, limits
    await db.subscriptions.update(user.id, {
      planType: subscription.metadata.plan_type,
      maxSeniors: getLimitForPlan(subscription.metadata.plan_type),
      expiresAt: new Date(subscription.current_period_end * 1000)
    });
  }
  
  if (subscription.status === 'canceled') {
    // Grace period logic
    await db.subscriptions.update(user.id, {
      status: 'past_due',
      gracePeriodEnd: new Date(Date.now() + 14 * 24 * 60 * 60 * 1000)
    });
  }
}
```

---

## Database Schema (Subscription Tables)

```sql
-- Subscriptions table
CREATE TABLE subscriptions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID NOT NULL REFERENCES users(id),
  stripe_customer_id TEXT,
  stripe_subscription_id TEXT,
  plan_type TEXT NOT NULL,          -- 'free' | 'family' | 'premium'
  status TEXT NOT NULL,             -- 'active' | 'past_due' | 'canceled' | 'trialing'
  max_seniors INT NOT NULL,
  max_family_members INT NOT NULL,
  current_period_start TIMESTAMPTZ,
  current_period_end TIMESTAMPTZ,
  cancel_at_period_end BOOLEAN DEFAULT false,
  trial_start TIMESTAMPTZ,
  trial_end TIMESTAMPTZ,
  created_at TIMESTAMPTZ DEFAULT now(),
  updated_at TIMESTAMPTZ DEFAULT now()
);

-- Linked seniors (who this subscription covers)
CREATE TABLE senior_profiles (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  subscription_id UUID NOT NULL REFERENCES subscriptions(id),
  display_name TEXT NOT NULL,       -- "Dad", "Mom", etc.
  user_id UUID REFERENCES users(id), -- Optional (senior may not have full account)
  phone TEXT,
  privacy_settings JSONB,
  status TEXT DEFAULT 'active',
  created_at TIMESTAMPTZ DEFAULT now()
);

-- Family members with access
CREATE TABLE family_access (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  subscription_id UUID NOT NULL REFERENCES subscriptions(id),
  user_id UUID NOT NULL REFERENCES users(id),
  permission_level TEXT,            -- 'view' | 'alert' | 'admin'
  invited_at TIMESTAMPTZ DEFAULT now(),
  accepted_at TIMESTAMPTZ,
  invited_by UUID REFERENCES users(id)
);
```

---

## Frontend Integration (React)

### Checkout Button Component

```tsx
// CheckoutButton.tsx
import { loadStripe } from '@stripe/stripe-js';

const stripe = await loadStripe('pk_test_...');

function CheckoutButton({ planType, interval }) {
  const handleCheckout = async () => {
    const response = await fetch('/api/create-checkout-session', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ planType, interval })
    });
    
    const session = await response.json();
    
    // Redirect to Stripe Checkout
    const result = await stripe.redirectToCheckout({
      sessionId: session.id
    });
    
    if (result.error) {
      alert(result.error.message);
    }
  };
  
  return (
    <button onClick={handleCheckout}>
      Start {planType} Plan
    </button>
  );
}
```

### Customer Portal Button

```tsx
// ManageSubscription.tsx
function ManageSubscriptionButton() {
  const handlePortal = async () => {
    const response = await fetch('/api/create-portal-session');
    const session = await response.json();
    window.location.href = session.url;
  };
  
  return (
    <button onClick={handlePortal}>
      Manage Subscription
    </button>
  );
}
```

---

## Environment Variables Needed

```bash
# .env (Backend)
STRIPE_SECRET_KEY=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...
STRIPE_PRICE_ID_FAMILY_MONTHLY=price_...
STRIPE_PRICE_ID_FAMILY_YEARLY=price_...
STRIPE_PRICE_ID_PREMIUM_MONTHLY=price_...
STRIPE_PRICE_ID_PREMIUM_YEARLY=price_...
```

```bash
# .env (Frontend)
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=pk_test_...
```

---

## Launch Checklist

- [ ] Create Stripe account
- [ ] Create 3 products (Free, Family, Premium)
- [ ] Add pricing tiers (monthly + annual for each paid plan)
- [ ] Get price IDs, store in config
- [ ] Enable Customer Portal
- [ ] Set up webhook endpoint (`/api/webhooks/stripe`)
- [ ] Test in Stripe CLI with local dev
- [ ] Build checkout flow in app
- [ ] Build upgrade/downgrade UI
- [ ] Test end-to-end: signup → trial → payment → access
- [ ] Go live with production keys

---

## Testing with Stripe CLI

```bash
# Install Stripe CLI
brew install stripe/stripe-cli/stripe

# Login
stripe login

# Forward webhooks to localhost
stripe listen --forward-to localhost:3000/api/webhooks/stripe

# Trigger test events
stripe trigger checkout.session.completed
stripe trigger customer.subscription.created
stripe trigger invoice.payment_succeeded
stripe trigger invoice.payment_failed
```

---

## Files to Create

```
wellness-check/
├── backend/
│   ├── src/
│   │   ├── routes/
│   │   │   ├── stripe.ts          # Checkout + portal endpoints
│   │   │   └── webhooks.ts        # Stripe webhook handlers
│   │   ├── middleware/
│   │   │   └── subscription.ts    # AuthZ: check active subscription
│   │   └── models/
│   │       └── subscription.ts    # DB operations
│   └── .env
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── CheckoutButton.tsx
│   │   │   ├── PricingTable.tsx
│   │   │   └── ManageSubscription.tsx
│   │   └── pages/
│   │       ├── pricing.tsx        # /pricing landing page
│   │       └── billing.tsx        # User's billing settings
│   └── .env
└── docs/
    └── STRIPE-SETUP.md           ← This file
```

---

## Next Steps

1. **Create Stripe account** (if you haven't)
2. **Set up products + pricing** in dashboard
3. **Copy price IDs** into config
4. **Build the checkout endpoint** (backend)
5. **Build the pricing page** (frontend)
6. **Test the flow** end-to-end

Want me to help actually build any of this, or just planning for now?
