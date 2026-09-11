# Database Schema - Firebase Firestore

## Collections Overview

Yeh Firebase Firestore ka database structure hai. Har collection ek JSON document ka set hai.

---

## 1. `users` Collection
Users ka data — jo consultation lete hain.

```
users/{userId}
{
  "uid": "string",
  "name": "string",
  "phone": "+91XXXXXXXXXX",
  "email": "string (optional)",
  "photoUrl": "string (optional)",
  "dob": "DD/MM/YYYY (optional)",
  "birthPlace": "string (optional)",
  "birthTime": "string (optional)",
  "walletBalance": 0,
  "createdAt": "timestamp",
  "isActive": true
}
```

---

## 2. `astrologers` Collection
Astrologers ka data — jo consultation dete hain.

```
astrologers/{astrologerId}
{
  "uid": "string",
  "name": "string",
  "photoUrl": "string",
  "phone": "+91XXXXXXXXXX",
  "expertise": ["Vedic Astrology", "Tarot", "Numerology"],
  "languages": ["Hindi", "English"],
  "experience": 5,
  "bio": "string",
  "chatRate": 20,          // per minute ₹
  "callRate": 30,           // per minute ₹
  "rating": 4.5,
  "totalReviews": 120,
  "totalConsultations": 500,
  "isOnline": true,
  "isAvailable": true,
  "walletBalance": 0,
  "createdAt": "timestamp"
}
```

---

## 3. `chats` Collection
Chat conversations between user and astrologer.

```
chats/{chatId}
{
  "chatId": "string",
  "userId": "string",
  "astrologerId": "string",
  "status": "active | completed | cancelled",
  "startedAt": "timestamp",
  "endedAt": "timestamp (optional)",
  "duration": 0,            // in seconds
  "totalCost": 0,            // ₹
  "perMinuteRate": 20
}
```

### Subcollection: `chats/{chatId}/messages`
```
chats/{chatId}/messages/{messageId}
{
  "messageId": "string",
  "senderId": "string",
  "senderType": "user | astrologer",
  "text": "string",
  "type": "text | image | system",
  "timestamp": "timestamp",
  "isRead": false
}
```

---

## 4. `walletTransactions` Collection
Wallet ke saare transactions — add money, deduction, refund.

```
walletTransactions/{transactionId}
{
  "transactionId": "string",
  "userId": "string",
  "type": "credit | debit",
  "amount": 100,
  "description": "Money added via Razorpay | Chat consultation deduction",
  "paymentMethod": "razorpay | chat | refund",
  "razorpayPaymentId": "string (optional)",
  "status": "success | failed | pending",
  "createdAt": "timestamp"
}
```

---

## 5. `reviews` Collection
Users ka astrologers ko dena wala review.

```
reviews/{reviewId}
{
  "reviewId": "string",
  "userId": "string",
  "astrologerId": "string",
  "chatId": "string (optional)",
  "rating": 4,
  "comment": "string",
  "createdAt": "timestamp"
}
```

---

## 6. `bookings` Collection
Call bookings — jab user call schedule karta hai.

```
bookings/{bookingId}
{
  "bookingId": "string",
  "userId": "string",
  "astrologerId": "string",
  "type": "chat | call",
  "status": "pending | confirmed | completed | cancelled",
  "scheduledAt": "timestamp",
  "duration": 0,
  "totalCost": 0,
  "createdAt": "timestamp"
}
```

---

## 7. `horoscopes` Collection
Daily horoscope content — admin upload karega.

```
horoscopes/{horoscopeId}
{
  "horoscopeId": "string",
  "zodiacSign": "Aries | Taurus | Gemini | ...",
  "date": "DD/MM/YYYY",
  "general": "string",
  "love": "string",
  "career": "string",
  "health": "string",
  "luckyNumber": 7,
  "luckyColor": "string",
  "createdAt": "timestamp"
}
```

---

## Firestore Security Rules (Basic)

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    
    // Users - sirf apna data dekh/pay
    match /users/{userId} {
      allow read, write: if request.auth.uid == userId;
    }
    
    // Astrologers - sab padh sakte hain, sirf astrologer khud update kare
    match /astrologers/{astrologerId} {
      allow read: if request.auth != null;
      allow write: if request.auth.uid == astrologerId;
    }
    
    // Chats - sirf involved user/astrologer dekh sakte hain
    match /chats/{chatId} {
      allow read, write: if request.auth != null;
      
      match /messages/{messageId} {
        allow read, write: if request.auth != null;
      }
    }
    
    // Reviews - sab padh sakte hain, sirf author likhe
    match /reviews/{reviewId} {
      allow read: if request.auth != null;
      allow create: if request.auth != null;
      allow delete, update: if false;
    }
    
    // Horoscopes - sab padh sakte hain
    match /horoscopes/{horoscopeId} {
      allow read: if request.auth != null;
      allow write: if false; // sirf admin console se
    }
  }
}
```

---

## Relationships Summary

```
User (1) -----> (N) Chats
User (1) -----> (N) WalletTransactions
User (1) -----> (N) Reviews
User (1) -----> (N) Bookings

Astrologer (1) -----> (N) Chats
Astrologer (1) -----> (N) Reviews
Astrologer (1) -----> (N) Bookings

Chat (1) -----> (N) Messages
```