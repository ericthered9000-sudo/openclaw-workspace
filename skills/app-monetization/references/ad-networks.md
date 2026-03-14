# Ad Network Comparison

## Major Ad Networks

### Google AdMob

**Best for:** Most apps, beginners, reliable revenue

| Metric | Value |
|--------|-------|
| CPM Range | $0.50 - $3.00 |
| Fill Rate | 95-99% |
| Minimum Payout | $100 |
| Payment Terms | Net-30 |
| Integration | Easy (SDK, plugins) |

**Ad Types:**
- Banner ads
- Interstitial ads
- Rewarded ads
- Native ads

**Pros:**
- Most widely used
- Excellent documentation
- Good fill rates
- Reliable payments
- Works well with Google Play

**Cons:**
- Lower CPMs than competitors
- Limited targeting compared to Meta
- Strict policy enforcement

---

### Meta Audience Network (Facebook)

**Best for:** Social apps, apps with Facebook login, higher CPMs

| Metric | Value |
|--------|-------|
| CPM Range | $1.00 - $5.00 |
| Fill Rate | 90-98% |
| Minimum Payout | $100 |
| Payment Terms | Net-30 |

**Ad Types:**
- Banner ads
- Interstitial ads
- Native ads
- Rewarded video

**Pros:**
- Higher CPMs
- Excellent targeting
- Works with Facebook user data

**Cons:**
- Requires Facebook developer account
- Stricter review process
- Privacy compliance more complex

---

### Unity Ads

**Best for:** Games, rewarded video ads

| Metric | Value |
|--------|-------|
| CPM Range | $3.00 - $15.00 |
| Fill Rate | 90-95% |
| Minimum Payout | $100 |
| Payment Terms | Net-60 |

**Ad Types:**
- Rewarded video (primary)
- Interstitial ads

**Pros:**
- Highest CPMs for rewarded video
- Strong for gaming apps
- Good user experience (opt-in)

**Cons:**
- Primarily for games
- Lower fill rates in some regions
- Longer payment terms

---

### AppLovin

**Best for:** Games, entertainment apps, maximizing eCPM

| Metric | Value |
|--------|-------|
| CPM Range | $2.00 - $10.00 |
| Fill Rate | 90-97% |
| Minimum Payout | $100 |
| Payment Terms | Net-30 |

**Ad Types:**
- Rewarded video
- Interstitial ads
- Banner ads

**Pros:**
- Strong mediation platform
- Good for gaming
- Advanced analytics

**Cons:**
- Can be complex to configure
- More suited for games

---

### IronSource (by Unity)

**Best for:** Games, mediation platforms

| Metric | Value |
|--------|-------|
| CPM Range | $2.00 - $8.00 |
| Fill Rate | 90-95% |
| Minimum Payout | $100 |

**Ad Types:**
- Rewarded video
- Interstitial ads
- Offerwall

**Pros:**
- Strong mediation (multiple networks)
- Good for scaling
- Advanced targeting

**Cons:**
- Requires more setup
- Primarily for games

---

## CPM Benchmarks by Category

| Category | Average CPM | Top Quartile |
|----------|-------------|--------------|
| Gaming | $1.50 - $5.00 | $8.00+ |
| Health & Fitness | $1.00 - $3.00 | $5.00+ |
| Productivity | $0.50 - $2.00 | $3.00+ |
| Finance | $2.00 - $8.00 | $12.00+ |
| News/Media | $1.00 - $4.00 | $6.00+ |
| Social | $1.50 - $4.00 | $6.00+ |

---

## Ad Type Best Practices

### Banner Ads

**When to use:** Content apps, always-visible screens

**Placement:**
- Top of screen (less intrusive)
- Bottom of screen (common)
- Within content feed (native)

**Do:**
- Keep sizes standard (320x50, 728x90)
- Allow dismissal after reasonable time
- Hide on critical screens (payment, emergency)

**Don't:**
- Place near buttons (accidental clicks)
- Show on small screens that break layout
- Use on screens with limited content

### Interstitial Ads

**When to use:** Between screens, after completing actions

**Placement:**
- Between app sections
- After completing a task
- At natural breaks in content

**Do:**
- Show at natural transitions
- Allow closing after 5 seconds
- Limit frequency (1 per 3-5 minutes)

**Don't:**
- Show during critical actions
- Show immediately on app launch
- Use on screens where user expects immediate action

### Rewarded Video

**When to use:** Games, apps with virtual currency/points

**Placement:**
- Offer in exchange for points/currency
- Unlock premium features temporarily
- Remove ads temporarily

**Do:**
- Make reward clear
- Allow user to choose when to watch
- Provide real value

**Don't:**
- Force users to watch
- Offer trivial rewards
- Replace core features with ads

---

## Ad Placement Guidelines by App Type

### Health/Medical Apps

| Screen | Ad Type | Allowed |
|--------|---------|---------|
| Dashboard | Banner | ✅ |
| Emergency | None | ❌ Never |
| Medication reminder | None | ❌ |
| Settings | Banner | ✅ |
| Reports | Banner | ✅ |
| Payment | None | ❌ |

### Senior-Focused Apps

**Additional considerations:**
- Avoid video ads (confusing to close)
- Larger text on ad banners
- No ads on emergency screens
- Clear "Remove Ads" option

---

## Revenue Calculation

### Basic Formula

```
Revenue = Users × Sessions/Day × Ads/Session × CPM ÷ 1000
```

### Example: Health App

| Metric | Value |
|--------|-------|
| Users | 10,000 |
| Sessions per day | 2 |
| Ads per session | 3 |
| Daily impressions | 60,000 |
| Monthly impressions | 1,800,000 |
| CPM | $1.50 |
| **Monthly Revenue** | **$2,700** |

### With Fill Rate

If fill rate is 95%:
```
Effective Revenue = $2,700 × 0.95 = $2,565
```