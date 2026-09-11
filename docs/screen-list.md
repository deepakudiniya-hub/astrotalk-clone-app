# Screen List - AstroTalk Clone App

Total screens: 12. Har screen ka purpose aur key elements.

---

## User App Screens

### Screen 1: Splash Screen
- App logo
- App name
- Loading animation
- Auto redirect to Login or Home

### Screen 2: Login / Signup
- Phone number input (+91)
- OTP send button
- OTP verify input (6 digit)
- Firebase Phone Auth integration
- Terms & conditions link
- Skip option (guest mode - browse only)

### Screen 3: Home (Astrologer List)
- Top bar: app name, wallet balance, notification icon
- Search bar (astrologer name search)
- Filter chips: All / Online / Chat / Call
- Expertise filter: Vedic, Tarot, Numerology, etc.
- Astrologer cards (ListView):
  - Photo (circular)
  - Name
  - Expertise (tags)
  - Rating (star + number)
  - Experience
  - Chat rate (₹X/min)
  - Call rate (₹X/min)
  - "Chat Now" button
  - "Call" button
  - Online/Offline status dot
- Bottom navigation: Home | Horoscope | Bookings | Wallet | Profile

### Screen 4: Astrologer Profile
- Photo (large)
- Name + verified badge
- Expertise tags
- Rating + total reviews
- Experience
- Languages spoken
- About section (bio)
- Reviews list (scrollable)
- Chat rate + Call rate display
- "Start Chat" button (bottom sticky)
- "Call Now" button
- "Follow" button (optional)

### Screen 5: Chat Screen
- Top bar: astrologer name, photo, timer, rate/min
- Chat messages list (scrollable)
  - User messages (right side, blue)
  - Astrologer messages (left side, grey)
  - Timestamp on each message
- Message input field (bottom)
- Send button
- Wallet balance display (top corner)
- "End Chat" button
- Free first 5 minutes timer (optional)
- Auto-deduct from wallet per minute

### Screen 6: Wallet
- Current balance (large display)
- "Add Money" button
- Quick add buttons: ₹100, ₹200, ₹500, ₹1000
- Custom amount input
- Razorpay payment integration
- Transaction history list:
  - Type (credit/debit icon)
  - Amount
  - Description
  - Date & time
  - Status (success/failed)
- "Refund Policy" link

### Screen 7: My Bookings / History
- Tabs: Chats | Calls
- List of past consultations:
  - Astrologer photo + name
  - Date & time
  - Duration
  - Cost
  - Status (completed/cancelled)
  - "Rate & Review" button (if not rated)
  - "Chat Again" button

### Screen 8: Daily Horoscope
- Zodiac sign selector (12 signs grid)
- Today's horoscope:
  - General prediction
  - Love
  - Career
  - Health
  - Lucky number
  - Lucky color
- Yesterday / Tomorrow toggle
- "Consult Astrologer" CTA

### Screen 9: Profile / Settings
- User photo + name + phone
- Edit profile button
- Date of birth, birth place, birth time (for kundli)
- My reviews
- Wallet link
- Bookings link
- Notifications settings (toggle)
- Help & Support
- About app
- Logout button
- App version

### Screen 10: Add Money / Payment
- Amount display
- Quick amount buttons
- Payment method selection (Razorpay):
  - UPI (GPay, PhonePe, Paytm)
  - Card (debit/credit)
  - Net banking
- "Pay ₹X" button
- Payment success/failure screen
- Wallet auto-update on success

### Screen 11: Review / Rating
- Astrologer name + photo
- Star rating (1-5, interactive)
- Comment box (optional)
- "Submit Review" button
- Auto-update astrologer's average rating

### Screen 12: Notifications
- Notification list:
  - "Your chat with [astrologer] was completed"
  - "₹X deducted from wallet"
  - "New astrologer available: [name]"
  - "Daily horoscope is here!"
  - "Offer: 50% off on first consultation"
- Read/unread status
- Timestamp

---

## Bottom Navigation (5 tabs)

```
| Home | Horoscope | Bookings | Wallet | Profile |
```

---

## Screen Flow

```
Splash -> Login -> Home -> Astrologer Profile -> Chat
                                   |
                                   v
                              Wallet -> Add Money -> Payment
                                   |
                                   v
                              Bookings -> Review
```