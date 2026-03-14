# Memory Index - Wellness Check / HomeBeacon

## March 2026 Session Summaries

### 2026-03-10: Tailwind Migration Disaster & Recovery
**Status**: ⚠️ Critical learning session

**What Happened**:
- Morning: Attempted Tailwind CSS migration (70% CSS reduction achieved)
- Result: Visual appearance BROKEN - lost centering, styling issues
- User rejected migration, reverted to original
- Discovery: Git repo missing 30+ accessibility fixes from March 8
- Working code exists in APK but NOT in git

**Key Lessons**:
1. Working APK is source of truth, not git
2. Never reconstruct from memory - extract from working build
3. One fix at a time, commit after each
4. User approves BEFORE deploying

**Fixes Applied**:
- #1: Duplicate URLs (`/en` serving old landing page) - RESOLVED
- #2: Centering on all pages - RESOLVED
- #3: Theme button moved to bottom - RESOLVED

**Files**:
- Working APK: `/home/james/HomeBeacon-release.apk` (March 9)
- Memory: `memory/2026-03-10.md` (full session log)

### 2026-03-09: Vercel Deployment Fixes
**Status**: ✅ Successful

**Issues Fixed**:
1. Vercel routing (`routes` → `rewrites`)
2. API_URL environment variable trailing newline
3. Deployment directory confusion (nested .vercel folders)

**Result**: Production site working at https://frontend-six-blond-57.vercel.app

### 2026-03-08: Accessibility Fixes (30+)
**Status**: ⚠️ NOT COMMITTED TO GIT

**Fixes Made** (per memory file):
- CSS syntax error (orphaned closing brace)
- Z-index hierarchy
- Touch targets (44px minimum)
- Font sizes (16px base)
- Color contrast
- Centering styles
- High contrast mode
- Large text mode
- And 20+ more...

**Critical**: These fixes are in the APK but were never committed to git. This is the source of all current issues.

---

## Project State
- **Production**: https://frontend-six-blond-57.vercel.app
- **Source**: `/home/james/wellness-check-code/frontend/`
- **Working APK**: March 9 release (1.4MB)
- **Git**: Broken (missing accessibility fixes)

## Workflow Going Forward
1. Fix ONE thing
2. Show result BEFORE deploying
3. User approves
4. Deploy
5. COMMIT immediately
6. Repeat