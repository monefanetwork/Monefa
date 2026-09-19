<div align="center">

# ⛓️ Monefa Network

### Finance Without Borders

**Monefa (XMF)** is a privacy-focused blockchain network built natively in **TypeScript** — a full implementation of the **CryptoNote** protocol (the architecture behind Monero), with ring-signature transactions, one-time stealth addresses, CPU-friendly Proof-of-Work, a mining pool, web wallet, desktop wallet, Telegram bot and block explorer — all running on the live mainnet at [monefa.net](https://monefa.net).

[![Website](https://img.shields.io/badge/🌐_Website-monefa.net-F26822?style=for-the-badge)](https://monefa.net)
[![Telegram Bot](https://img.shields.io/badge/🤖_Telegram-Monefanet__bot-26A5E4?style=for-the-badge)](https://t.me/Monefanet_bot)
[![Downloads](https://img.shields.io/badge/⬇️_Releases-Latest_Builds-10B981?style=for-the-badge)](../../releases)
[![Changelog](https://img.shields.io/badge/📜_Updates-CHANGELOG-8B5CF6?style=for-the-badge)](CHANGELOG.md)

[![Core](https://img.shields.io/badge/Core-TypeScript-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Consensus](https://img.shields.io/badge/PoW-CryptoNight--Lite--Fa-2EA043)](#%EF%B8%8F-coin-specifications)
[![Privacy](https://img.shields.io/badge/Privacy-Stealth_+_LSAG-F26822)](#-privacy-technology)

</div>

---

## 📖 What is Monefa?

Monefa is a complete, self-hosted privacy blockchain stack. Every layer — the keccak-based hashing, the memory-hard PoW, the elliptic-curve stealth-address math and the LSAG ring signatures — is implemented from scratch in TypeScript and runs on the [Bun](https://bun.sh) runtime. The network is live and anyone can use it right now:

- **Send and receive XMF** privately — no visible amounts, no visible addresses, unlinkable one-time payments
- **Mine on any CPU** — through the browser, the desktop wallet, or the official standalone miner
- **Accept payments** — public payment links with QR invoices via Monefa Pay
- **Track the chain** — live explorer with blocks, transactions, mempool and network stats

> ⚠️ **Disclaimer** — Monefa is an independent community implementation of the CryptoNote architecture. It is *not* affiliated with, endorsed by, or connected to Monero (XMR) or the Monero Project. Use at your own risk; a professional security audit is recommended before any serious financial use.

## 💿 Get a Wallet — no installation from source needed

| Wallet | Platform | Get it |
|---|---|---|
| 🖥️ **GUI Wallet v1.1.0** | Windows 10/11 (portable) | [Download → Releases](../../releases/tag/gui-wallet-v1.1.0) · [monefa.net/downloads](https://monefa.net/downloads) |
| 🖥️ **GUI Wallet v1.1.0** | Linux x86_64 (AppImage) | [Download → Releases](../../releases/tag/gui-wallet-v1.1.0) · [monefa.net/downloads](https://monefa.net/downloads) |
| 🌐 **Web wallet** | Any browser | [monefa.net](https://monefa.net) |
| 🤖 **Telegram bot + Mini App** | Telegram (mobile/desktop) | [@Monefanet_bot](https://t.me/Monefanet_bot) |
| 🧩 **Browser extension** | Chrome / Firefox | [monefa.net/downloads](https://monefa.net/downloads) |
| ⛏️ **CLI Miner (standalone binary)** | Windows · Linux x64 | [Download → Releases](../../releases/tag/miner-v1.1.0) |
| 📱 **Android Wallet v1.0.0** (native Kotlin, no WebView) | Android 7.0+ | [Download → Releases](../../releases/tag/wallet-android-v1.0.2) · [monefa.net/downloads](https://monefa.net/downloads) |

## ⛏️ Mining — four easy ways

**1. Official CLI miner (standalone binary — no source, no runtime needed):**

```bash
# Linux x64                       # Windows x64 (PowerShell)
./monefa-miner-1.1.0-linux-x64 \  .\monefa-miner-1.1.0-win-x64.exe `
  --url ws://monefa.net:3030 \    --url ws://monefa.net:3030 `
  --address 4YOUR_XMF_ADDRESS \   --address 4YOUR_XMF_ADDRESS `
  --threads 8                     --threads 8
```

**2. Desktop GUI Wallet** — built-in Mining page: pool or solo, per-thread control, live hashrate and accepted shares.

**3. Browser mining** — open [monefa.net](https://monefa.net) and opt in (never auto-starts).

**4. Android wallet — two modes** — mine directly **on the phone's CPU** through the official pool (opt-in, foreground service, never auto-starts), or remotely start/pause/stop mining on **your own node or server** with live hashrate, shares and block feed.

Pool payouts support a 3-level referral network (L1 5% / L2 2% / L3 1%).

## 🌐 Public Node

The official node accepts miner connections and exposes a public read API:

```
Miner stratum : ws://monefa.net:3030
GET /api/node/info        → height, supply, mined, peers, hashrate
GET /api/node/blocks      → recent blocks
GET /api/node/tx/{hash}   → transaction detail (incl. mempool)
GET /api/node/pool/stats  → mining pool statistics
```

## 🔒 Privacy Technology

1. **Stealth addresses** — every payment goes to a one-time address `P = Hs(r·A)·G + B`; only your view key can detect your incoming outputs.
2. **LSAG ring signatures** — each spender signs within a ring of decoy keys (default ring size 3), making the true spender computationally unidentifiable.
3. **Key images** — spent outputs publish a unique `I = Hs(P)·x`, preventing double-spends without revealing which output was spent.

Wallet keys are encrypted with AES-256-GCM; the view key remains exportable for audits (View Key button in the bot / wallet).

## 🪙 Coin Specifications

| Parameter | Value |
|---|---|
| **Name / Ticker** | Monefa / **XMF** |
| **Consensus** | Proof-of-Work — CryptoNight-Lite-Fa (keccak-512 + 128 KB memory-hard scratchpad) |
| **Block time** | ~15 seconds target, automatic difficulty retarget |
| **Total supply** | 2⁶⁴−1 lepton ≈ **18.45 M XMF**, decreasing block reward |
| **Privacy** | Stealth addresses + LSAG ring signatures + key images |
| **Output lock** | 5 blocks |
| **Seed format** | 16-word mnemonic (Persian wordlist) |
| **Native units** | 1 XMF = 10⁸ lepton |

## 📜 Updates & Changelog

All official builds and their change notes are published on the [**Releases**](../../releases) page and summarized in [CHANGELOG.md](CHANGELOG.md).

Latest highlights:

- **Network v2.1.0** — Telegram Mini App rebuilt (auth fixed, mining, payments, 5 languages), math captcha restored, persistent merchant payment links, bot explorer rewritten, auto-mining on boot removed
- **Android Wallet v1.0.2** — native Kotlin wallet (no WebView): real on-device CPU mining (opt-in) + remote mining control, balance, stealth transfers, receive QR, 16-word seed, explorer, math captcha, 5 languages with RTL, PIN lock + encrypted storage
- **GUI Wallet v1.1.0** — built-in pool/solo CPU mining, 9 languages with RTL, math captcha, monero-gui style UX
- **CLI Miner v1.1.0** — standalone Windows/Linux binaries connecting to the official pool

## 🔐 Source Code Notice

The Monefa codebase is **proprietary**. The source code is **not** distributed or hosted on GitHub — this repository exists to provide:

- official **binary releases** (wallets, miner) with verified change notes,
- **documentation** for users and pool miners,
- a public **issue tracker** for bug reports and feature requests.

Redistribution of unmodified official binaries is permitted; copying, re-licensing or redistribution of the source code is not. See [LICENSE](LICENSE).

## 🤝 Feedback

Found a bug or have an idea? Open an [issue](../../issues) or reach the team via [monefa.net](https://monefa.net) / [@Monefanet_bot](https://t.me/Monefanet_bot).

---

<div dir="rtl">

## 📖 مونفا چیست؟ (فارسی)

**مونفا (XMF)** یک شبکه بلاکچین حریم‌خصوصی کامل بر پایه معماری **CryptoNote** است که از صفر با TypeScript پیاده‌سازی شده — با تراکنش‌های ناشناس حلقه‌ای، آدرس‌های استلث یک‌بارمصرف، ماینینگ CPU، استخر، کیف پول وب و دسکتاپ، بات تلگرام و اکسپلورر زنده روی شبکه اصلی [monefa.net](https://monefa.net).

| روش استفاده | لینک |
|---|---|
| 🌐 کیف پول وب | [monefa.net](https://monefa.net) |
| 📱 کیف پول اندروید (ناتیو کاتلین، بدون WebView) | اندروید ۷+ · [Releases](../../releases/tag/wallet-android-v1.0.2) یا [monefa.net/downloads](https://monefa.net/downloads) |
| 🖥️ کیف پول دسکتاپ (ویندوز/لینوکس) | [Releases](../../releases/tag/gui-wallet-v1.1.0) یا [monefa.net/downloads](https://monefa.net/downloads) |
| 🤖 بات و Mini App تلگرام | [@Monefanet_bot](https://t.me/Monefanet_bot) |
| 🧩 افزونه مرورگر | [monefa.net/downloads](https://monefa.net/downloads) |
| ⛏️ ماینر CLI (باینری آماده) | [Releases](../../releases/tag/miner-v1.1.0) |

**ماینینگ با باینری آماده (بدون نیاز به نصب):**
```bash
./monefa-miner-1.1.0-linux-x64 --url ws://monefa.net:3030 --address 4... --threads 8
```

**مشخصات سکه:** نماد XMF · PoW حافظه‌مقاوم CryptoNight-Lite-Fa · بلاک ~۱۵ ثانیه · عرضه ≈ ۱۸٫۴۵ میلیون · سید ۱۶ کلمه‌ای · قفل خروجی ۵ بلاک

**آخرین آپدیت‌ها:** کیف پول اندروید v1.0.0 (اپ بومی کاتلین بدون WebView، کنترل ماینینگ ابری روی نود خودتان، ۵ زبان با RTL) · نسخه شبکه v2.1.0 (بازسازی Mini App تلگرام، کپچای ریاضی، لینک‌های پرداخت ماندگار، بازنویسی اکسپلورر بات) · کیف پول دسکتاپ v1.1.0 (ماینینگ داخلی استخر/سولو، ۹ زبان با RTL) · ماینر CLI v1.1.0 (باینری مستقل ویندوز/لینوکس)

### 🔐 اطلاعیه سورس کد

سورس‌کد مونفا **متن‌باز نیست** و در گیت‌هاب منتشر نمی‌شود. این ریپو فقط برای ارائه **باینری‌های رسمی**، **مستندات استفاده**، **ثبت تغییرات (آپدیت‌ها)** و **پیگیری مشکل** است. توزیع باینری‌های رسمی بدون تغییر مجاز است؛ کپی یا بازنشر سورس‌کد مجاز نیست. جزئیات در [LICENSE](LICENSE).

> ⚠️ سلب مسئولیت: این پروژه پیاده‌سازی مستقل آموزشی/اجتماعی از معماری CryptoNote است و به پروژه مونرو وابستگی ندارد. پیش از استفاده مالی جدی، ممیزی امنیتی حرفه‌ای لازم است.

</div>
