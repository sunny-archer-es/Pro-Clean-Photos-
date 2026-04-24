# Sunny Archer Services — Photo Sharing App

Drop photos into a folder, name them, add a note, and share a private Google Drive link — all from your browser, including iPhone.

---

## What the app does

1. You drop photos into the app
2. It asks you to rename each photo one by one
3. You add an optional text note
4. It uploads everything to a new folder in your Google Drive
5. You get a shareable link — anyone with the link can view the folder

---

## Files

| File | Description |
|------|-------------|
| `sunny-archer-services.html` | The entire app — one file, no install needed |
| `README.md` | This setup guide |

---

## One-time setup (~5 minutes)

### Step 1 — Host the app on GitHub Pages

1. Go to [github.com](https://github.com) and create a free account (or sign in)
2. Create a new repository, e.g. `Pro-Clean-Photos-`
3. Upload `sunny-archer-services.html` — rename it to `index.html` if you want a cleaner URL
4. Go to the repository **Settings** → **Pages**
5. Under Source, select **main** branch → click Save
6. Your app will be live at:
   ```
   https://sunny-archer-es.github.io/Pro-Clean-Photos-/
   ```

---

### Step 2 — Create a Google Cloud project

1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Click the project dropdown at the top → **New Project**
3. Give it a name (e.g. `Sunny Archer Services`) → click **Create**

---

### Step 3 — Enable Google Drive API

1. In your project, go to **APIs & Services** → **Library**
2. Search for **Google Drive API**
3. Click it → click **Enable**

---

### Step 4 — Create an OAuth Client ID

1. Go to **APIs & Services** → **Credentials**
2. Click **+ Create Credentials** → choose **OAuth 2.0 Client ID**
3. If prompted to configure the consent screen first, click **Configure Consent Screen** → choose **External** → fill in App name (`Sunny Archer Services`) and your email → Save
4. Back in Credentials → **+ Create Credentials** → **OAuth 2.0 Client ID**
5. Application type: **Web application**
6. Name: anything (e.g. `Sunny Archer App`)
7. Under **Authorised JavaScript origins** → click **+ Add URI** → enter:
   ```
   https://sunny-archer-es.github.io
   ```
   ⚠️ Just the domain — no path at the end
8. Click **Create**
9. A popup shows your **Client ID** — it looks like:
   ```
   123456789-abc123xyz.apps.googleusercontent.com
   ```
   Copy it and keep it handy

---

### Step 5 — Add yourself as a test user

1. Go to **APIs & Services** → **OAuth consent screen**
2. Scroll down to **Test users** → click **+ Add users**
3. Enter your Gmail address:
   ```
   sunny.archer.es@gmail.com
   ```
4. Click **Save**

> Without this step, Google will show an "access denied" error when you try to sign in.

---

### Step 6 — Paste the Client ID into the app

1. Open the app in your browser:
   ```
   https://sunny-archer-es.github.io/Pro-Clean-Photos-/
   ```
2. You'll see a dark setup banner at the top
3. Paste your Client ID into the input field
4. Click **Save & Continue**
5. The banner disappears — the app remembers your Client ID from now on

---

## Using the app on iPhone

Open Safari and go to:
```
https://sunny-archer-es.github.io/Pro-Clean-Photos-/
```

To add it to your home screen:
1. Tap the **Share** button (box with arrow) in Safari
2. Tap **Add to Home Screen**
3. Tap **Add**

It will appear as an app icon on your home screen.

---

## How the share link works

When you finish uploading, the app creates a folder in your Google Drive and sets it to **"anyone with the link can view"**. The link looks like:

```
https://drive.google.com/drive/folders/1aBcDeFgHiJk...
```

The folder ID in the URL is a long random string — it's unguessable. Anyone you send it to can open the photos without needing a Google account.

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "Access denied" error on sign-in | Add your Gmail to Test users (Step 5) |
| Sign-in popup is blocked | Allow popups for the site in your browser settings |
| "Client ID not valid" | Make sure you added `https://sunny-archer-es.github.io` (no trailing slash) to Authorised JavaScript origins |
| App not loading on GitHub Pages | Wait 1–2 minutes after enabling Pages — it takes a moment to go live |
| Photos not uploading | Your Google access token may have expired — refresh the page and sign in again |

---

## Notes

- The app stores your Client ID in your browser's local storage — you only need to enter it once per device
- Files are uploaded directly to **your** Google Drive account — Sunny Archer Services never stores your photos
- The app works entirely in the browser — no server, no backend, no data collection
