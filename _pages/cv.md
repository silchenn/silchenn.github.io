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
Making a deliberate, full pivot into cybersecurity, exploring three tracks in parallel to determine the right fit before committing (decision checkpoint ~2026-11): **Detection Engineering / Blue Team** (where hands-on work has already started — see below), **Cloud Security**, and **Red Team / offensive security**. Prior background is end-to-end product building — real, shipped software, not mockups — which now serves as evidence of execution ability rather than as the professional identity itself.

Education
======
* **B.A.**, University of Michigan (Ann Arbor)

Cybersecurity Learning Plan
======
* **Foundations:** preparing for **CCNA** (OSI/TCP-IP, subnetting, routing/switching) — main current focus, not yet passed; Linux fundamentals in hands-on practice.
* **Detection Engineering / Blue Team (hands-on, ahead of the others):** malware traffic analysis / C2 detection and scam-indicator enrichment — see **Hands-On Evidence** below. Real, validated, git-tracked scripts; next steps are a Sigma-rule layer and a demoable alerting pipeline.
* **Cloud Security (exploring):** AWS/Azure security fundamentals, IAM, cloud posture auditing — practice vehicle is **CloudGuard**, a personal lab project (spec-stage; not yet a claimed skill). Cloud foundations cert is the first milestone.
* **Red Team (exploring):** OWASP Top 10, TryHackMe/HackTheBox rooms, CompTIA Security+ as a baseline.


Hands-On Evidence
======
* **[Malware Traffic Analysis](/portfolio/malware-traffic-analysis/) — C2 beacon & fan-out detection:** Parsed real C2 malware pcaps (NetSupport RAT, FormBook) with Python/scapy into structured flow data, then wrote statistically robust (median/CV-based) beacon and fan-out detection scripts — validated against real infection samples, git-tracked with each fix documented. The most concrete cybersecurity evidence on this CV so far. Honest label: active, in-progress practice, not finished expertise.
* **[antiscam-toolkit](/portfolio/antiscam-toolkit/) — scam link, wallet & fake-job-ad detection:** One Python detection core scoring URLs (brand-impersonation/typosquat heuristics, RDAP domain age, URLhaus, Google Safe Browsing), phone numbers, and TRON USDT wallets (Base58Check + on-chain Tether blacklist), plus a trilingual (zh/en/vi) rule + TF-IDF detector for scam-compound recruitment ads; served via CLI, Telegram bot and FastAPI web UI, 48 pytest tests. Honest label: beginner-level practice project, not deployed; classifier evaluated only on a small self-built synthetic set (real-sample evaluation pipeline built, real data still being collected).
* **Adidas (Logistics Automation Specialist, Intern):** Built a live Power Automate + Power BI pipeline replacing a manual, error-prone Excel workflow across supplier/factory/logistics teams — real delivery inside an enterprise environment.
* **Product-building background:** Shipped end-to-end software (web PWA and native iOS) using AI-assisted development — kept as personal projects going forward, not resume-line evidence for the cybersecurity pivot.
* **Languages:** Native bilingual (Mandarin Chinese / English).

Service and leadership
======
* **Creative Society Advocate:** Exploring the intersection of technology and media through the **CiP (Contents Innovation Program)** framework.

