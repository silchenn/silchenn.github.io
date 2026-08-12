---
title: "KYOU (今日): Cyber-Electronic Generative Art & Digital Ritual PWA"
excerpt: "A 0-to-1 AI-assisted generative art PWA translating ancient GanZhi time coordinates into a daily glowing Cyber-Electronic (赛博电子) mosaic ritual. Showcasing 0-1 product design, electronic Chinese aesthetic curation, and full-stack AI-assisted engineering."
collection: portfolio
order: 1
header:
  teaser: "kyou/hero_demo.png"
---

🔗 **Live Demo:** [https://ink-kappa.vercel.app/](https://ink-kappa.vercel.app/)

**KYOU** (今日, *Today*) is a mobile-first, daily generative art Progressive Web App (PWA) that translates cosmological time coordinates (GanZhi, Five Elements) into a shared, deterministic Cyber-Electronic (赛博电子 / 电子中式) digital signal ritual.

Designed and engineered from scratch (0-to-1) using AI-assisted pair programming, KYOU reimagines traditional calendar systems into a bold, high-contrast digital neon experience for a modern audience.

---

## 🎨 Visual Artifact Showcase

### 1. Daily Energy Mosaic Hero (每日能量场主视觉)
The central visual engine calculates the daily Heavenly Stems and Earthly Branches (e.g., *Ren-Yin* 壬寅) and renders an interactive, 160-column mosaic electric grid field with glowing pixelated GanZhi glyphs on a fixed pitch-black canvas (`#120f1c`).

### 2. Mobile Digital Share Card (移动端艺术分享卡)
Users can export a high-resolution, seed-based share card containing deterministic daily mosaic artwork, glowing neon GanZhi glyphs, current Shichen coordinates, and non-predictive poetic reflection, integrated with native Web Share API (`drawShareCard`) for frictionless mobile sharing.

---

## 🚀 Key Capabilities Highlighted

### 1. 0-to-1 Product Development & Vision (从零到一开发与产品定义)
* **Product Constitution ("Show, Don't Predict"):** Positioned against traditional fortune-telling/divination apps that exploit user anxiety. KYOU presents time as an entry point for daily presence and mindful digital contemplation.
* **Agile Pivot & Brand Iteration:** Rapidly evolved the product identity from an initial "quiet monochrome ink" prototype into a bold **"Cyber-Electronic" (赛博电子 / 电子中式)** digital neon signal (*kyou*), embracing high saturation, bloom glow, and low-res pixelation while enforcing strict "Single Visual Hero" discipline (removing UI chrome, dashboard controls, and fake status text).
* **End-to-End Delivery:** Managed the complete product lifecycle: product vision $\rightarrow$ mathematical time coordinate translation $\rightarrow$ custom WebGL/Canvas 2D particle engine $\rightarrow$ PWA distribution $\rightarrow$ social share virality loop.

### 2. Design Excellence & Cyber-Electronic Aesthetics (赛博电子视觉设计与审美落地)
* **Five Elements Peking-Opera Neon Palette:** Spec'd a custom color theory mapping Five Elements to ultra-saturated neon hues with blown-out white-hot cores set against a pitch-black canvas:
  * 🌿 **Wood (木):** Emerald Green (`#12c76a`) · Pulse upward motion
  * 🔥 **Fire (火):** Vermilion Red (`#ff3b30`) · High-exposure blown-out core
  * 🌾 **Earth (土):** Amber Gold (`#ffb020`) · Low-frequency flickering
  * ⚔️ **Metal (金):** Cyan Silver (`#2fd0e6`) · Sharply converging highlight
  * 🌊 **Water (水):** Royal Blue (`#2979ff`) · Low-frequency wave circulation
* **Mathematical Generative Domain Allocator:** Five Elements relationships (比和/相生/相克) govern the spatial allocation of the day's Stem and Branch colors across the mosaic grid—same elements create unified fields, generating elements produce soft probability gradients, and controlling elements enforce steep domain dominance.
* **Micro-Interactions & Hourly Lighting:** Twelve Shichen time coordinates (子丑寅卯辰巳午未申酉戌亥) inject subtle accent flickering into the particle field without overriding the primary day identity.

### 3. AI-Assisted Engineering & System Architecture (AI 辅助全栈工程与性能调优)
* **Modular Architecture with LLM Pair-Programming:** Partnered with Claude/AI to split complex single-file prototypes into clean ES6 modules (`data.js`, `elements.js`, `electric-field.js`, `shichen.js`, `share-card.js`, `main.js`).
* **Algorithmic Performance Optimization:** Diagnosed a severe 60fps rendering bottleneck caused by thousands of per-cell `ctx.shadowBlur` invocations. Refactored the particle render loop into an offscreen-canvas Gaussian blur layer (`drawGlow`), slashing GPU/CPU frame times by **90%+** while preserving glowing neon bloom.
* **Automated Daily Pipeline & Offline PWA:** Integrated `lunar-javascript` into an automated daily node script (`scripts/generate-daily.js`) with time-zone enforcement (`Asia/Ho_Chi_Minh`), paired with Service Worker caching for instant offline PWA loading.

---

## 🛠️ System Architecture

1. **Data Layer (`lunar-javascript`):** Ingests daily astronomical & Ganzhi coordinates into daily JSON data drops (`data/today.json`).
2. **Translation Engine (`elements.js`):** Maps Stems & Branches 五行 relationships (generating/overcoming) into neon color palettes, particle density, and flow velocity.
3. **Canvas Hero Engine (`electric-field.js`):** Renders the real-time 160-column mosaic electric field with offscreen blur compositing.
4. **Export & Social Layer (`share-card.js`):** Generates high-res image cards (`drawShareCard`) using seed-based RNG (`rand()`) for native Web Share API export.

---

## 💻 Tech Stack

* **Core:** Vanilla JavaScript (ES6+), HTML5 Canvas 2D, Vanilla CSS (Design Tokens)
* **Libraries & PWA:** `lunar-javascript`, PWA Service Workers, Web Share API
* **Engineering Tools:** AI Pair Programming (Claude / Cursor), Node.js Build Runner

