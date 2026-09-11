# FlutterFlow Guide - Beginner ke liye

## FlutterFlow kya hai?
FlutterFlow ek visual app builder hai. Drag-drop se app banta hai, code likhna nahi padta. Bina coding ke Android + iOS app ban sakta hai.

## FlutterFlow ke main concepts

### 1. Pages
- Ek page = ek screen (jaise Home page, Login page, Chat page)
- Page = ek file jisme UI elements hote hain
- Naya page: Left panel -> Pages -> + button

### 2. Widgets
- Widgets = UI ke building blocks
- Har cheez ek widget hai: Text, Button, Image, TextField, ListView, etc.
- Widget tree: Parent widget -> Child widgets (tree structure)
- Common widgets:

| Widget | Kaam |
|---|---|
| Text | Text dikhana |
| TextField | User input lena |
| IconButton | Button with icon |
| ElevatedButton | Raised button |
| Container | Box (color, padding, margin) |
| Row | Horizontal layout |
| Column | Vertical layout |
| ListView | Scrollable list |
| Stack | Elements overlap karna |
| Image | Photo dikhana |
| CircleImage | Circular photo |
| Card | Card-style container |
| Divider | Horizontal line |
| Icon | Icon dikhana |
| Padding | Space around widget |
| Expanded | Widget ko full width/height |

### 3. Actions
- Actions = button click pe kya ho
- Example: "Chat Now" button click -> Chat page open
- Action types:
  - Navigate to page
  - Backend action (database query, API call)
  - Show snackbar/alert
  - Custom code (advanced)

### 4. Backend Queries
- Firebase se data lana
- Types:
  - **Collection Query**: Multiple documents laao (jaise astrologers list)
  - **Document Query**: Ek specific document laao (jaise ek astrologer profile)
  - **Real-time Stream**: Live updates (jaise chat messages)

### 5. State Variables
- App mein data store karna
- Example: `selectedAstrologer`, `walletBalance`, `currentUser`
- Page state: sirf ek page ke liye
- App state: poore app mein access

### 6. AI Gen Feature
- FlutterFlow mein AI se UI generate kar sakte ho
- AI Gen Page: text likho, AI page bana dega
- Example: "astrologer list card with photo, name, rating, chat button"
- AI Gen Component: text likho, AI component bana dega
- Yeh beginner ke liye bohot useful hai

---

## FlutterFlow Interface Tour

### Left Panel (Pages & Navigation)
- Pages: saari screens yahan list hoti hain
- Navigation: bottom nav, drawer, etc.
- Components: reusable UI blocks

### Center (Canvas)
- Yahan app ka design dikh raha hai
- Drag-drop widgets yahan
- Click karke widget select karo
- Properties change karo

### Right Panel (Properties)
- Selected widget ki properties
- Style: color, font, size, padding
- Layout: width, height, alignment
- Action: click pe kya karna
- Backend: data bind karna

### Top Bar
- Device preview (phone/tablet)
- Theme toggle (light/dark)
- Run/Preview button
- Deploy button

---

## Step-by-Step: Pehla Page Banao

### Example: Home Page (Astrologer List)

1. **New page create karo**
   - Left panel -> Pages -> + -> "Home"
   - Blank page select karo

2. **AppBar add karo**
   - Top par Scaffold ka AppBar hai
   - Title: "AstroApp"
   - Actions: wallet icon, notification icon

3. **Search bar add karo**
   - AppBar ke neeche TextField widget drag karo
   - Hint text: "Search astrologer..."
   - Border: rounded

4. **ListView add karo**
   - TextField ke neeche ListView drag karo
   - Yeh astrologer cards list hoga

5. **Astrologer Card banao**
   - ListView ke andar Container drag karo
   - Container ke andar Row drag karo
   - Row mein:
     - Left: CircleImage (astrologer photo)
     - Middle: Column (name, expertise, rating)
     - Right: Column (chat rate, "Chat Now" button)

6. **Firebase se data bind karo**
   - ListView select karo
   - Properties -> Backend Query -> Collection Query
   - Collection: `astrologers`
   - Order by: rating descending
   - Save karo

7. **Card ko dynamic banao**
   - CircleImage -> Properties -> Image URL -> `astrologerRecord.photoUrl`
   - Text (name) -> `astrologerRecord.name`
   - Text (rating) -> `astrologerRecord.rating`
   - Text (rate) -> `astrologerRecord.chatRate`

8. **"Chat Now" button pe action do**
   - Button select karo
   - Actions -> Navigate -> Chat page
   - Pass parameter: `astrologerRecord` (selected astrologer)

9. **Preview karo**
   - Top right "Run" button click karo
   - App preview dikhega
   - Astrologers list aayega (agar Firebase mein data hai)

---

## AI Gen Page ka Use Kaise Karein

### Step 1: AI Gen Page open karo
- FlutterFlow mein "AI Gen" tab mein jao
- ya kisi page pe "Generate with AI" button click karo

### Step 2: Prompt likho
Example prompts:

**Login Page:**
```
Create a phone login page with India country code (+91), 
phone number input field, send OTP button, 6-digit OTP 
input boxes, verify button. Purple theme, dark background.
```

**Astrologer Card:**
```
Create an astrologer card with circular photo on left, 
name and expertise tags in middle, rating with stars, 
chat rate per minute, and a "Chat Now" button on right. 
Use purple accent color.
```

**Chat Screen:**
```
Create a chat screen with astrologer name and photo in 
app bar, timer and rate display, message list with user 
messages on right (blue bubbles) and astrologer messages 
on left (grey bubbles), message input field with send 
button at bottom.
```

**Wallet Screen:**
```
Create a wallet screen showing current balance prominently 
at top, quick add money buttons (100, 200, 500, 1000), 
custom amount input, and transaction history list below.
```

### Step 3: AI generate karega
- AI page/components generate kar dega
- Preview dekho
- Manually adjust karo (drag-drop se)

---

## FlutterFlow Tips for Beginners

1. **Pehle free plan se seekho** — paid plan jab confident ho tab lo
2. **AI Gen use karo** — bol ke UI banao, time bachega
3. **Templates dekho** — FlutterFlow marketplace mein free templates hain
4. **YouTube se seekho** — "FlutterFlow Hindi tutorial" search karo
5. **Ek component bana ke reuse karo** — astrologer card ek baar banao, har jagah use karo
6. **Firebase data pehle daalo** — UI bind karne ke liye data chahiye
7. **Chhote shuru karo** — pehle 2-3 screens banao, phir aage badho
8. **Preview regularly** — har change ke baad preview karo
9. **Naming convention follow karo** — page names, widget names clear rakho
10. **Community join karo** — FlutterFlow forum, Reddit, Discord