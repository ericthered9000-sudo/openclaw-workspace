---
name: app-monetization
description: Research monetization strategies for apps including ad networks, subscription pricing, in-app purchases, and revenue projections. Use when: (1) Planning monetization for a new app, (2) Researching ad network options, (3) Setting subscription pricing, (4) Estimating revenue potential, (5) Deciding between monetization models. Use after validating app concept and before or during pricing decisions.
---

# App Monetization

This skill provides a systematic workflow for researching and planning app monetization strategies.

## Workflow

### Step 1: Understand the App

Ask the user for:
- App category (health, productivity, finance, etc.)
- Target audience (seniors, professionals, parents, etc.)
- Core features
- Platform(s) (iOS, Android, Web)
- Development stage (planning, launched, scaling)

### Step 2: Choose Monetization Model(s)

Evaluate options based on app type:

| Model | Best For | Revenue Potential |
|-------|----------|-------------------|
| **Freemium** | Most apps | 3-5% conversion to paid |
| **Ads** | High-traffic apps | $1-5 CPM for content apps |
| **Subscription** | Utility, SaaS | Predictable recurring revenue |
| **One-time purchase** | Tools, games | Limited recurring revenue |
| **In-app purchases** | Games, social | High per-user potential |
| **Marketplace fees** | Platforms | Percentage of transactions |

**Common combinations:**
- Freemium + Ads (free tier shows ads)
- Freemium + Subscription (upgrade removes ads, adds features)
- Free + IAP (games, virtual goods)

### Step 3: Research Ad Networks

If considering ads, research:

**Major Networks:**

| Network | CPM Range | Best For | Notes |
|---------|-----------|----------|-------|
| Google AdMob | $0.50-3.00 | Most apps | Easy integration, reliable |
| Meta Audience Network | $1.00-5.00 | Social apps | Higher CPMs, requires Facebook account |
| Unity Ads | $3.00-10.00 | Games | Rewarded video, higher engagement |
| AppLovin | $2.00-8.00 | Games, entertainment | Strong for gaming |
| IronSource | $2.00-6.00 | Games | Good for rewarded ads |

**Ad Types:**

| Type | CPM | Intrusiveness | Best For |
|------|-----|----------------|----------|
| Banner | $0.50-2.00 | Low | Always-visible content |
| Interstitial | $2.00-8.00 | Medium | Between screens |
| Rewarded Video | $5.00-15.00 | Low (opt-in) | Games, in-app currency |
| Native | $1.00-4.00 | Very Low | Feed-based content |

### Step 4: Research Competitor Pricing

Search for:
- Competitor app pricing
- Free tier limitations
- Premium features
- Annual vs monthly discounts
- Family/team plans

Document:
- Pricing range in category
- Most common price point
- Premium features competitors charge for
- Pricing gaps (overpriced or underpriced segments)

### Step 5: Calculate Revenue Projections

Create projections based on:

**Ad Revenue:**
```
Monthly Ad Revenue = Users × Ads/User/Day × 30 × CPM ÷ 1000
```

**Example:** 5,000 users × 5 ads/day × 30 days × $1.50 CPM ÷ 1000 = $1,125/month

**Subscription Revenue:**
```
Monthly Subscription Revenue = Users × Conversion% × Price
```

**Example:** 5,000 users × 5% conversion × $6.99 = $1,748/month

### Step 6: Define Pricing Tiers

Create a tiered pricing structure:

| Tier | Price | Features | Target User |
|------|-------|----------|-------------|
| Free | $0 | [limited features] | Trial, low-income |
| Basic/Ad-Free | $X/mo | [ad removal] | Price-sensitive |
| Premium | $Y/mo | [full features] | Most users |
| Family/Team | $Z/mo | [multi-user] | Families, teams |

**Pricing psychology:**
- Annual plans retain 2-3x better than monthly
- Show annual as "X months free" equivalent
- Most users choose middle tier
- Premium tier makes mid-tier look better

### Step 7: Output Monetization Plan

Create a structured report:

```markdown
# Monetization Plan: [APP NAME]

## Executive Summary
- Recommended model: [Freemium + Ads, Subscription, etc.]
- Projected Year 1 revenue: $X
- Key monetization features

## Monetization Model

### Primary Model: [Model]
- Why this model fits
- Revenue potential

### Secondary Model: [If applicable]

## Pricing Structure

| Tier | Price | Features |
|------|-------|----------|
| ... | ... | ... |

## Ad Strategy (if applicable)

- Network: [Recommended]
- Ad type: [Banner, Interstitial, etc.]
- Placement: [Where in app]
- Estimated CPM: $X
- Projected ad revenue: $X/month at Y users

## Revenue Projections

| Period | Users | Conversion | Monthly Revenue | Annual Revenue |
|--------|-------|------------|-----------------|----------------|
| Year 1 | X | Y% | $A | $B |
| Year 2 | X | Y% | $A | $B |
| Year 3 | X | Y% | $A | $B |

## Implementation Checklist

- [ ] Set up payment processor (RevenueCat, Stripe, etc.)
- [ ] Configure subscription tiers
- [ ] Implement ad SDK (if applicable)
- [ ] Add paywall screens
- [ ] Create upgrade flows
- [ ] Set up analytics for conversion tracking

## Sources
- [Competitor pricing sources]
- [Ad network documentation]
- [Market data sources]
```

Save report to: `research/[APP-NAME]-monetization-[DATE].md`

## Reference Files

- **[ad-networks.md](references/ad-networks.md)**: Detailed ad network comparison
- **[subscription-tips.md](references/subscription-tips.md)**: Subscription optimization best practices

## Tips

- **Start simple** — One upgrade path converts better than multiple
- **Test pricing** — A/B test price points if possible
- **Watch conversion** — 3-5% is typical, below 2% signals pricing issue
- **Annual discounts** — 15-20% off drives annual subscriptions
- **Free tier value** — Free users still provide word-of-mouth and ad revenue
- **Upgrade prompts** — Show upgrade at high-value moments, not immediately