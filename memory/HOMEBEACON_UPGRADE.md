# HomeBeacon Production Upgrade Plan

## Status: In Progress - Paused for Play Store Prep

## ⚠️ Before Play Store Submission
- [ ] Integrate real auth into App.tsx (replace demo logins)
- [ ] Update all API calls to use auth tokens
- [ ] Update socket connection for authenticated users
- [ ] Test full auth flow: register → login → use app → logout
- [ ] Configure CORS properly for production
- [ ] Update capacitor.config.ts (disable cleartext/allowMixedContent)

## Phase 1: Authentication & Security (Critical) ⚠️
- [x] Install auth dependencies (bcrypt, jsonwebtoken, zod)
- [x] Create auth types (`backend/src/types/auth.ts`)
- [x] Create auth middleware (`backend/src/middleware/auth.ts`)
- [x] Create auth routes (`backend/src/routes/auth.ts`)
- [x] Add auth imports to index.ts
- [x] Add password_hash column to users table
- [x] Mount auth routes properly
- [x] Backend compiles successfully!
- [ ] Configure CORS properly for production
- [ ] Add Helmet.js security headers (already using helmet)
- [ ] Add input validation with Zod (done in auth routes)

## Phase 2: State Management & Data Fetching
- [x] Install TanStack Query
- [x] Create API client with auth headers (`frontend/src/lib/auth.ts`)
- [x] Create Zustand store (`frontend/src/store/useAppStore.ts`)
- [x] Create auth hooks (`frontend/src/hooks/useAuth.ts`)
- [x] Create QueryProvider (`frontend/src/providers/QueryProvider.tsx`)
- [x] Create ErrorBoundary (`frontend/src/components/ErrorBoundary.tsx`)
- [x] Create Login component (`frontend/src/components/Login.tsx`)
- [ ] Add react-hot-toast to App.tsx
- [ ] Update App.tsx to use new auth system
- [ ] Implement optimistic updates for activities

## Phase 3: Code Organization
- [ ] Split App.tsx into views/ and components/
- [ ] Create proper folder structure
- [ ] Add proper loading states

## Phase 4: Performance
- [ ] Add React.lazy() code splitting
- [ ] Replace date handling with date-fns
- [ ] Optimize assets for PWA
- [ ] Add database indexes

## Phase 5: Mobile/Production
- [ ] Update capacitor.config.ts for production
- [ ] Disable cleartext/allowMixedContent
- [ ] Environment validation
- [ ] Build and test signed APK

## Key Files Modified
- `/home/james/wellness-check-code/backend/src/types/auth.ts` - NEW
- `/home/james/wellness-check-code/backend/src/middleware/auth.ts` - NEW
- `/home/james/wellness-check-code/backend/src/routes/auth.ts` - NEW
- `/home/james/wellness-check-code/backend/src/index.ts` - MODIFIED