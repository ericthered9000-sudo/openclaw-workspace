---
name: app-name-research
description: Research app names for conflicts across app stores, trademarks, domains, and companies. Use when: (1) Validating a proposed app name, (2) Checking if a name is available for use, (3) Finding alternative names when conflicts exist, (4) Researching trademark availability for an app name. Use at the start of any new app project or when rebranding.
---

# App Name Research

This skill provides a systematic workflow for researching app name availability across app stores, trademarks, domains, and existing products.

## Workflow

### Step 1: Define the Name

Ask the user for:
- The proposed name
- The app category/type (health, productivity, finance, etc.)
- Target platforms (iOS, Android, Web)
- Geographic markets (US, EU, Global)

If the user hasn't decided on a name, ask for 3-5 keywords or themes to generate suggestions.

### Step 2: App Store Search

Search for the exact name and variations:

**Google Play Store:**
- Search: `"[name] app"` and `"[name]"`
- Note: app names, developer names, download counts

**Apple App Store:**
- Search: `"[name]"` and `"[name] app"`
- Note: app names, categories, developer names

**Web Search for Competitors:**
- `"[name] app"`
- `"[name] [category] app"`
- `"[name] [category]"`

Document:
- Exact matches (name taken)
- Similar matches (potential confusion)
- Category overlap (same category apps)
- Download/user counts if visible

### Step 3: Trademark Search

**USPTO Search:**
- Search USPTO TESS for the exact name
- Search for similar names
- Check classes: Class 9 (software), Class 42 (SaaS)

**Common Law Trademarks:**
- Search for companies using the name
- Search for products with the name
- Check if name is generic/descriptive

Document:
- Exact trademark matches
- Similar trademark matches
- Trademark class conflicts
- Whether name is generic (harder to trademark)

### Step 4: Domain Search

Check domain availability:
- `.com` - Primary recommendation
- `.app` - Mobile app specific
- `.io` - Tech/startup common
- `.co` - Common alternative

Use domain registrar searches or whois.

Document:
- Available domains
- Taken domains (who owns them)
- Premium domains (for sale at high price)

### Step 5: Company/Product Search

Search for:
- Companies with similar names
- Products with similar names
- Service marks
- Social media handles (@name on Twitter, Instagram, etc.)

Document conflicts and their industries.

### Step 6: Generate Alternatives

If conflicts found, generate alternatives using:

**Name Generation Strategies:**
1. **Compound words**: Combine two relevant words (WellnessGuard)
2. **Suffixes**: Add -ly, -ify, -io, -hub, -app
3. **Prefixes**: Add My-, -Go, Smart-
4. **Unique spellings**: Phonetic variations
5. **Metaphors**: Related concepts (Lighthouse for safety app)
6. **Acronyms**: First letters of descriptive phrase

For each alternative, run Steps 2-4 to verify availability.

### Step 7: Output Research Report

Create a structured report containing:

```markdown
# App Name Research: [NAME]

## Executive Summary
- Available/Not Available
- Primary conflicts
- Recommendation

## App Store Results
- Google Play: [findings]
- Apple App Store: [findings]
- Competitors: [list]

## Trademark Results
- USPTO: [findings]
- Common law: [findings]
- Risk level: [low/medium/high]

## Domain Results
- Available: [list]
- Taken: [list with owners]
- Recommended: [primary domain]

## Company/Product Conflicts
- [list any conflicts]

## Alternatives (if needed)
| Name | Status | Notes |
|------|--------|-------|
| ... | ... | ... |

## Recommendation
[Final recommendation with reasoning]
```

Save report to: `research/[APP-NAME]-research-[DATE].md`

## Reference Files

- **[trademark-classes.md](references/trademark-classes.md)**: USPTO class definitions for apps/software
- **[name-patterns.md](references/name-patterns.md)**: Common naming patterns and examples

## Tips

- **Generic names** (like "Wellness Check") are harder to trademark
- **Descriptive names** are harder to protect than arbitrary/fanciful names
- **Compound names** (WellGuard) are easier to trademark than single words
- Check the name in all target markets, not just one country
- Social media handles matter for marketing - check @name availability
- Consider SEO implications - unique names rank easier