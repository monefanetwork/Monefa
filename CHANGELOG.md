# 📜 Monefa Network — Changelog & Updates

All notable updates of the Monefa network, wallets and tools.
Official binaries: [Releases](../../releases) · Live network: [monefa.net](https://monefa.net)

---

## [Android Wallet v1.0.2] — 2026-09

Mining on the phone's own CPU + captcha.

### Real on-device mining (opt-in)
- Native Kotlin implementation of the Monefa PoW (keccak-512, 128 KB memory-hard scratchpad, 2048 iterations) — verified hash-exact against the node's reference implementation via automated vectors
- Connects to the official pool stratum `monefa.net:3333` (subscribe/authorize/notify/submit, auto-reconnect, difficulty handling)
- Foreground service with persistent notification — only starts by explicit user action, stop anytime from the notification or the app
- Thread count control (1–8), live hashrate, accepted/rejected shares, uptime
- For Google Play builds the feature is compiled out (`PHONE_MINING = false`) per Play Financial-features policy

### Security
- Math captcha (HMAC-signed, 5-min validity) now required on login/register — mirrored on the website
- Includes the v1.0.1 launch-crash fix

### Fixes
- Live hashrate now always visible on the Mining screen (local and cloud modes)
- versionCode 3 (versionName 1.0.2) — installs directly over previous versions
- sha256: `23dba7ed0740e57ef5820c36de1d27831b8789bcd8a89fefef928512f1446e38`

---

## [Android Wallet v1.0.1] — 2026-09

Hotfix release — fixes the first-launch crash present in v1.0.0.

- **Crash on every launch fixed**: `kotlin.UninitializedPropertyAccessException: lateinit property plain has not been initialized` — `MonefaApp.attachBaseContext` read the language preference before the store was initialized
- Store rewritten with lazy, crash-proof initialization — safe to access from any phase, including `attachBaseContext`
- Additional resilience: if a device's KeyStore is broken, the app now falls back to app-private storage instead of crashing
- versionCode 2 (versionName 1.0.1) — installs directly over v1.0.0, same signing key
- sha256: `133ef232d3d4f1137d7ff501facc681f87467f7ab96271c5b11471d8378d805b`

---

## [Android Wallet v1.0.0] — 2026-09

First official native mobile wallet — **Kotlin + Jetpack Compose, no WebView**.

### Wallet
- Same monefa.net account as the web: login, balance (unlocked/locked), transfer history
- Stealth transfers (mixin = 3) with optional Payment ID
- Receive with on-device QR generation, 16-word seed reveal (Persian wordlist)

### Mining (remote control — cloud mining)
- Start / pause / resume / stop mining on the user's own node or server (`/user-mining` API)
- Solo/Pool mode, thread count, live hashrate, shares, blocks found, network stats
- Nothing mines on the phone — designed for Google Play Financial-features policy compliance

### Security & Privacy
- EncryptedSharedPreferences (AES-256-GCM) session storage, optional PIN lock (SHA-256)
- Zero trackers/ads — only `INTERNET` permission; all traffic to https://monefa.net
- Privacy policy live at monefa.net/privacy

### Localization
- EN / FA / RU / AR / TR with full RTL and in-app language switcher
- APK: `MonefaWallet-v1.0.0.apk` (~8 MB, signed release build, minSdk 24, targetSdk 35)

---

## [Network v2.1.0] — 2026-09

### Telegram Mini App (rebuilt)
- Fixed Telegram initData authentication (signature verification) — Mini App now works for all users
- Rebuilt on the real database schema: balance, transfer history, real Pay invoices
- Mining tab: real browser mining with server-side share validation, per-thread control, payouts to your own wallet
- Full UI internationalization — EN / FA / RU / AR / TR with auto language detection and RTL support

### Security
- Stateless math captcha (SVG formula, HMAC-signed, single-use) restored for web and GUI wallet login
- Removed default admin credentials — first boot now generates a random password (`M-xxxx`) printed to the log
- Server-side validation hardened for browser-mining share submission

### Monefa Pay
- **My Payment Links** — merchants can create persistent payment links (fixed or free amount), stored in DB, with public claim pages (`/pay/l/{code}`) and soft deactivation
- Invoice flow with QR codes and live payment status

### Bot & Explorer
- Bot explorer rewritten: block height, transaction hash (including pending mempool transactions), block hash search, and a privacy notice for wallet addresses
- Node `/tx` endpoint now covers the mempool

### Node
- Removed automatic mining resume on node boot — server mining starts only via an explicit admin action
- Browser-mining endpoints accept explicit payout addresses (referral-safe)

---

## [GUI Wallet v1.1.0] — 2026-09

- Built-in CPU mining: pool mode (auto jobs from the Monefa pool) or solo mode, per-thread control, live hashrate / accepted shares / duration — payouts to your own address
- 9 languages with full RTL: English, فارسی, Русский, العربية, Türkçe, 中文, Español, Deutsch, हिन्दी
- Math captcha on login (server-verified)
- monero-gui style UX: dark theme (#2b2b2b + orange #F26822), sidebar, multi-step wizard, balance hero, confirm modals
- View Key export, mnemonic recovery, QR codes
- Verified end-to-end on live mainnet: ~11.7 KH/s on 2 threads, 57 accepted shares, 0 rejected

---

## [CLI Miner v1.1.0] — 2026-09

- First standalone binary release — no runtime installation needed
- Windows x64 (`monefa-miner-1.1.0-win-x64.exe`) and Linux x64 (`monefa-miner-1.1.0-linux-x64`)
- Connects to the official node pool: `ws://monefa.net:3030`
- Flags: `--url`, `--address`, `--threads`, `--cpu`

---

## Older versions

Network versions v1.x–v2.0 (2026-08/09) delivered the initial chain, P2P sync,
web wallet, explorer, mining pool with referral payouts, Telegram bot, browser
extension and Monefa Pay. Details are included in each release's notes.
