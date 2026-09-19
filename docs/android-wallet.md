# 📱 Monefa Wallet for Android — v1.0.2

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

### Mining — two modes

**1. On this phone (CPU)** — real on-device mining through the official pool (`monefa.net:3333` stratum):

- Native Kotlin implementation of the Monefa PoW (keccak-512 + 128 KB memory-hard scratchpad + 2048 iterations) — verified against the node's reference implementation
- Foreground service with a persistent notification, start/pause/stop always under your control, never auto-started
- Thread count control (1–8), live hashrate, accepted/rejected shares, uptime

> ⚠️ Mining uses the CPU intensively and consumes battery. It runs **only** when you explicitly start it.

**2. Remote control (cloud mining)** — start/pause/resume/stop mining on **your own Monefa node or server** via the `/user-mining` API: solo/pool mode, thread count, live hashrate, shares, blocks found.

> 🛡️ For the **Google Play build**, on-device mining is compiled out (`PHONE_MINING = false` in `app/build.gradle.kts`) per the Play *Financial Features* policy; the sideload APK ships with it enabled.

### Explorer
- Latest blocks with live updates, mempool feed
- Block / transaction search

### Security & Privacy
- Session stored in **EncryptedSharedPreferences** (AES-256-GCM)
- Optional **PIN lock** (SHA-256)
- **Math captcha** on login/register (HMAC-signed, server-verified)
- **Zero trackers, zero ads, zero analytics** — network access only; no location, no contacts, no advertising IDs
- All traffic goes to `https://monefa.net` (the official node API) and the official pool

### Localization
- English · فارسی · Русский · العربية · Türkçe — with full RTL support and in-app language switcher

---

## 🛡️ Google Play compliance summary

| Requirement | How the app complies |
|---|---|
| Financial features declaration | Declared as a software wallet; no exchange / custody / lending features |
| On-device mining prohibition | **Play build ships with phone mining compiled out** (`PHONE_MINING = false`); remote control of the user's own node remains. The sideload APK has opt-in, user-initiated phone mining |
| Data safety | Collects: account email, wallet data (server-side), app settings — no third-party sharing, encrypted in transit and at rest |
| Target API level | targetSdk 35 (current Play requirement) |
| Account deletion | Wallet data can be deleted server-side on request; app logout clears local session |
| Privacy policy | https://monefa.net/privacy |

---

## 🔐 Verification

sha256 of `MonefaWallet-v1.0.2.apk`:

```
23dba7ed0740e57ef5820c36de1d27831b8789bcd8a89fefef928512f1446e38
```

> 🔧 **v1.0.2** — real on-device CPU mining (opt-in, pool stratum), math captcha on login/register, live hashrate. Includes the v1.0.1 launch-crash fix. versionCode 3, installs over previous versions. Same signature.

The APK is signed with the official Monefa release key. Android will warn about unknown sources when sideloading — this is normal outside Play Store.

---

## 📦 Installation (sideload)

1. Download the APK from the link above.
2. Open it and allow *Install unknown apps* for your browser/file manager if asked.
3. Log in with your monefa.net account — or create a wallet on the website first.

> 🍎 iOS version is planned. Until then, the web wallet at [monefa.net](https://monefa.net) works on any iPhone browser.
