# DataBridge — Install on Your Phone
### Two paths: APK (Android sideload) + PWA (iPhone & Android)

---

## PATH A — Android APK via GitHub (free, ~8 minutes)

This builds your APK automatically in GitHub's cloud — no Android Studio needed.

### 1. Create a free GitHub account
Go to https://github.com → Sign up (free)

### 2. Create a new repository
- Click the **+** icon → **New repository**
- Name it: `databridge`
- Set to **Public**
- Click **Create repository**

### 3. Upload the project files
On the new repo page click **"uploading an existing file"** link, then:
- Drag the entire contents of this zip (all files/folders) into the upload area
- Make sure these are included:
  - `src/` folder (with App.jsx + main.jsx)
  - `public/` folder (with icon files)
  - `.github/workflows/build-apk.yml`  ← THE MOST IMPORTANT ONE
  - `package.json`, `vite.config.js`, `index.html`, `capacitor.config.json`
- Scroll down → click **"Commit changes"**

### 4. Watch the APK build automatically
- Click the **"Actions"** tab at the top of your repo
- You'll see **"Build Android APK"** running (takes 4–6 minutes)
- When it shows a green ✅ tick, click on it
- Scroll down to **"Artifacts"** section
- Click **"DataBridge-debug-APK"** to download the zip
- Extract the zip — inside is `app-debug.apk`

### 5. Install the APK on your Android phone
On your Android phone:
1. Transfer the `app-debug.apk` to your phone (WhatsApp, email, USB, Google Drive)
2. Open the file on your phone
3. If prompted, tap **"Allow from this source"** in Settings
4. Tap **Install**
5. Done — DataBridge appears on your home screen!

---

## PATH B — PWA on iPhone Safari (5 minutes, no build needed)

### 1. Deploy to Netlify
1. Go to https://netlify.com → sign up free
2. Click **"Add new site"** → **"Deploy manually"**

But wait — you need to build first. Two options:

**Option 1 — GitHub auto-deploy (easiest):**
- In Netlify → "Import from Git" → connect your GitHub repo
- Build command: `npm run build`
- Publish directory: `dist`
- Click Deploy — Netlify builds AND hosts it automatically
- Every time you push to GitHub, it redeploys

**Option 2 — Build on your Windows PC:**
```
cd databridge-full
npm install
npm run build
```
Then drag the `dist/` folder to Netlify's manual deploy page.

### 2. Install on iPhone
1. Open **Safari** on your iPhone (must be Safari)
2. Go to your Netlify URL e.g. `https://databridge-abc.netlify.app`
3. Tap the **Share** button (box with ↑ arrow, bottom of screen)
4. Scroll down → tap **"Add to Home Screen"**
5. Name it `DataBridge` → tap **Add**

Your app is now on your iPhone home screen.
Opens fullscreen, works offline, feels like a native app. ✅

---

## Re-triggering the APK build any time

If you update the code and push to GitHub, it builds automatically.
Or go to: **GitHub → Actions → "Build Android APK" → "Run workflow"**

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Actions tab not showing workflow | Make sure `.github/workflows/build-apk.yml` was uploaded |
| "Cannot install" on Android | Go to Settings → Apps → Special access → Install unknown apps → allow your file manager |
| PWA not showing "Add to Home Screen" | Must use Safari, not Chrome, on iPhone |
| Netlify deploy fails | Check build command is `npm run build` and publish dir is `dist` |
