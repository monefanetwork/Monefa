# 📱 Monefa Wallet for Android — v1.0.1

Official native Android wallet for the Monefa network (XMF). **Kotlin + Jetpack Compose — not a WebView shell.**

- **Download (APK):** [Releases → wallet-android-v1.0.1](../../releases/tag/wallet-android-v1.0.1) · [monefa.net/downloads](https://monefa.net/downloads)
- **Requires:** Android 7.0+ (API 24) · ~8 MB · package `net.monefa.wallet`

---

## ✨ Features

### Wallet
- Login with your existing **monefa.net** account — the same wallet, balance and history everywhere
- Balance in XMF with unlocked / locked breakdown
- **Send** with stealth transfer (mixin = 3) and optional Payment ID
- **Receive** with an on-device generated QR code (ZXing rendering inside the app)
- Full transfer history
- **16-word seed** reveal (Persian wordlist) for backup and recovery

### Mining — remote control (cloud mining)
Start / pause / resume / stop mining that runs on **your own Monefa node or server** via the official `/user-mining` API:

- Solo or Pool mode, adjustable thread count
- Live hashrate, accepted shares, blocks found, session duration
- Network stats (height, difficulty, pool status)

> ⚠️ **Nothing is mined on the phone itself.** This design is intentional: Google Play's *Financial Features* policy prohibits on-device cryptocurrency mining, while remote management of your own infrastructure is allowed. The app is therefore fully compliant for Play Store distribution.

### Explorer
- Latest blocks with live updates, mempool feed
- Block / transaction search

### Security & Privacy
- Session stored in **EncryptedSharedPreferences** (AES-256-GCM)
- Optional **PIN lock** (SHA-256)
- **Zero trackers, zero ads, zero analytics** — the only permission is `INTERNET`
- All traffic goes to `https://monefa.net` (the official node API)

### Localization
- English · فارسی · Русский · العربية · Türkçe — with full RTL support and in-app language switcher

---

## 🛡️ Google Play compliance summary

| Requirement | How the app complies |
|---|---|
| Financial features declaration | Declared as a software wallet; no exchange / custody / lending features |
| On-device mining prohibition | No mining code on the device — remote control of the user's own node only |
| Data safety | Collects: account email, wallet data (server-side), app settings — no third-party sharing, encrypted in transit and at rest |
| Target API level | targetSdk 35 (current Play requirement) |
| Account deletion | Wallet data can be deleted server-side on request; app logout clears local session |
| Privacy policy | https://monefa.net/privacy |

---

## 🔐 Verification

sha256 of `MonefaWallet-v1.0.1.apk`:

```
133ef232d3d4f1137d7ff501facc681f87467f7ab96271c5b11471d8378d805b
```

> 🔧 **v1.0.1 hotfix** — fixes the first-launch crash in v1.0.0 (`UninitializedPropertyAccessException` during app startup). versionCode 2, installs directly over v1.0.0. Same signature.

The APK is signed with the official Monefa release key. Android will warn about unknown sources when sideloading — this is normal outside Play Store.

---

## 📦 Installation (sideload)

1. Download the APK from the link above.
2. Open it and allow *Install unknown apps* for your browser/file manager if asked.
3. Log in with your monefa.net account — or create a wallet on the website first.

> 🍎 iOS version is planned. Until then, the web wallet at [monefa.net](https://monefa.net) works on any iPhone browser.
