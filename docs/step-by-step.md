# Step-by-Step Development Plan

## Week 1: Setup & Learning

### Day 1-2: Accounts & Tools
- [ ] FlutterFlow account banao
- [ ] Firebase account banao (Google account se)
- [ ] Razorpay account banao
- [ ] GitHub account banao (already hai)
- [ ] Google Play Console account banao (₹2,000 one-time)

### Day 3-4: FlutterFlow Basics Seekho
- [ ] YouTube: "FlutterFlow beginner tutorial Hindi" dekho
- [ ] FlutterFlow docs: https://docs.flutterflow.io
- [ ] Ek simple app banao (counter app ya to-do list)
- [ ] Samjho: Pages, Widgets, Actions, Backend Queries
- [ ] Samjho: Navigation, ListView, Container, Text, Button

### Day 5-7: Firebase Basics
- [ ] Firebase Console explore karo
- [ ] Firestore database create karo
- [ ] Authentication enable karo (Phone)
- [ ] Collections manually add karo (users, astrologers)
- [ ] Dummy data add karo (5 astrologers)
- [ ] Security rules set karo (setup-guide.md se copy-paste)

---

## Week 2: UI Design (Screens Banao)

### Day 8-9: Basic Layout
- [ ] Project create karo FlutterFlow mein
- [ ] Theme set karo (purple/dark)
- [ ] Bottom navigation bar add karo (5 tabs)
- [ ] Pages create karo (12 screens — screen-list.md dekho)
- [ ] Navigation connect karo (tab -> page mapping)

### Day 10-11: Home Screen (Astrologer List)
- [ ] AppBar: app name, wallet balance, notification icon
- [ ] Search bar widget
- [ ] Filter chips (All / Online / Chat / Call)
- [ ] ListView widget add karo
- [ ] Astrologer card design karo:
  - Photo (CircularImage)
  - Name (Text)
  - Expertise (tags - wrapping row)
  - Rating (Row of stars + number)
  - Chat rate (Text)
  - "Chat Now" button
  - "Call" button
  - Online status dot
- [ ] Firebase se astrologers data bind karo (Backend Query)
- [ ] AI Gen try karo: "astrologer card with photo, name, rating, chat button"

### Day 12: Astrologer Profile Screen
- [ ] Large photo
- [ ] Name + verified badge
- [ ] Expertise tags
- [ ] Rating + total reviews
- [ ] Experience, languages
- [ ] Bio/About section
- [ ] Reviews list (ListView)
- [ ] "Start Chat" button (sticky bottom)
- [ ] "Call Now" button
- [ ] Firebase se single astrologer data bind karo (Document query)

### Day 13: Login Screen
- [ ] Phone number input (TextField)
- [ ] "Send OTP" button
- [ ] OTP input (6 digit boxes)
- [ ] "Verify" button
- [ ] Firebase Phone Auth action set karo
- [ ] Login success -> Home page redirect
- [ ] Guest mode option (skip login, browse only)

### Day 14: Wallet Screen
- [ ] Balance display (large text)
- [ ] "Add Money" button
- [ ] Quick add buttons (₹100, ₹200, ₹500, ₹1000)
- [ ] Custom amount input
- [ ] Transaction history (ListView)
- [ ] Firebase se transactions data bind karo

---

## Week 3-4: Backend & Database Integration

### Day 15-16: Data Binding
- [ ] Home screen: astrologers collection se data laao
- [ ] Profile screen: specific astrologer document laao
- [ ] Wallet screen: walletTransactions collection laao
- [ ] Bookings screen: bookings collection laao
- [ ] Horoscope screen: horoscopes collection laao

### Day 17-18: User Authentication Flow
- [ ] Phone OTP login implement karo
- [ ] Login success par user document create karo (Firestore)
- [ ] User session manage karo
- [ ] Logout functionality
- [ ] Auto-login (agar already logged in)
- [ ] Guest mode restrictions (chat/payment block)

### Day 19-20: Wallet & Payments (Razorpay)
- [ ] Razorpay account setup
- [ ] API keys integrate karo FlutterFlow mein
- [ ] "Add Money" flow:
  1. User amount enter kare
  2. Razorpay checkout khule
  3. Payment success -> wallet update
  4. Transaction record add karo
- [ ] Wallet deduction logic (chat shuru hone pe)
- [ ] Insufficient balance warning
- [ ] Test payments (Razorpay test mode)

### Day 21-22: Reviews System
- [ ] "Rate & Review" screen design
- [ ] Star rating widget (interactive)
- [ ] Comment box
- [ ] Submit review -> Firestore mein save
- [ ] Astrologer rating auto-update (average calculation)
- [ ] Reviews astrologer profile pe display

