# Sahod Planner (mobile app)

The Sahod Planner artifact, turned into an installable phone app (PWA). It works offline once it's installed, and it keeps your numbers on the phone.

## Files
- `index.html`: the whole app
- `manifest.webmanifest`: app name, icon and colours used when you install it
- `sw.js`: offline support (caches the app and fonts)
- `icons/`: home-screen icons
- `vendor/qrcode.min.js`: QR code generator ([qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator), MIT)

## Run it on this PC
```
python -m http.server 8795 --directory sahod-planner-app
```
Then open http://localhost:8795.

## Put it on your phone
Phones only install apps from an HTTPS site, so host this folder somewhere free first, such as GitHub Pages, Netlify Drop or Cloudflare Pages. Then:
- **Android (Chrome):** open the link, tap ⋮ → **Install app** (or **Add to Home screen**).
- **iPhone (Safari):** open the link, tap Share → **Add to Home Screen**.

## Make it an APK (Android)
If you want an APK file you can send to people or put on the Play Store, use the free website [PWABuilder](https://www.pwabuilder.com):

1. Paste `https://callistaaa111.github.io/sahod-planner/` into it and start.
2. Choose **Package for stores → Android**.
3. Download the zip. It has an `.apk` you can install or send to anyone, and an `.aab` for the Play Store. Keep the signing key file from the zip somewhere safe; you need it to publish updates on the Play Store.

The APK still loads the app from GitHub Pages, so changes pushed here reach everyone automatically. To install the APK, the phone has to allow **Install unknown apps** for the app it's opened from, such as Files or Messenger.

You may not need an APK at all: on Android, **Chrome → ⋮ → Install app** already installs it as a real app. iPhones can't install APKs; use Safari's **Add to Home Screen** instead.

## Move your numbers to another phone
In **Setup → Move to another phone**:
- **Share to another phone** sends a link through Messenger, Viber, email and so on. Open it on the other phone in Chrome or Safari, then tap **Load these numbers**.
- **Show QR code**: scan it with the other phone's camera, then tap the link. Spending logs older than 60 days are left out to keep the code scannable.

Your numbers travel inside the link itself, after the `#`. That part never reaches GitHub's servers, so nothing is uploaded. Anyone you send the link to can load your numbers, though.

## Notes
- Each phone keeps its own data.
- The artifact's "Saved to your account" sync only works inside claude.ai, so this version saves on the phone only.
- After you change `index.html`, raise `CACHE` in `sw.js` (for example `sahod-v2`) so installed phones pick up the update.
