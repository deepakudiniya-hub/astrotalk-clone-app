# Setup Guide - FlutterFlow + Firebase

## Part A: FlutterFlow Setup

### Step 1: Account Banao
1. https://flutterflow.io par jao
2. "Get Started" click karo
3. Email se account banao ya Google se sign-in karo
4. Free plan se start karo (pehle explore karo)
5. Project create karo: "AstroApp" naam do

### Step 2: Project Settings
1. New project -> Blank app
2. Project name: AstroApp
3. Platform: Android (initially)
4. Theme: Purple/Dark (astrology ke liye perfect)
5. Primary color: #6A1B9A (purple)
6. Background: #0D0D0D (dark) ya #F5F5F5 (light)

### Step 3: Navigation Setup
1. Bottom Navigation bar add karo (5 tabs)
2. Tabs: Home, Horoscope, Bookings, Wallet, Profile
3. Har tab ke liye page assign karo

---

## Part B: Firebase Setup

### Step 1: Firebase Project Create Karo
1. https://console.firebase.google.com par jao
2. "Add Project" click karo
3. Project name: "astroapp-prod" (ya jo marzi)
4. Google Analytics: Enable karo (free)
5. Project create hone ka wait karo

### Step 2: Android App Add Karo
1. Firebase Console mein "Add App" -> Android
2. Package name: `com.yourname.astroapp` (FlutterFlow mein bhi same rakhna)
3. App nickname: AstroApp
4. `google-services.json` download karo
5. Ye file FlutterFlow mein upload karni hai

### Step 3: FlutterFlow mein Firebase Connect Karo
1. FlutterFlow -> Project Settings -> Firebase
2. "Connect Firebase" click karo
3. Firebase project select karo
4. `google-services.json` upload karo
5. Save karo

### Step 4: Firebase Services Enable Karo
Firebase Console mein jao aur yeh enable karo:

**Authentication:**
1. Build -> Authentication -> Get Started
2. Sign-in method: "Phone" enable karo
3. Save karo

**Firestore Database:**
1. Build -> Firestore Database -> Create Database
2. Production mode mein start karo (security rules baad mein)
3. Location: `asia-south1` (Mumbai) select karo
4. Enable karo

**Storage:**
1. Build -> Storage -> Get Started
2. Location: `asia-south1`
3. Enable karo

**Cloud Messaging (FCM):**
1. Build -> Cloud Messaging
2. Already enabled hota hai naye projects mein
3. Server key note karo (FlutterFlow mein daalna hai)

### Step 5: Razorpay Setup
1. https://razorpay.com par account banao
2. Dashboard -> API Keys -> Generate Key
3. Key ID aur Key Secret note karo
4. Test mode mein start karo (fake payments test ke liye)
5. FlutterFlow -> Custom Code ya Action -> Razorpay integration

---

## Part C: Firebase Collections Setup

### Firestore mein collections create karo:

1. Firebase Console -> Firestore -> "Start Collection"
2. Yeh collections banao (collection ID):

```
users
astrologers
chats
walletTransactions
reviews
bookings
horoscopes
```

3. Har collection mein ek dummy document add karo (test ke liye)
4. Fields wahi rakhna jo [database-schema.md] mein diye hain

### Dummy Astrologer Data Add Karo

```
Collection: astrologers
Document ID: auto
Fields:
  name: "Pandit Sharma"
  expertise: ["Vedic Astrology", "Tarot"]
  languages: ["Hindi", "English"]
  experience: 5
  chatRate: 20
  callRate: 30
  rating: 4.5
  totalReviews: 120
  isOnline: true
  isAvailable: true
```

Aise 5-10 dummy astrologers add kar lo testing ke liye.

---

## Part D: Security Rules Setup

Firebase Console -> Firestore -> Rules mein yeh paste karo:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth.uid == userId;
    }
    match /astrologers/{astrologerId} {
      allow read: if request.auth != null;
      allow write: if request.auth.uid == astrologerId;
    }
    match /chats/{chatId} {
      allow read, write: if request.auth != null;
      match /messages/{messageId} {
        allow read, write: if request.auth != null;
      }
    }
    match /reviews/{reviewId} {
      allow read: if request.auth != null;
      allow create: if request.auth != null;
      allow delete, update: if false;
    }
    match /horoscopes/{horoscopeId} {
      allow read: if request.auth != null;
      allow write: if false;
    }
    match /walletTransactions/{transactionId} {
      allow read, write: if request.auth != null;
    }
    match /bookings/{bookingId} {
      allow read, write: if request.auth != null;
    }
  }
}
```

Publish karo. Done!

---

## Troubleshooting

**Firebase connection nahi ho raha?**
- Package name same hai FlutterFlow aur Firebase mein?
- google-services.json sahi upload kiya?
- FlutterFlow project settings mein Firebase project ID sahi hai?

**Phone OTP nahi aa raha?**
- Firebase Console -> Authentication -> Phone -> test numbers add karo
- Real phone number pe testing ke liye paid plan chahiye (free mein test numbers use karo)

**Firestore permission denied?**
- Security rules check karo
- Debug mode try karo: `allow read, write: if true;` (temporary, for testing only)