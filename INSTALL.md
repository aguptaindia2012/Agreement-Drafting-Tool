# DroCon Bharat Agreement Studio — Install Guide

This bundle turns the Agreement Studio into an **installable app** for laptops
(Windows / macOS) and **Android phones**, using a single shared codebase (a PWA —
Progressive Web App). Once installed it opens in its own window like a normal app,
works offline, and keeps your saved drafts on that device.

## What's in this folder
- `index.html` — the app
- `manifest.webmanifest` — app name, icons, colours
- `service-worker.js` — enables installation + offline use
- `icons/` — the DCB app icons

> ⚠️ **Important:** the install feature only works when the folder is **served over a web
> address (http/https)** — not when you double-click the file. Browsers block app
> installation from `file://`. Pick one of the hosting options below (Option A is the
> easiest and is free).

---

## Step 1 — Put the app online (one-time, ~5 minutes)

### Option A — Netlify Drop (free, easiest, recommended)
1. Go to **https://app.netlify.com/drop**
2. Drag this **entire folder** onto the page.
3. Netlify gives you a link like `https://your-name.netlify.app`.
4. Share that link with your team. Done — everyone installs from there.

### Option B — GitHub Pages (free)
1. Create a free GitHub account and a new repository.
2. Upload all files from this folder (keep the `icons` folder).
3. Repo **Settings → Pages → Deploy from branch → main → /(root)**.
4. Use the published `https://…github.io/…` link.

### Option C — Your own server / intranet
Copy this folder to any web server (or company intranet) that serves over **https**.
Open the folder's `index.html` URL.

### Option D — Just run it locally on one laptop (no hosting)
If you only need it on one machine and don't need the "Install" button, you can run a
tiny local server:
- Install Node.js, then in this folder run: `npx serve` (gives a `http://localhost:3000` link), **or**
- With Python: `python -m http.server 8080` then open `http://localhost:8080`.
Installation works from `http://localhost` too.

---

## Step 2 — Install on a laptop (Chrome or Edge)
1. Open the hosted link.
2. Click **⤓ Install app** in the top bar — **or** the install icon in the browser's
   address bar (a small monitor/▾ icon), then **Install**.
3. It now appears in your Start Menu / Applications and opens in its own window.

(Safari on macOS: use the **Share → Add to Dock** option.)

## Step 3 — Install on an Android phone (Chrome)
1. Open the hosted link in **Chrome**.
2. Tap **⤓ Install app**, **or** the **⋮** menu → **Add to Home screen / Install app**.
3. The DCB icon appears on your home screen and opens full-screen like a native app.

(iPhone/iPad Safari: **Share → Add to Home Screen**.)

---

## Notes
- **Drafts are saved per-device** (in the browser of that install). They are *not* shared
  between laptops/phones automatically. To move a draft, use **Save JSON draft** and
  **Open JSON Draft** on the other device.
- **Offline:** after the first online open, the app and its libraries are cached, so it
  keeps working without internet. The very first load needs internet.
- **Updates:** when you replace the files on the host with a newer version, installed apps
  pick up the update automatically the next time they're opened (online).

## Advanced — a real Google Play Store app (optional)
A PWA can be wrapped into a Play Store APK/AAB without rewriting anything:
1. Host the app (Step 1).
2. Go to **https://www.pwabuilder.com**, paste your hosted link, and it generates a
   signed Android package plus store-listing assets.
This is optional — for internal team use, installing directly from the link (Step 3) is
simpler and needs no Play Store account.
