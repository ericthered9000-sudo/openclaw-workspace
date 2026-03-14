# Subscription Optimization Tips

## Pricing Psychology

### Annual vs Monthly

| Metric | Monthly | Annual |
|--------|---------|--------|
| Retention (1 year) | 10-15% | 25-35% |
| Commitment | Low | High |
| Revenue timing | Spread out | Upfront |
| Average discount | None | 15-20% |

**Best practice:** Offer annual at "2 months free" pricing (equivalent to 17% discount).

### Price Anchoring

Show prices in order: Highest → Mid → Lowest

**Example:**
```
Premium: $19.99/mo
Pro: $9.99/mo  ← Most will pick this
Basic: $4.99/mo
```

Most users pick the middle option.

### Decoy Pricing

Add a "premium" tier to make the mid-tier look better.

**Example:**
```
Family: $14.99/mo (4 users)
Pro: $9.99/mo (1 user)     ← Target
Basic: $4.99/mo (limited)
```

The Family tier makes Pro look reasonable.

---

## Free Tier Design

### What to Give Away

**Give for free:**
- Basic functionality
- Limited usage (X actions/day)
- Core feature access
- Community features

**Reserve for paid:**
- Advanced features
- Unlimited usage
- Priority support
- Ad-free experience
- Advanced analytics/reports
- Family/team features

### Free Tier Limits

| Limit Type | Example | Effect |
|------------|---------|--------|
| Usage count | "5 check-ins per day" | Soft paywall |
| Feature gate | "Wellness score requires Pro" | Hard paywall |
| History limit | "7-day history" | Value paywall |
| Ad-free | "Remove ads for $2.99" | Convenience paywall |

### When to Show Upgrade Prompts

**Good moments:**
- After user hits a free limit
- After completing a valuable action
- After 3-5 sessions (not immediately)
- In settings (always available)

**Bad moments:**
- On first launch
- During onboarding
- In the middle of a task
- On error screens

---

## Conversion Optimization

### Free-to-Paid Conversion Benchmarks

| Category | Average | Good | Excellent |
|----------|---------|------|-----------|
| General | 2-4% | 4-6% | 8%+ |
| Health | 4-8% | 8-12% | 15%+ |
| Productivity | 3-7% | 7-10% | 12%+ |
| Finance | 2-5% | 5-8% | 10%+ |

### Ways to Improve Conversion

1. **Clear value proposition** — Show what they're missing
2. **Social proof** — "Join 10,000+ premium users"
3. **Trial period** — 7-day free trial increases conversion
4. **Annual discount** — 15-20% off annual plans
5. **Family/team plans** — Increase per-customer revenue
6. **Upgrade reminders** — Gentle nudges at limits

### Trial Best Practices

| Trial Length | Conversion Rate | Notes |
|--------------|-----------------|-------|
| 3-day | Lower | Too short to see value |
| 7-day | Good | Standard for most apps |
| 14-day | Better | More time to see value |
| 30-day | Variable | Can reduce urgency |

**Tip:** Collect payment method upfront for higher trial conversion.

---

## Churn Reduction

### Why Users Cancel

| Reason | % | Solution |
|--------|---|----------|
| Not using enough | 30% | Engagement reminders |
| Too expensive | 25% | Annual discount, cheaper tier |
| Missing features | 20% | Roadmap communication |
| Switching apps | 15% | Competitive analysis |
| Technical issues | 10% | Better support |

### Retention Tactics

1. **Onboarding** — Good onboarding = 2x retention
2. **Regular updates** — New features give reasons to stay
3. **Email engagement** — Weekly digest, tips
4. **Loyalty rewards** — Long-time subscriber benefits
5. **Win-back campaigns** — Special offers to lapsed users

### Churn Benchmarks

| Period | Good Churn | Acceptable | Needs Work |
|--------|------------|------------|------------|
| Monthly | <5% | 5-7% | >7% |
| Annual | <15% | 15-25% | >25% |

---

## Pricing Tiers

### Simple Tier Structure

| Tier | Price | Purpose | Target |
|------|-------|---------|--------|
| Free | $0 | Acquisition | Trial users |
| Basic | $5-10/mo | Core users | Most users |
| Premium | $10-20/mo | Power users | 10-20% |
| Family/Team | $15-30/mo | Groups | 5-10% |

### Feature Differentiation

| Feature | Free | Basic | Premium | Family |
|---------|------|-------|---------|--------|
| Core features | Limited | Full | Full | Full |
| Usage limits | Yes | No | No | No |
| Ads | Yes | No | No | No |
| Advanced features | No | Some | All | All |
| Support | Community | Email | Priority | Priority |
| Users | 1 | 1 | 1 | 4+ |

---

## Payment Processing

### RevenueCat (Recommended for Mobile)

**Pros:**
- Handles iOS + Android subscriptions
- Single API
- Analytics built-in
- Free tier available

**Cons:**
- Takes 1% of revenue (after $10k/mo)
- Requires setup

### Stripe (Recommended for Web)

**Pros:**
- Excellent documentation
- Webhooks for events
- Subscription management
- 2.9% + $0.30 per transaction

**Cons:**
- Doesn't handle mobile app stores

### Platform Fees

| Platform | Fee | Notes |
|----------|-----|-------|
| Apple App Store | 15-30% | 15% after year 1 for subs |
| Google Play | 15-30% | 15% after year 1 for subs |
| Stripe | 2.9% + $0.30 | Web payments |
| RevenueCat | 1% after $10k/mo | Subscription management |

---

## Revenue Recognition

### Monthly Subscriptions

- Revenue recognized monthly
- Predictable MRR (Monthly Recurring Revenue)
- Easy to forecast

### Annual Subscriptions

- Revenue recognized monthly (deferred)
- Large upfront payment
- Better cash flow
- Higher CLV (Customer Lifetime Value)

### Metrics to Track

| Metric | Formula | Target |
|--------|---------|--------|
| MRR | Monthly revenue from subs | Growing |
| ARR | MRR × 12 | Growing |
| ARPU | Revenue ÷ Users | $5-15 |
| CLV | ARPU × Avg months | $50-150 |
| LTV:CAC | CLV ÷ CAC | >3:1 |