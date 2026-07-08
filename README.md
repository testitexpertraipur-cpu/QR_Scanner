# QR Scanner PWA

A tiny (176 KB total), installable, offline-capable QR code scanner. No server, no database, no account, no recurring cost — runs entirely in the browser.

## What's inside
- `index.html` — the whole app (UI + camera scan loop + upload-from-photo fallback + local scan history)
- `jsQR.min.js` — the decoding library, bundled locally (no CDN dependency, works offline)
- `manifest.json` — makes it installable ("Add to Home Screen") on Android, iOS, and desktop
- `sw.js` — service worker that caches everything on first visit, so it keeps working with no internet after that
- `icon-192.png`, `icon-512.png` — app icons

## Why it works everywhere
- Plain HTML/CSS/JS — no framework, no build step.
- Camera access uses the standard `getUserMedia` API, supported on every modern browser (Chrome, Safari, Firefox, Edge, Samsung Internet) on Android, iOS, Windows, macOS, and Linux.
- If a device has no camera or denies permission, users can still scan by picking a photo.

## One important rule: it must be served over HTTPS
Browsers only allow camera access on secure origins (`https://`) or `localhost`. Opening `index.html` directly from a folder (`file://`) will NOT allow the camera — this is a browser security rule, not a bug in the app.

## Free hosting (zero cost, lifetime)
**GitHub Pages** is the simplest zero-cost option and gives you HTTPS automatically:
1. Create a new GitHub repository (e.g. `qr-scanner`).
2. Upload these files to the repo root (or a `/docs` folder).
3. In the repo, go to **Settings → Pages**, set the source branch/folder, and save.
4. GitHub gives you a URL like `https://yourname.github.io/qr-scanner/` — that's it, live and free forever.
5. Open that link on a phone and tap **Install** (Android/Chrome) or **Share → Add to Home Screen** (iOS Safari) to add it as an app icon.

Other equally free HTTPS options if preferred: Cloudflare Pages, Netlify, Vercel — all work the same way (drag-and-drop the folder, get an HTTPS link).

## Local testing
```
npx serve .
```
then open the `https://localhost` or `http://localhost` link it gives you (localhost is exempt from the HTTPS rule).

## Customizing
- Colors/branding: edit the CSS variables at the top of `index.html` (`--bg`, `--amber`, etc.) and swap `icon-192.png` / `icon-512.png`.
- App name shown on the home screen: edit `name`/`short_name` in `manifest.json`.
