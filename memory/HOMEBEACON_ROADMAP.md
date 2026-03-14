# HomeBeacon Roadmap

## v1.0 - Initial Launch (Current)
- ✅ Wellness score tracking
- ✅ One-tap check-in
- ✅ Emergency 911 button
- ✅ Medication reminders
- ✅ Doctor visit scheduling
- ✅ Weekly reports
- ✅ Family dashboard
- ✅ Landing page & privacy policy
- ⏳ Play Store submission (pending)

## v1.1 - Doctor Directory (Next)
**Requested by James's dad (2026-03-09)**

### Features
- Save list of doctors in one place
- Store: Name, specialty, phone, address, notes
- Link to Doctor Visits (select from saved doctors)
- Quick-dial phone numbers from app
- Family can view senior's doctor list

### Database Schema
```sql
CREATE TABLE doctors (
  id TEXT PRIMARY KEY,
  user_id TEXT NOT NULL,
  name TEXT NOT NULL,
  specialty TEXT,
  phone TEXT,
  address TEXT,
  notes TEXT,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES users(id)
);
```

### Tasks
- [ ] Add doctors table to database
- [ ] Create Doctors tab in app
- [ ] Add/Edit/Delete doctor UI
- [ ] Link doctors to visits
- [ ] Add quick-dial button
- [ ] Family view access

## v1.2 - Authentication
**Security upgrade**

### Features
- Real user accounts (email/password)
- JWT-based authentication
- Password hashing with bcrypt
- Secure API endpoints
- Token refresh

### Tasks
- [ ] Integrate auth into App.tsx
- [ ] Replace demo logins
- [ ] Update API calls with auth headers
- [ ] Add password reset flow
- [ ] Add email verification

## v1.3 - Premium Features
**Monetization**

### Features
- Subscription tiers (Ad-Free, Premium, Family)
- Google Play Billing integration
- Premium: unlimited check-ins, wellness insights
- Family: 3 caregiver accounts

### Tasks
- [ ] Integrate Play Billing
- [ ] Add subscription UI
- [ ] Implement feature gating
- [ ] Add ad banner for free tier
- [ ] Premium upgrade flow

## Backlog (Future)
- iOS version
- Push notification scheduling
- Medication refill reminders
- Appointment calendar sync
- Export data (PDF, CSV)
- Multiple seniors per family account
- Voice commands
- Widget for home screen