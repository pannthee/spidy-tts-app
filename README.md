# Spidy TTS

Personal Text-to-Speech Android app (Capacitor + React).

- Engine: Microsoft Edge TTS, edge-tts 7.3.1 wire protocol (Sec-MS-GEC token
  generated in-app, no API key, free)
- Voices: Burmese Nilar + Thiha, plus 12 Multilingual voices
- Script up to 5,000 chars per generation; long text auto-chunked
  (sentence-based, ~800 chars/chunk, parallel pool), merged into one MP3
- Speed: 0.50x to 2.00x slider
- History list (last 20) with replay + download; output MP3 saves to Documents/SpidyTTS/ on the phone

## Build the APK with GitHub Actions

1. Create an empty **public** GitHub repo named `spidy-tts-app`
   (no README / .gitignore / license).
2. Push this project to it (or let Muse push it).
3. Open the repo's **Actions** tab — the "Build Spidy TTS APK" run
   starts automatically on push. When it finishes, download the
   `spidy-tts-apk` artifact, unzip, and install `app-debug.apk`.

Note: Android launcher/splash PNGs are stored base64-encoded in
`scripts/android-assets.json` (the push route only carries text files);
the workflow restores them with `scripts/restore-android-assets.py`
before the Gradle build. `public/logo.png` is unused and not shipped.

## Local dev

```bash
npm install
npm run build
npx cap sync android
```