### Day 23-24: Horoscope Feature
- [ ] Zodiac sign grid (12 signs)
- [ ] Horoscope data Firestore se laao
- [ ] General / Love / Career / Health tabs
- [ ] Lucky number + color display
- [ ] "Consult Astrologer" CTA button
- [ ] Daily auto-update (admin console se data daalna)

### Day 25-26: Bookings & History
- [ ] Past consultations list (chats + calls)
- [ ] Filter tabs: Chats / Calls
- [ ] Status display (completed/cancelled)
- [ ] "Rate & Review" button (if not rated)
- [ ] "Chat Again" button -> astrologer profile

### Day 27-28: Profile & Settings
- [ ] User info display (photo, name, phone)
- [ ] Edit profile functionality
- [ ] DOB, birth place, birth time fields
- [ ] Notifications toggle
- [ ] Help & Support section
- [ ] Logout button
- [ ] App version display

---

## Week 5-6: Chat System (Core Feature)

### Day 29-31: Real-time Chat Setup
- [ ] Chat page design complete karo
- [ ] Firestore subcollection: `chats/{chatId}/messages`
- [ ] Real-time stream setup (Firestore snapshots)
- [ ] Message send functionality:
  1. User type kare message
  2. Send button click
  3. Message Firestore mein save
  4. Astrologer ko notification
  5. Astrologer reply
- [ ] Message bubble UI (user right, astrologer left)
- [ ] Timestamp display
- [ ] Scroll to bottom on new message

### Day 32-33: Chat Wallet Logic
- [ ] Chat start hone pe wallet check karo (minimum balance)
- [ ] Per-minute rate deduction
- [ ] Timer display (kitna time baaki)
- [ ] Auto-end jab balance khatam
- [ ] "End Chat" button (manual end)
- [ ] Chat completion summary (duration, cost)
- [ ] Wallet deduction record save karo

### Day 34-36: Notifications (FCM)
- [ ] Firebase Cloud Messaging setup
- [ ] Notification types:
  - New chat message
  - Chat started/ended
  - Wallet deduction
  - Wallet recharge success
  - New astrologer available
  - Daily horoscope reminder
- [ ] Notification permission request
- [ ] Notification tap -> relevant screen

### Day 37-42: Polish & Extra Features
- [ ] Search functionality (astrologer name/expertise)
- [ ] Filter logic (online, chat available, call available)
- [ ] Sort options (rating, price, experience)
- [ ] Empty states (no astrologers, no chats, etc.)
- [ ] Error handling (network error, payment failed)
- [ ] Loading indicators
- [ ] Pull-to-refresh
- [ ] Image caching (astrologer photos)
- [ ] Dark mode toggle (optional)

---

## Week 7: Testing

### Day 43-44: Internal Testing
- [ ] APK download FlutterFlow se
- [ ] Phone pe install karo
- [ ] Test cases run karo:
  - Login with phone OTP
  - Browse astrologers
  - View astrologer profile
  - Start chat
  - Send/receive messages
  - Wallet add money
  - Wallet deduction
  - Rate & review
  - View bookings history
  - Daily horoscope
  - Logout/login

### Day 45-46: Beta Testing
- [ ] 5-10 friends/family ko app do
- [ ] Feedback collect karo
- [ ] Bugs note karo
- [ ] Common issues fix karo

### Day 47-49: Bug Fixes
- [ ] Critical bugs fix karo
- [ ] UI improvements
- [ ] Performance optimization
- [ ] Edge cases handle karo (low balance, network failure)
- [ ] Final APK generate karo

---

## Week 8: Play Store Launch

### Day 50-51: Play Store Preparation
- [ ] App icon design karo (512x512px)
- [ ] App screenshots (phone) — kam se kam 2-3 screenshots
- [ ] Feature graphic (1024x500px)
- [ ] App description likho (Hindi + English)
- [ ] Privacy policy page banao (Google Sites free)
- [ ] App category: Lifestyle
- [ ] Content rating questionnaire fill karo

### Day 52-53: Play Store Submit
- [ ] Google Play Console mein app create karo
- [ ] APK/AAB upload karo (FlutterFlow se AAB download)
- [ ] Store listing details bharo
- [ ] Screenshots upload karo
- [ ] Privacy policy URL add karo
- [ ] Submit for review

### Day 54-56: Review & Launch
- [ ] Google ka review wait karo (1-3 days)
- [ ] Agar reject ho jaye toh fix karo
- [ ] Approved hone par publish karo
- [ ] App link share karo

---

## Post-Launch (Ongoing)

- [ ] User feedback collect karo
- [ ] Regular bug fixes
- [ ] Naye astrologers add karo (Firebase console se)
- [ ] Daily horoscope update karo
- [ ] Analytics dekho (Firebase + Play Console)
- [ ] Phase 2 plan: Call feature, Kundli, Video call