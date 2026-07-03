# AppRove Setup Guide

Follow this top to bottom. If you've already done a step, just check it and move on.

---

## Part 1 — Google Cloud (one-time, not per person)

1. Go to **console.cloud.google.com**, sign in with your **personal Gmail** (not your company account — your company's Workspace blocks some of this).
2. Top bar → "Select a project" → make sure you're in the project you created earlier (or make a new one: **New Project** → name it anything → Create).
3. Left menu → **APIs & Services → Library** → search **"Google Drive API"** → click it → **Enable**.
4. Left menu → **APIs & Services → Credentials** → **+ Create Credentials → OAuth client ID**.
   - Application type: **Web application**
   - Under "Authorized JavaScript origins," add: `https://orubanenko7-source.github.io`
   - Click **Create**
   - **Copy the Client ID** it shows you (looks like `123456-abc.apps.googleusercontent.com`) — save it somewhere, you'll need it once in the app.
5. Left menu → **APIs & Services → Google Auth Platform → Audience** tab:
   - User type: **External**
   - Publishing status: **Testing**
   - Under "Test users" → **+ Add Users** → add the Gmail address of **all 3 project managers** (including yourself if you're one of them).
6. Still in Google Auth Platform, find **Data Access** (or the Scopes section) → **Add or Remove Scopes** → in the "Manually add scopes" box at the bottom, paste:
   ```
   https://www.googleapis.com/auth/drive
   ```
   → **Add to table** → **Update/Save**.

✅ You only do Part 1 once, no matter how many project managers use the app.

---

## Part 2 — Google Drive folders (repeat for EACH of the 3 project managers)

Each PM needs their own set of 3 folders, and only they get Editor access to their own set.

For **each PM**, do this:

1. In Google Drive, create a new folder — name it something like `[PM Name] - Inbox`.
2. Inside that same folder (or right next to it), create two more folders: `[PM Name] - Approved` and `[PM Name] - Needs Review`.
3. Right-click the parent/Inbox folder → **Share** → add that specific PM's Google account → set their role to **Editor** → Send/Save.
   - (If you nested Approved/Needs Review inside the Inbox folder, sharing the parent folder as Editor automatically covers the subfolders too.)
4. Open each of the 3 folders and copy its **folder ID** from the browser address bar — it's the long string after `/folders/`, e.g.:
   `https://drive.google.com/drive/folders/`**`1AbCdEfGhIJKlmnop`**
5. Write down, for this PM: **Inbox ID**, **Approved ID**, **Needs Review ID**.

Repeat this for all 3 people. You should end up with 9 folder IDs total (3 folders × 3 people).

---

## Part 3 — GitHub Pages (one-time, likely already done)

Skip this if `https://orubanenko7-source.github.io/approve/` (or whichever repo you used) is already live and loading the AppRove instructions screen.

1. github.com → your repo → confirm `index.html` contains the latest AppRove app code.
2. Repo → **Settings → Pages** → Source: **Deploy from a branch**, Branch: **main**, Folder: **/ (root)** → Save.
3. Wait ~1 minute, refresh that page, confirm the green "your site is live at ..." link.

---

## Part 4 — Set up the app itself

1. On your phone, open your live GitHub Pages link in Safari.
2. Tap ⚙️ **Settings** (top right).
3. Paste the **Client ID** from Part 1, step 4 into "Google OAuth Client ID (shared)."
4. Tap **"+ Add Project Manager"**. For PM #1, fill in:
   - Name
   - A 4-digit PIN (different from the other 2 PMs)
   - Their Inbox / Approved / Needs Review folder IDs from Part 2
   - Tap **Save**
5. Repeat step 4 for PM #2 and PM #3.
6. Tap **Save** on the main Settings screen.

---

## Part 5 — Test it

1. Tap Continue past the instructions screen.
2. Enter one PM's PIN.
3. Tap **Sign in with Google**, and sign in with **that same PM's** Google account (the one you shared their folders with).
4. Drop a test PDF into that PM's Inbox folder in Drive, then tap **Retry** if needed.
5. Swipe it right (or tap ✓) — check that it actually moved into that PM's Approved folder in Drive.
6. Tap 🔒 **Log out**, and repeat with the next PM's PIN + their own Google sign-in.

---

### If something breaks
Tell me exactly which numbered step you're on and paste the exact error text you see (from the app, or from a browser/Google/GitHub error page) — that's the fastest way for me to help.
