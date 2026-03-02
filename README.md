# MHXR APK Patcher

In-browser patcher for Monster Hunter Explore (MHXR) v09.03.06. Patches the Android APK to connect to an [Apypos](https://github.com/Houmgaor/apypos-server) private server — entirely client-side, no server needed.

**Live**: [https://houmgaor.github.io/mhxr-patcher/](https://houmgaor.github.io/mhxr-patcher/)

## What it does

1. **URL redirect** — Replaces the hardcoded Capcom dispatch URL with your server address (both arm64-v8a and armeabi-v7a)
2. **SafetyNet bypass** — Patches `sSafetyNet::isComplete()` and `sSafetyNet::move()` in the native binary
3. **SafetyNet Java stub** — Replaces the SafetyNet attestation method in DEX bytecode
4. **GMS bypass** (optional) — Stubs Google Play Services methods that crash without GMS
5. **Cleartext HTTP** — Adds `usesCleartextTraffic="true"` to AndroidManifest.xml binary XML
6. **JAR v1 signing** — Signs the patched APK with an ephemeral RSA key

All patching runs in your browser using [JSZip](https://stuk.github.io/jszip/) and [node-forge](https://github.com/digitalbazaar/forge). No data is uploaded anywhere.

## Usage

1. Visit the [patcher page](https://houmgaor.github.io/mhxr-patcher/)
2. Upload the MHXR v09.03.06 APK (or click "download it automatically")
3. Enter your Apypos server address (e.g. `192.168.1.100:8080`)
4. Click **Patch APK**
5. Download the patched APK and install on your device

## Hosting

This is a single `index.html` file with no build step. To host it yourself:

```bash
# Any static file server works
python3 -m http.server 8000
# or
npx serve .
```

## License

AGPL-3.0 — same as [apypos-server](https://github.com/Houmgaor/apypos-server).
