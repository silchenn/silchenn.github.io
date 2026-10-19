---
layout: archive
title: ""
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Summary
======
Entry-level security analyst focused on detection engineering and open-source intelligence (OSINT), with a growing foundation in offensive security. Based in Southeast Asia, I'm motivated by the scam and fraud ecosystem I see around me, and built [Scam Hunter](/portfolio/scam-hunter/) to flag the fake links, crypto wallets and human-trafficking job ads common in the region. Also hands-on with real malware C2 traffic analysis and Python-based detection tooling. Background in data pipelines and analytics from a supply-chain automation internship at Adidas. Currently preparing for the CCNA. Bilingual in English and Mandarin.

Education
======
* **B.A.**, University of Michigan (Ann Arbor)

Cybersecurity Learning Plan
======
* **Foundations:** preparing for **CCNA** (OSI/TCP-IP, subnetting, routing/switching) — main current focus, not yet passed; Linux fundamentals in hands-on practice.
* **Detection Engineering / OSINT (hands-on):** malware traffic analysis / C2 detection and threat-intel / scam-indicator enrichment — see **Hands-On Evidence** below. Real, git-tracked tools; next steps are real-sample data for the anti-scam classifier, written OSINT investigations, and a Sigma-rule layer.
* **Offensive Security (apprentice):** OWASP Top 10, TryHackMe/HackTheBox rooms and CTFs on authorized targets, building toward documented write-ups and an entry offensive cert (eJPT/PNPT), with OSCP as the mid-term goal.
* **Baseline cert:** CompTIA Security+ (shared by both tracks), after CCNA.


Hands-On Evidence
======
* **[Malware Traffic Analysis](/portfolio/malware-traffic-analysis/) — C2 beacon & fan-out detection:** Parsed real C2 malware pcaps (NetSupport RAT, FormBook) with Python/scapy into structured flow data, then wrote statistically robust (median/CV-based) beacon and fan-out detection scripts — validated against real infection samples, git-tracked with each fix documented. The most concrete cybersecurity evidence on this CV so far. Honest label: active, in-progress practice, not finished expertise.
* **[Scam Hunter](/portfolio/scam-hunter/) — scam link, wallet & fake-job-ad detection:** One Python detection core scoring URLs (brand-impersonation/typosquat heuristics, RDAP domain age, URLhaus, Google Safe Browsing), phone numbers, and TRON USDT wallets (Base58Check + on-chain Tether blacklist), plus a trilingual (zh/en/vi) rule + TF-IDF detector for scam-compound recruitment ads; served via CLI, Telegram bot and FastAPI web UI, 48 pytest tests. Honest label: beginner-level practice project, not deployed; classifier evaluated only on a small self-built synthetic set (real-sample evaluation pipeline built, real data still being collected).
* **Adidas (Logistics Automation Specialist, Intern):** Built a live Power Automate + Power BI pipeline replacing a manual, error-prone Excel workflow across supplier/factory/logistics teams — real delivery inside an enterprise environment.
* **Product-building background:** Shipped end-to-end software (web PWA and native iOS) using AI-assisted development — kept as personal projects going forward, not resume-line evidence for the cybersecurity pivot.
* **Languages:** Native bilingual (Mandarin Chinese / English).


