# Sahod Planner (mobile app)

The Sahod Planner artifact, turned into an installable phone app (PWA). It works offline once it's installed, and it keeps your numbers on the phone.

## Files
- `index.html`: the whole app
- `manifest.webmanifest`: app name, icon and colours used when you install it
- `sw.js`: offline support (caches the app and fonts)
- `icons/`: home-screen icons

## Run it on this PC
```
python -m http.server 8795 --directory sahod-planner-app
```
Then open http://localhost:8795.

## Put it on your phone
Phones only install apps from an HTTPS site, so host this folder somewhere free first, such as GitHub Pages, Netlify Drop or Cloudflare Pages. Then:
- **Android (Chrome):** open the link, tap ⋮ → **Install app** (or **Add to Home screen**).
- **iPhone (Safari):** open the link, tap Share → **Add to Home Screen**.

## Notes
- Each phone keeps its own data. To move to another phone, use **Setup → Backup** to copy a code and paste it on the new phone.
- The artifact's "Saved to your account" sync only works inside claude.ai, so this version saves on the phone only.
- After you change `index.html`, raise `CACHE` in `sw.js` (for example `sahod-v2`) so installed phones pick up the update.
