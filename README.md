# AstroTalk Clone - Android App

Ek astrology consultation app jahan users astrologers se chat/call karke consultation lete hain. FlutterFlow + Firebase se banayenge — bina coding ke.

---

## Tech Stack

| Component | Tool | Cost |
|---|---|---|
| App Builder | FlutterFlow | ₹3,000/month |
| Backend | Firebase (Firestore, Auth, Storage, FCM) | Free |
| Payments | Razorpay | Free setup |
| Real-time Chat | Firebase Firestore Streams | Free |
| Push Notifications | Firebase Cloud Messaging | Free |
| Code Storage | GitHub | Free |
| Play Store | Google Play Console | ₹2,000 one-time |

---

## Budget: ₹10,000

| Item | Cost |
|---|---|
| FlutterFlow Standard (2 months) | ₹6,000 |
| Google Play Console (lifetime) | ₹2,000 |
| Domain (optional) | ₹800 |
| App Icon (optional, Fiverr) | ₹1,000 |
| Buffer | ₹200 |
| **Total** | **₹10,000** |

Detailed breakdown: [docs/budget.md](docs/budget.md)

---

## Timeline: 6-8 Weeks

| Week | Task |
|---|---|
| Week 1 | Setup + Learning (FlutterFlow + Firebase) |
| Week 2 | UI Design (12 screens) |
| Week 3-4 | Backend + Database Integration |
| Week 5-6 | Chat System + Notifications |
| Week 7 | Testing |
| Week 8 | Play Store Launch |

Detailed plan: [docs/step-by-step.md](docs/step-by-step.md)

---

## App Screens (12 total)

1. Splash Screen
2. Login / Signup (Phone OTP)
3. Home (Astrologer List)
4. Astrologer Profile
5. Chat Screen
6. Wallet
7. My Bookings / History
8. Daily Horoscope
9. Profile / Settings
10. Add Money / Payment
11. Review / Rating
12. Notifications

Detailed screens: [docs/screen-list.md](docs/screen-list.md)

---

## Database: Firebase Firestore

7 collections:
- `users` — user data
- `astrologers` — astrologer data
- `chats` + `messages` subcollection — chat conversations
- `walletTransactions` — wallet history
- `reviews` — user reviews
- `bookings` — call/chat bookings
- `horoscopes` — daily horoscope content

Detailed schema: [docs/database-schema.md](docs/database-schema.md)

---

## Setup Guides

- [FlutterFlow + Firebase Setup](docs/setup-guide.md)
- [FlutterFlow Beginner Guide](docs/flutterflow-guide.md)
- [Step-by-Step Development Plan](docs/step-by-step.md)

---

## Core Features

- **Phone OTP Login** — Firebase Phone Authentication
- **Astrologer List** — browse, search, filter by expertise
- **Astrologer Profile** — details, reviews, rates
- **Real-time Chat** — Firebase Firestore streams
- **Wallet System** — add money via Razorpay, per-minute deduction
- **Daily Horoscope** — 12 zodiac signs
- **Ratings & Reviews** — 5-star rating + comments
- **Booking History** — past consultations
- **Push Notifications** — FCM
- **Play Store Deploy** — proper Android APK/AAB

---

## Phase 2 Features (Future)

- Audio/Video Call (Agora)
- Kundli Generation
- Free 5-minute chat for new users
- Refer & Earn
- Multi-language support
- Admin Panel (Web)
- Astrologer App (separate)

---

## Contact

Developer: Deepak Udiniya
Email: deepakudiniya@gmail.com

---

> Note: Yeh documentation ek guide hai. FlutterFlow mein actually app banana ke liye step-by-step.md follow karo. Koi doubt ho toh refer to docs.