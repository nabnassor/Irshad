# إرشاد — Irshad Website 🃏

Visual communication platform for autistic children (Arabic + English).
Static site + Firebase (Firestore, Auth, Storage, Hosting). No build step needed.

## Files
```
public/index.html   → the public website (families & children, no login)
public/admin.html   → admin panel at yoursite.com/admin
public/manifest.json, sw.js, icon.svg → PWA / offline support
firebase.json, firestore.rules, storage.rules → Firebase deployment config
```

---

## 🚀 Deploy in 6 steps (≈15 minutes)

### 1. Get your full Firebase config
Firebase Console → ⚙️ Project settings → Your apps → your Web app → **Config**.
Copy the whole `firebaseConfig` object.

### 2. Paste it TWICE
Open `public/index.html` and `public/admin.html`, find:
```js
const firebaseConfig = { apiKey: "PASTE_YOUR_API_KEY", ... }
```
and replace with your real config. (Your appId `1:685461208884:web:1fa90c664471e324722f61` is already filled in.)

### 3. Enable services (Firebase Console)
- **Authentication** → Sign-in method → enable **Email/Password**
- **Firestore Database** → Create database (production mode, region: me-central or europe-west)
- **Storage** → Get started

### 4. Create YOUR admin account (this is the "admin credentials" step)
Authentication → **Users** → **Add user**
→ Email: your email · Password: a strong password **you choose yourself**.
Only accounts you create here can log in to `/admin`. Nobody else can register.

### 5. Deploy
```bash
npm install -g firebase-tools
firebase login
firebase use YOUR_PROJECT_ID
firebase deploy
```
Your site goes live at `https://YOUR_PROJECT_ID.web.app`

### 6. First login
Open `https://YOUR_PROJECT_ID.web.app/admin`, sign in.
On first login the panel **auto-creates the 9 categories + starter cards** in Firestore.
From then on everything is editable from the panel.

---

## 🛠 Admin panel features
- 🃏 **Cards**: add / edit / delete / hide, upload photo + Arabic audio per card, reorder
- 📁 **Categories**: add / edit / delete, choose icon (emoji) + color
- ⚙️ **Settings**: phone, email, "download all cards" PDF link, about text (AR + EN)
- 📦 **Export** full JSON backup or cards CSV · **Import** a JSON backup
- 📊 **Stats**: total taps + most-used cards (use this for قياس الأثر in your project report)

## 🔒 Security
- Public: read-only. All writes require login (see `firestore.rules`).
- Exception: the public app may increment a card's `tapCount` only (for stats).
- Never share your admin password; it never appears in the code.

## 🖨 Connect the physical necklaces
Generate a QR code pointing to your live URL (e.g. `https://YOUR_PROJECT_ID.web.app/parents` view is at the للأهل section) and print it on the necklaces — families scan it and land on the guide.

## 💰 Cost
Firebase **Spark (free)** plan covers this project's scale entirely. 0 OMR.
