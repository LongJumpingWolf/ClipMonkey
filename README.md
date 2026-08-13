# ClipMonkey

Single-file web app. Paste or drop an image, uploads to ImgBB, keeps a numbered
local log of names + links. No backend, no database — everything lives in
this browser's localStorage.

## Deploy to Vercel

**Fastest — CLI, no GitHub needed:**
```
cd clipmonkey
npx vercel --prod
```
Follow the prompts (link/create a project). Done in under a minute.

**Or — GitHub-connected, matches your other projects:**
```
git init
git add . && git commit -m "clipmonkey" && git push origin main
```
Then in the Vercel dashboard: New Project → Import this repo → Deploy.
No build settings needed — it's static, Vercel serves `index.html` as-is.

## After deploying

1. Open the live URL.
2. Click the ⚙ settings icon → paste your ImgBB API key (free at
   [api.imgbb.com](https://api.imgbb.com/)) → Save.
3. Paste (Ctrl+V) or drop an image anywhere on the page.

## Icons

Full icon set generated from the logo, wired into `index.html`'s `<head>`:

- `favicon.ico`, `icons/favicon-16x16.png`, `icons/favicon-32x32.png`, `icons/favicon-48x48.png` — browser tab icon
- `apple-touch-icon.png` (180×180) — iOS home screen / bookmarks
- `icons/icon-192.png`, `icons/icon-512.png` — Android/PWA manifest icons
- `icons/icon-512-maskable.png` — Android adaptive icon (safe full-bleed)
- `icons/mstile-150x150.png` — Windows tile
- `site.webmanifest` — makes it installable as a PWA (Add to Home Screen / Install App)

All paths in `index.html` are absolute (`/icons/...`), so they only resolve
correctly once deployed at a domain root — they won't show up if you just
double-click `index.html` locally. That's expected.

## Notes

- Needs to run over `https://` (which Vercel gives you automatically) —
  clipboard access is blocked on plain `file://` pages.
- Data is per-browser, per-device. There's no sync — it's intentionally
  local-only. Use the 📤 Export button for a portable backup file.
- Dragging images from other websites depends on that site allowing
  cross-origin fetches (CORS). Paste and direct file drops always work
  regardless.
