---
title: "Vela: Visual Intrusion Detection for the Home Network"
excerpt: "A 3D view of home-network traffic — hosts as stars, connections as light lanes — fed by a Python/Scapy capture backend that aggregates flows, names peers via DNS / TLS SNI / ASN, and pushes them over an authenticated WebSocket. ATT&CK-mapped detection rules are designed; the detection engine is next."
collection: portfolio
order: 2
---

🔗 **Live Demo (simulated data):** [https://silchenn.github.io/vela/](https://silchenn.github.io/vela/) · **Source:** [github.com/silchenn/vela](https://github.com/silchenn/vela)

> **Status note:** This is an early, in-progress practice project. The visualization (simulated and live modes) and the capture backend are built and running; the **detection engine is not built yet** — the rules below are designed and documented, not implemented. Capture currently covers only the machine it runs on, not the whole home network.
>
> **AI-assisted:** this project was built with AI assistance — AI coding assistants were used throughout development.

**Why I started it:** Vela began as a study aid for my CCNA preparation. Instead of only reading about the TCP/IP model, DNS, TCP/UDP, ports and how packets actually move between hosts, I wanted to watch those concepts happen on my own network — every connection, protocol and lookup made visible — so I could build a real feel for what network traffic looks like.

**Objective:** From there the goal grew: make a home network's traffic something you can *watch* — and, more importantly, make every red lane on screen trace back to a detection rule with a stated principle, a justified threshold and an explainable false-positive story. The visuals are the hook; the detection logic is the point.

### What it shows
* **Stars:** the router, this machine, LAN devices, cloud servers and everyday internet services.
* **Lanes:** connections between IPs; the speed and density of the light trails follow the transfer rate.
* **Colors:** HTTPS cyan · HTTP white · DNS violet · QUIC amber · alerts red.
* Two visual styles (Star Lanes and Cyberpunk), with simulated drills — big download, 4K video, DNS storm, port scan, NAS outage, DDoS — and click-to-follow on any node.

### Architecture
```
en0 capture (Scapy) ──> PacketEvent ──> aggregator (200 ms windows) ──> flow / node messages ──> WebSocket ──> Three.js frontend
                                              │
                                  peer naming: DNS answers > TLS SNI > offline ASN database
```
* **Flow aggregation:** packets are rolled into flows keyed by (this machine, peer, transport, service port) and pushed every 200 ms — never packet-by-packet — so the frontend stays smooth.
* **Peer naming:** external IPs are labelled from captured DNS answers first, then the TLS ClientHello SNI (with split-segment reassembly), then an offline IP→ASN database, so "142.250.x.x" shows up as a named service.
* **Live mode:** the same frontend switches from simulated to real traffic by connecting to the backend's WebSocket.

### Detection rules (designed, not yet implemented)
Each rule in `docs/DETECTIONS.md` follows one template — principle → decision logic → initial threshold → false-positive sources → how to verify — and is mapped to MITRE ATT&CK:

| Rule | ATT&CK |
|---|---|
| Port scan | T1046 Network Service Discovery |
| New device | T1200 Hardware Additions |
| Threat-intel hit (FireHOL, abuse.ch) | per intel category |
| C2 beaconing | T1071 Application Layer Protocol |
| DNS tunneling | T1071.004 DNS |
| Data exfiltration | T1048 / T1041 |

C2 beaconing reuses the approach from my [Malware Traffic Analysis](/portfolio/malware-traffic-analysis/) project. A candidate "direct-to-IP connection" rule (outbound connections with no prior DNS lookup and no SNI) is also written up, including the warm-up period it needs to avoid false positives at startup.

### Security & privacy decisions
* The WebSocket binds only to LAN or loopback addresses (`0.0.0.0` and public addresses are refused) and requires a token; a wrong token gets HTTP 401. This service sees every connection in the house, so it must never be internet-facing.
* Only packet headers, DNS answers and the TLS ClientHello server name are read — payloads are never parsed or stored.
* Intended only for networks you own or are authorized to monitor; scans and attack drills run only in your own lab.

### Honest limits
* No detection engine yet — today it visualizes traffic; it doesn't alert on real traffic.
* Local-interface capture sees only this machine's traffic. Whole-home visibility needs gateway capture (conntrack on an OpenWrt / Linux gateway), which is planned.
* Scapy is fine for a prototype but too slow for production capture.
* The online demo runs on simulated data; live mode only works from a locally opened page, since an HTTPS page can't connect to a LAN `ws://` address.

### Tech Stack
* **Backend:** Python, Scapy, WebSockets, offline IP→ASN database (iptoasn)
* **Frontend:** Three.js single-file prototypes, deployed via GitHub Pages / GitHub Actions
* **Quality:** unittest suite (15 tests, aggregation and node naming), git-tracked, MIT licensed
* **Development:** AI-assisted (AI coding assistants used throughout)
