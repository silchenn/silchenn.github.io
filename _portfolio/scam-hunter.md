---
title: "Scam Hunter: Scam Link, Wallet & Fake-Job-Ad Detection"
excerpt: "A defensive toolkit against Southeast-Asia scam patterns — one detection core that scores suspicious URLs, phone numbers, USDT (TRON) wallets and fake 'high-salary' job ads, served through a CLI, a Telegram bot and a web page."
collection: portfolio
order: 1
redirect_from:
  - /portfolio/antiscam-toolkit/
---

> **Status note:** This is a beginner-level, in-progress practice project. The detection core, CLI, Telegram bot and web UI all run and are covered by a pytest suite (48 tests). It is **not deployed** to a public server and has no real users yet. The job-ad classifier has only been evaluated on a small **synthetic** dataset — see "Honest limits" below.
>
> **AI-assisted:** this project was built with AI assistance — AI coding assistants were used throughout development.

**Objective:** Turn the scam patterns people around me actually run into — fake exchange links, unknown overseas callers, "send USDT to this address", and "high-salary customer service job in Cambodia, flights included" recruitment ads — into explainable, repeatable checks. Every risk score comes with the reasons behind it, so a non-technical user can see *why* something was flagged.

### Architecture
One shared detection core, three front-ends. Entities are extracted from a message once, each checker scores its own type, and the analyzer merges the results:

```
user message ──> extract.py ──┬─> url_checker     heuristics + RDAP domain age + Safe Browsing / URLhaus
                              ├─> phone_checker   region, number range, VoIP
                              ├─> wallet_checker  TRON Base58Check + USDT blacklist + address age
                              └─> job_detector    trilingual red-flag rules + TF-IDF classifier
                                         │
                           analyzer.py ──> formatter.py ──> bot.py / cli.py / web (FastAPI)
```

Each target gets a 0–100 score: **≥60 high risk, 25–59 suspicious, <25 nothing obvious found**.

### What the checks do
* **URLs:** brand impersonation (domain contains `binance`, `okx`, `metamask`, `vietcombank`… but isn't the official domain), including typosquats like `binanse` and digit-for-letter swaps like `0kx`; newly registered domains via **RDAP** (under 30 days weighs heavily); structural signals (abused TLDs such as `.top/.xyz/.vip`, raw-IP hosts, punycode, direct `.apk` downloads, shorteners); optional **Google Safe Browsing** and **URLhaus** threat-intel lookups.
* **Phone numbers:** flags Cambodia / Myanmar / Laos numbers *in the context of unsolicited contact* (the message says so explicitly — a local number is not itself a scam), plus VoIP and Chinese virtual-operator ranges.
* **USDT (TRON) wallets:** Base58Check validation, then an on-chain call to the USDT contract's `isBlackListed` to see whether Tether has frozen the address, plus address creation time. A frozen address is a very strong signal.
* **Fake job ads:** red-flag rules in Chinese, English and Vietnamese, each signal category counted once. High pay alone scores nothing — only "high pay + zero requirements / vague role" does, so legitimate overseas tech jobs aren't caught. The heaviest weights go to "contract signed on arrival" and "passports held by the company", which are strong human-trafficking indicators. A TF-IDF classifier runs alongside the rules.

### Honest limits
* The classifier's ~92% 5-fold CV accuracy is on **63 samples I synthesized myself** from public reporting on scam-compound recruitment. Synthetic data is cleaner than reality; real-world performance will be worse. On the same set, the rules put 29/30 scam ads in high risk and none of the 33 normal ads.
* To fix that, I built a real-data pipeline: every sample is tagged `synthetic` or `real`, `cli.py job-review` labels candidate ads interactively, and `cli.py train` reports **real-sample-only, out-of-fold metrics separately** once both classes have real examples — so the synthetic number can't be mistaken for production accuracy. Collecting real samples is the next step.
* Rules can be evaded (homophones, image-only ads); OCR is a possible extension.
* Every online lookup fails soft: if a network call or API errors out, the result says "lookup failed" instead of breaking the analysis.

### Safety & privacy decisions
* Defensive detection only — no "scam-baiting" or attacking scam infrastructure.
* User reports go to a review queue (`reports.jsonl`), never straight into the blocklist, so the report feature can't be abused to blacklist legitimate sites or numbers.
* Message text isn't logged; reporter IDs and IPs are stored only as hashes. The web endpoints (and the bot) are rate-limited per user/IP so it can't be used as a free bulk-lookup proxy that burns threat-intel API quota.

### Tech Stack
* **Core:** Python, `scikit-learn` (TF-IDF + classifier), RDAP, Google Safe Browsing API, URLhaus API, TRON / USDT contract calls
* **Interfaces:** CLI, Telegram bot (`python-telegram-bot`), FastAPI web UI with a self-contained static page
* **Quality:** pytest suite (48 tests), git-tracked
* **Development:** AI-assisted (AI coding assistants used throughout)
