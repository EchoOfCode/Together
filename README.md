# Together — Shared Real-Time Calendar 🗓️

A modern, fast, zero-backend shared calendar. Anyone can open the same link, view the same schedule live, and collaborate simultaneously in real time.

Built with an editorial warm paper & ink aesthetic, 4 interactive views (Month, Week, Day, Agenda), full event CRUD, offline local storage fallback, and instant Firebase synchronization.

---

## ⚡ 1-Click Deploy to Vercel

Deploy your own shared calendar to Vercel for free:

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2FEchoOfCode%2FTogether&env=VITE_FIREBASE_API_KEY,VITE_FIREBASE_AUTH_DOMAIN,VITE_FIREBASE_PROJECT_ID,VITE_FIREBASE_STORAGE_BUCKET,VITE_FIREBASE_MESSAGING_SENDER_ID,VITE_FIREBASE_APP_ID&envDescription=Get%20these%20values%20from%20your%20free%20Firebase%20Console%20(Project%20Settings%20-%3E%20Web%20app)&envLink=https%3A%2F%2Fconsole.firebase.google.com)

---

## 🚀 Setup Guide (Takes 3 Minutes)

You need **0 lines of backend code** and **no paid servers**. Data lives in Google Firebase's free Firestore database, and Vercel hosts the frontend.

### Step 1: Create a Free Firebase Project
1. Go to [console.firebase.google.com](https://console.firebase.google.com) and click **Add project** (name it anything, e.g., `family-calendar` or `team-sync`).
2. In the left sidebar: go to **Build → Firestore Database → Create database**:
   - Select **Start in test mode**.
   - Pick your nearest region and click **Enable**.
3. Under the **Rules** tab, replace the rules with the following so your calendar stays active indefinitely:
   ```javascript
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /{document=**} {
         allow read, write: if true;
       }
     }
   }
   ```
   Click **Publish**.
4. In Project Settings (gear icon ⚙️) → scroll to **Your apps** → click the **`</>`** (Web) icon.
5. Register your app (any nickname) and copy the `firebaseConfig` keys:
   - `apiKey`
   - `authDomain`
   - `projectId`
   - `storageBucket`
   - `messagingSenderId`
   - `appId`

---

### Step 2: Connect to Your Calendar

You can connect Firebase in **two easy ways**:

#### Method A: In Vercel (Recommended for GitHub repos)
1. Push this repository to your GitHub.
2. In your Vercel Dashboard, go to **Settings → Environment Variables**.
3. Add the following variables:
   - `VITE_FIREBASE_API_KEY`
   - `VITE_FIREBASE_AUTH_DOMAIN`
   - `VITE_FIREBASE_PROJECT_ID`
   - `VITE_FIREBASE_STORAGE_BUCKET`
   - `VITE_FIREBASE_MESSAGING_SENDER_ID`
   - `VITE_FIREBASE_APP_ID`
4. Redeploy. Your calendar is now live and automatically connected for everyone who visits your link!

#### Method B: Directly in the Web UI (Zero-configuration deploy)
1. Deploy the site to Vercel without setting any environment variables.
2. Open your live website URL.
3. Click the **⚙️ Settings** icon in the top right header (or the sync badge).
4. Paste your `firebaseConfig` JSON directly into the box and click **Save & Connect**.
5. The badge will turn green (**Synced ✓**) and all connected devices will update live!

---

### Step 3: Run Locally (Optional)

To run or customize the project on your machine:

```bash
# 1. Clone the repository
git clone https://github.com/your-username/shared-calendar.git
cd shared-calendar

# 2. Install dependencies
npm install

# 3. Configure environment variables
cp .env.example .env
# Edit .env and paste your Firebase keys

# 4. Start local development server
npm run dev
```

Visit `http://localhost:3000` in your browser.

---

## ✨ Features

- **4 Interactive Views**:
  - 📅 **Month View**: Date badges, color-coded event dots on mobile, full text pills on desktop, and selected-day agenda drawer.
  - 🕒 **Week View**: 7-day hourly grid with positioned event cards and all-day header.
  - 📆 **Day View**: Focused 24-hour timeline with spacious day badges (no text overlaps).
  - 📋 **Agenda View**: Chronological upcoming events list grouped by date.
- **Full Event CRUD**:
  - Click any event pill to view details, edit times, change calendars, add locations, and take notes.
  - Quick delete (`×`) directly on pills or within dialogs.
- **Multiple Calendars & Categories**:
  - Add custom calendars with built-in color picker.
  - Toggle visibility of any category with a single click.
- **Dual-Mode Data Engine**:
  - **Offline Local Storage**: Automatically saves all your events locally in your browser. Zero setup required to start using it immediately!
  - **Real-Time Firebase Sync**: Connect Firebase to sync changes instantaneously across all devices and team members.
- **Mobile-First Responsive Design**:
  - Bottom-sheet dialogs for mobile thumb reach.
  - Touch-friendly buttons and prevention of iOS Safari auto-zoom.
- **Tools & Backups**:
  - 📤 **iCalendar (.ics) Export**: Import your schedule directly into Google Calendar, Apple Calendar, or Outlook.
  - 💾 **JSON Backup & Restore**: Download or import full calendar backups.
- **⌨️ Keyboard Shortcuts**:
  - `T` — Jump to Today
  - `M` / `W` / `D` / `A` — Switch to Month / Week / Day / Agenda view
  - `N` — Create New Event
  - `/` — Focus Search Bar
  - `Esc` — Close dialogs

---

## 🔒 Security Note

Firebase API keys are designed to identify your Firebase project to Google's servers. By storing them in `.env` and Vercel Environment Variables, your credentials are never exposed in your public GitHub repository.

Access control and data permissions are enforced via **Firestore Security Rules**. For public collaborative calendars, test mode rules allow anyone with the link to read and write events. If you require private user accounts and role-based permissions in the future, Firebase Authentication can be added seamlessly.

---

## 📄 License

MIT License — feel free to fork, customize, and share!
