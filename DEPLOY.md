# CFB Super App — Mobile Build · Deploy Guide

Self-contained PWA build of the clickable prototype. Auto-scales from iPhone SE (320px) through Pro Max / large Android (430px+) and small tablets; respects notches and home-indicator safe areas; installable to the home screen; works offline after first load.

## Fastest: Netlify Drop (~30 seconds, free)
1. Go to https://app.netlify.com/drop
2. Drag this entire `Mobile Build` folder onto the page
3. Open the generated URL on any phone → Share → **Add to Home Screen**

## Alternatives
- **GitHub Pages:** push this folder to a repo → Settings → Pages → deploy from branch.
- **Vercel:** `vercel deploy` from this folder, or drag onto vercel.com/new.
- **Local network test:** run `python3 -m http.server 8000` in this folder, then open `http://<your-computer-ip>:8000` on a phone connected to the same Wi-Fi.

Note: the service worker (offline + install prompt) activates only over http(s) — opening index.html directly from the file system still works fully as a clickable prototype, just without install/offline.

## What's in the box
- `index.html` — the entire app (26 screens, all interactions)
- `manifest.webmanifest` — home-screen install metadata (standalone, portrait)
- `sw.js` — cache-first service worker for offline use
- `icon-192.png` / `icon-512.png` — app icons

## Device behavior
- **Phones (or any touch device ≤768px):** true fullscreen app — no phone frame, no simulated status bar; native status bar area and home indicator are padded via safe-area insets; 100dvh so browser chrome collapse doesn't clip the tab bar.
- **Large phones/small tablets (520–768px):** content column capped at 520px, centered, so cards don't stretch.
- **Desktop (>768px):** review mode — framed phone with the screen-map sidebar, same as the design prototype.
- Typography scales fluidly (clamp) so hero titles never wrap awkwardly on narrow devices.
