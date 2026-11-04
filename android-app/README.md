# Android app (Neon Arcade)

The website (index.html on GitHub Pages) uses short 4-letter room codes.
This folder builds the Android app version, which uses 6-digit number codes.
Both run the same index.html: `inject.html` sets
`window.ARCADE_CONFIG = { app:true, codeDigits:6 }` in the app copy only.
App rooms and website rooms are separate — join from the same version.

Every push to `main` builds an APK (see `.github/workflows/android-apk.yml`)
and posts it under **Releases → Latest**.

- `capacitor.config.json` — app ID, name, background colour
- `permissions.txt` — Android permissions (microphone for voice chat)
- `native/MainActivity.java` — fullscreen, keeps the screen awake
- `res/` — launcher icons

Signing: repo secrets `ANDROID_KEYSTORE_B64` and `ANDROID_KEYSTORE_PASSWORD`
(same key as the other apps). Without them each build uses a throwaway key.
