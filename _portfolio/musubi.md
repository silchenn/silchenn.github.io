---
title: "Project MUSUBI: Reconstructing Subjective Truth through AIGC"
excerpt: "A generative media pilot (The DreamX Factory) using Midjourney to transform fleeting dreams and childhood memories into a secure digital heritage."
collection: portfolio
order: 4
---

<style>
  /* -------------------------------------------------- */
  /* Immersive Pitch-Black Cinema Theme Overrides      */
  /* -------------------------------------------------- */
  body, 
  #main, 
  .page, 
  .page__content, 
  .archive, 
  .wrapper, 
  footer, 
  .masthead, 
  .breadcrumbs, 
  .greedy-nav,
  .navigation-wrapper {
    background-color: #000000 !important;
    background: #000000 !important;
    color: #eeeeee !important;
    border-color: rgba(255, 255, 255, 0.08) !important;
  }
  
  /* Sidebar adjustments */
  .sidebar, 
  .author__profile, 
  .nav__list,
  .sidebar.sticky {
    background-color: #000000 !important;
    background: #000000 !important;
    border-color: rgba(255, 255, 255, 0.08) !important;
    color: #dddddd !important;
  }
  
  /* Link adjustments to make them white/light on black */
  .sidebar a, 
  .author__urls a,
  .greedy-nav a,
  .masthead__menu-item a,
  .breadcrumbs a {
    color: #bbbbbb !important;
    text-shadow: none !important;
  }
  .sidebar a:hover, 
  .author__urls a:hover,
  .greedy-nav a:hover,
  .masthead__menu-item a:hover,
  .breadcrumbs a:hover {
    color: #ffffff !important;
  }
  
  /* Typographic hierarchy light-up */
  h1, h2, h3, h4, h5, h6, 
  .page__title, 
  .archive__item-title,
  .author__name,
  .author__bio {
    color: #ffffff !important;
  }
  
  /* Subtle styling for rules, buttons, and blocks */
  hr {
    border-color: rgba(255, 255, 255, 0.08) !important;
  }
  
  .page__content blockquote {
    border-left: 4px solid rgba(255, 255, 255, 0.25) !important;
    background: rgba(255, 255, 255, 0.03) !important;
    color: #cccccc !important;
  }

  .musubi-section-title {
    border-bottom: 2px solid rgba(255, 255, 255, 0.1);
    padding-bottom: 8px;
    margin-top: 40px;
    font-size: 1.5rem;
    font-weight: 600;
  }
  
  /* Infinite Wall Marquee Section */
  .musubi-marquee-section {
    width: 100vw;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
    overflow: hidden;
    padding: 30px 0;
    display: flex;
    flex-direction: column;
    gap: 25px;
    background: rgba(10, 10, 10, 0.25);
    backdrop-filter: blur(8px);
  }
  
  .musubi-marquee-track {
    display: flex;
    overflow: hidden;
    user-select: none;
    gap: 20px;
    width: 100%;
  }
  
  .musubi-marquee-group {
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: space-around;
    gap: 20px;
    min-width: 100%;
  }
  
  /* Track movements */
  .scroll-left .musubi-marquee-group {
    animation: scroll-l 32s linear infinite;
  }
  .scroll-right .musubi-marquee-group {
    animation: scroll-r 35s linear infinite;
  }
  
  /* Pause entire track on hover so visitors can select any card easily */
  .musubi-marquee-track:hover .musubi-marquee-group {
    animation-play-state: paused;
  }
  
  @keyframes scroll-l {
    0% { transform: translateX(0); }
    100% { transform: translateX(-100%); }
  }
  @keyframes scroll-r {
    0% { transform: translateX(-100%); }
    100% { transform: translateX(0); }
  }
  
  /* Hover Marquee Cards (Vertical Poster Style) */
  .musubi-card {
    position: relative;
    width: 320px; /* Fixed width for uniform scrolling wall */
    height: 460px; /* Fixed vertical poster height */
    background: rgba(255, 255, 255, 0.02);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 16px;
    overflow: hidden;
    transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
    backdrop-filter: blur(12px);
    flex-shrink: 0;
  }
  
  .musubi-card:hover {
    transform: scale(1.04);
    border-color: rgba(255, 255, 255, 0.35);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.45);
    z-index: 10; /* Stack on top when hovered */
  }
  
  .musubi-media-container {
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 1;
    overflow: hidden;
    background: #000;
  }
  
  .musubi-media-container img {
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    object-fit: cover;
    z-index: 2;
    opacity: 1;
    transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1), filter 0.6s ease;
  }
  
  .musubi-media-container video {
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    object-fit: cover;
    z-index: 1;
    opacity: 0; /* Hidden by default when image cover exists */
    transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1), opacity 0.6s ease, filter 0.6s ease;
  }
  
  /* Zoom & darken background on hover to make text extremely legible */
  .musubi-card:hover .musubi-media-container img {
    transform: scale(1.08);
    filter: brightness(0.35) blur(2px);
  }
  .musubi-card:hover .musubi-media-container video {
    opacity: 1;
    z-index: 4;
    transform: scale(1.08);
    filter: brightness(0.35) blur(2px);
  }
  
  /* For video-only cards (no static image) */
  .musubi-media-container.video-only-container video {
    opacity: 1;
    z-index: 2;
    filter: brightness(0.8) contrast(0.95);
  }
  .musubi-card:hover .musubi-media-container.video-only-container video {
    filter: brightness(0.35) blur(2px);
  }
  
  /* Sliding Overlay Information Block */
  .musubi-info {
    position: absolute;
    bottom: 0; left: 0;
    width: 100%; height: 100%;
    padding: 24px;
    z-index: 6;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    box-sizing: border-box;
    background: linear-gradient(to top, rgba(0, 0, 0, 0.85) 0%, rgba(0, 0, 0, 0.4) 60%, transparent 100%);
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.4s cubic-bezier(0.16, 1, 0.3, 1), transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
    pointer-events: none;
  }
  
  .musubi-card:hover .musubi-info {
    opacity: 1;
    transform: translateY(0);
  }
  
  .musubi-title {
    font-size: 1.2rem;
    font-weight: 700;
    color: #fff;
    margin: 0 0 8px 0;
    border-bottom: none;
    padding-bottom: 0;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
  }
  
  .musubi-desc {
    font-size: 0.82rem;
    color: rgba(255, 255, 255, 0.85);
    line-height: 1.5;
    margin: 0;
    text-shadow: 0 1px 2px rgba(0, 0, 0, 0.5);
  }
  
  .musubi-tag {
    align-self: flex-start;
    padding: 3px 8px;
    background: rgba(255, 255, 255, 0.12);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 4px;
    font-size: 0.68rem;
    color: #fff;
    margin-top: 14px;
    font-family: monospace;
    backdrop-filter: blur(4px);
  }
</style>

**Objective:** To demonstrate the power of AI as a "Vessel for the Soul"—transforming intangible, subjective memories into tangible, high-fidelity media that can be preserved for generations.

### The "Media" Hook: Emotional Resonance
Project MUSUBI focuses on the **"DreamX Factory"** pilot. I collaborated with my cousin to capture the "light and temperature" of her childhood memories—a realm where traditional photography cannot reach. By using AIGC, we moved from "Objective Capturing" to **"Subjective Reconstruction."**

### AI Orchestration: The Methodology
This project is not about "one-click generation." It is a rigorous exercise in **AI Orchestration**:
*   **Narrative Ingestion:** Mapping the emotional nuances and visual fragments of the memory.
*   **Iterative Prompt Engineering:** Using Midjourney with custom descriptors to match the specific "haze" and "nostalgia" of 1990s/2000s childhood aesthetics.
*   **Verification:** A loop-back system where the user provides feedback on the "emotional accuracy" of the generated frames until the subjective truth is achieved.

<h3 class="musubi-section-title">Visual Gallery: The Complete MUSUBI Anthology</h3>
*Below is the complete curated showcase of our pilot study titled "The Geometry of Nostalgia" presented as an infinite digital art wall. We reconstructed recurring dream fragments through iterative AI orchestration. Hover over the wall to freeze the scroll; hover over any item to reveal its details, prompts, and motion layers.*

<div class="musubi-marquee-section">
  <!-- Track 1: Scrolls Left -->
  <div class="musubi-marquee-track scroll-left">
    <div class="musubi-marquee-group">

      <!-- Card 2 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-1.png" alt="The Sentinel">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Sentinel</h4>
          <p class="musubi-desc">Visualizing the overwhelming presence of a colossal monument towering over a silent city, capturing the feelings of vulnerability in childhood nightmares.</p>
          <span class="musubi-tag">Aesthetic: Low-Key / Scale</span>
        </div>
      </div>
      <!-- Card 3 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-4.png" alt="The Echo at the Station">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Echo at the Station</h4>
          <p class="musubi-desc">Capturing the isolation of a single glowing billboard in a rainy, forgotten terminal, focusing on the texture of wet asphalt, soft focus, and ambient light leaks.</p>
          <span class="musubi-tag">Aesthetic: Rainy / Low-light</span>
        </div>
      </div>
      <!-- Card 8 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/犬女.jpg" alt="The Canine Daughter">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Canine Daughter</h4>
          <p class="musubi-desc">Reconstructing a memory of a loyal childhood companion. The portrait blends traditional Asian atmospheric painting with soft lighting, depicting the silent, spiritual dialogue between a young child and her canine sentinel.</p>
          <span class="musubi-tag">Aesthetic: Traditional Haze / Emotional</span>
        </div>
      </div>
      <!-- Card 10 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/大慈大悲麻将厅.png" alt="The Mahjong Hall of Infinite Mercy">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Mahjong Hall of Infinite Mercy</h4>
          <p class="musubi-desc">Reconstructing the lively haze of an old neighborhood parlor where elder relatives played, blending spiritual mercy symbols with the clicking of tiles under bright fluorescent tubes.</p>
          <span class="musubi-tag">Aesthetic: Nostalgic Parlor / Spiritual Realism</span>
        </div>
      </div>
      <!-- Card 12 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/放生.png" alt="The Rite of Release">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Rite of Release</h4>
          <p class="musubi-desc">A dreamscape portraying the ritual release of captive goldfishes into a misty, glowing mountain lake, evoking themes of letting go and personal transcendence.</p>
          <span class="musubi-tag">Aesthetic: Mystical Fog / Rite</span>
        </div>
      </div>
      <!-- Card 14 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/游戏人生.png" alt="Playing with Fate">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">Playing with Fate</h4>
          <p class="musubi-desc">Visualizing childhood afternoons spent in retro arcade rooms, where glowing CRT screens cast vibrant shadows on young faces, blending virtual play with reality.</p>
          <span class="musubi-tag">Aesthetic: Retro Arcade / Cyberpunk Warmth</span>
        </div>
      </div>
      <!-- Card 16 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/离别.jpeg" alt="The Departure">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Departure</h4>
          <p class="musubi-desc">Capturing the quiet, melancholic sunset at a long-distance bus station, representing the emotional weight of childhood goodbyes and endless roads.</p>
          <span class="musubi-tag">Aesthetic: Golden Hour / Melancholy</span>
        </div>
      </div>
      <!-- Card 18 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/阴影.png" alt="The Looming Shadow">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Looming Shadow</h4>
          <p class="musubi-desc">Exploring the psychological landscape of childhood fears—a towering, silent shadow stretching across a narrow bedroom wall under moonlight.</p>
          <span class="musubi-tag">Aesthetic: High-Contrast Chiaroscuro / Scale</span>
        </div>
      </div>
    </div>
    
    <!-- Cloned Group for Seamless Loop -->
    <div class="musubi-marquee-group" aria-hidden="true">

      <!-- Card 2 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-1.png" alt="The Sentinel">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Sentinel</h4>
          <p class="musubi-desc">Visualizing the overwhelming presence of a colossal monument towering over a silent city, capturing the feelings of vulnerability in childhood nightmares.</p>
          <span class="musubi-tag">Aesthetic: Low-Key / Scale</span>
        </div>
      </div>
      <!-- Card 3 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-4.png" alt="The Echo at the Station">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Echo at the Station</h4>
          <p class="musubi-desc">Capturing the isolation of a single glowing billboard in a rainy, forgotten terminal, focusing on the texture of wet asphalt, soft focus, and ambient light leaks.</p>
          <span class="musubi-tag">Aesthetic: Rainy / Low-light</span>
        </div>
      </div>
      <!-- Card 8 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/犬女.jpg" alt="The Canine Daughter">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Canine Daughter</h4>
          <p class="musubi-desc">Reconstructing a memory of a loyal childhood companion. The portrait blends traditional Asian atmospheric painting with soft lighting, depicting the silent, spiritual dialogue between a young child and her canine sentinel.</p>
          <span class="musubi-tag">Aesthetic: Traditional Haze / Emotional</span>
        </div>
      </div>
      <!-- Card 10 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/大慈大悲麻将厅.png" alt="The Mahjong Hall of Infinite Mercy">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Mahjong Hall of Infinite Mercy</h4>
          <p class="musubi-desc">Reconstructing the lively haze of an old neighborhood parlor where elder relatives played, blending spiritual mercy symbols with the clicking of tiles under bright fluorescent tubes.</p>
          <span class="musubi-tag">Aesthetic: Nostalgic Parlor / Spiritual Realism</span>
        </div>
      </div>
      <!-- Card 12 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/放生.png" alt="The Rite of Release">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Rite of Release</h4>
          <p class="musubi-desc">A dreamscape portraying the ritual release of captive goldfishes into a misty, glowing mountain lake, evoking themes of letting go and personal transcendence.</p>
          <span class="musubi-tag">Aesthetic: Mystical Fog / Rite</span>
        </div>
      </div>
      <!-- Card 14 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/游戏人生.png" alt="Playing with Fate">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">Playing with Fate</h4>
          <p class="musubi-desc">Visualizing childhood afternoons spent in retro arcade rooms, where glowing CRT screens cast vibrant shadows on young faces, blending virtual play with reality.</p>
          <span class="musubi-tag">Aesthetic: Retro Arcade / Cyberpunk Warmth</span>
        </div>
      </div>
      <!-- Card 16 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/离别.jpeg" alt="The Departure">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Departure</h4>
          <p class="musubi-desc">Capturing the quiet, melancholic sunset at a long-distance bus station, representing the emotional weight of childhood goodbyes and endless roads.</p>
          <span class="musubi-tag">Aesthetic: Golden Hour / Melancholy</span>
        </div>
      </div>
      <!-- Card 18 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/阴影.png" alt="The Looming Shadow">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Looming Shadow</h4>
          <p class="musubi-desc">Exploring the psychological landscape of childhood fears—a towering, silent shadow stretching across a narrow bedroom wall under moonlight.</p>
          <span class="musubi-tag">Aesthetic: High-Contrast Chiaroscuro / Scale</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Track 2: Scrolls Right -->
  <div class="musubi-marquee-track scroll-right">
    <div class="musubi-marquee-group">
      <!-- Card 4 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-5.jpg" alt="The Courtyard Goldfish Cover">
          <video autoplay loop muted playsinline>
            <source src="/images/musubi/musubi-5.mp4" type="video/mp4">
          </video>
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Courtyard Goldfish (Motion)</h4>
          <p class="musubi-desc">A giant plastic goldfish bag floats above drying laundry lines in a residential courtyard. Hover to trigger the motion loop, highlighting swaying water and glowing orange fish against a hot summer sky.</p>
          <span class="musubi-tag">Aesthetic: VHS Loop / Summer</span>
        </div>
      </div>
      <!-- Card 5 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-2.png" alt="The Melancholy Recital">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Melancholy Recital</h4>
          <p class="musubi-desc">A surrealist dreamscape where nature and obsolete technology merge: a TV-headed pianist performing under a bleeding celestial flower.</p>
          <span class="musubi-tag">Aesthetic: Surreal / Metaphor</span>
        </div>
      </div>
      <!-- Card 9 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/銀翼.png" alt="The Silver Wings">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Silver Wings</h4>
          <p class="musubi-desc">An evocative science-fiction dreamscape where mechanical wings catch the cold light of high altitude. Recreating the childhood fascination with flight and majestic clockwork structures.</p>
          <span class="musubi-tag">Aesthetic: Cybernetic / High-Contrast Metallic</span>
        </div>
      </div>
      <!-- Card 6 -->
      <div class="musubi-card">
        <div class="musubi-media-container video-only-container">
          <video autoplay loop muted playsinline class="video-only">
            <source src="/images/musubi/musubi-6.mp4" type="video/mp4">
          </video>
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Riverbank Ritual (Motion)</h4>
          <p class="musubi-desc">Traditional folding fans float in a perfect circular arrangement above dark, quiet river steps at dusk. Recreating the humid air and green-jade hues of an old memory.</p>
          <span class="musubi-tag">Aesthetic: Jade-Gold / Riverbank</span>
        </div>
      </div>
      <!-- Card 7 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-7.png" alt="The Moonlit Courtyard">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Moonlit Courtyard</h4>
          <p class="musubi-desc">A cold, moonlit ancient courtyard with paper lanterns casting a faint warm glow. Inspired by classical ghost stories (Liaozhai), capturing a tranquil yet eerie emptiness.</p>
          <span class="musubi-tag">Aesthetic: Liaozhai / Monochrome</span>
        </div>
      </div>
      <!-- Card 11 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/大鱼.png" alt="The Great Leviathan">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Great Leviathan</h4>
          <p class="musubi-desc">Recreating a recurring childhood dream of a giant, ancient celestial fish swimming silently above the tiled roofs of residential alleyways during a sudden summer shower.</p>
          <span class="musubi-tag">Aesthetic: Celestial Leviathan / Dreamscape</span>
        </div>
      </div>
      <!-- Card 13 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/梦中人.png" alt="The Dreamweaver">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Dreamweaver</h4>
          <p class="musubi-desc">Depicting a silent, glowing figure waiting on a foggy platform, symbolizing the personification of memories that we only meet in our sleep.</p>
          <span class="musubi-tag">Aesthetic: Ethereal Portrait / Low-Light</span>
        </div>
      </div>
      <!-- Card 15 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/游戏人生2.png" alt="Playing with Fate: Part II">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">Playing with Fate: Part II</h4>
          <p class="musubi-desc">The continuation of virtual journeys, focusing on the mechanical beauty of analog joysticks and a child's deep immersion into pixelated dream worlds.</p>
          <span class="musubi-tag">Aesthetic: CRT Nostalgia / Analog Tech</span>
        </div>
      </div>
      <!-- Card 17 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/自渡.png" alt="Self-Salvation">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">Self-Salvation</h4>
          <p class="musubi-desc">A deep, introspective scene of a single figure rowing a boat across a dark, starry sea towards a distant lighthouse, exploring themes of growth and self-crossing.</p>
          <span class="musubi-tag">Aesthetic: Starry Void / Introspective</span>
        </div>
      </div>
      <!-- Card 19 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/鱼怪.png" alt="Fish Spirit">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Sea Spirit</h4>
          <p class="musubi-desc">Reconstructing folklore-inspired nightmares of a benign, multi-eyed river spirit rising from dark waters, blending childhood curiosity with ancient myths.</p>
          <span class="musubi-tag">Aesthetic: Folk Horror / Jade Dark</span>
        </div>
      </div>
    </div>
    
    <!-- Cloned Group for Seamless Loop -->
    <div class="musubi-marquee-group" aria-hidden="true">
      <!-- Card 4 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-5.jpg" alt="The Courtyard Goldfish Cover">
          <video autoplay loop muted playsinline>
            <source src="/images/musubi/musubi-5.mp4" type="video/mp4">
          </video>
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Courtyard Goldfish (Motion)</h4>
          <p class="musubi-desc">A giant plastic goldfish bag floats above drying laundry lines in a residential courtyard. Hover to trigger the motion loop, highlighting swaying water and glowing orange fish against a hot summer sky.</p>
          <span class="musubi-tag">Aesthetic: VHS Loop / Summer</span>
        </div>
      </div>
      <!-- Card 5 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-2.png" alt="The Melancholy Recital">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Melancholy Recital</h4>
          <p class="musubi-desc">A surrealist dreamscape where nature and obsolete technology merge: a TV-headed pianist performing under a bleeding celestial flower.</p>
          <span class="musubi-tag">Aesthetic: Surreal / Metaphor</span>
        </div>
      </div>
      <!-- Card 9 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/銀翼.png" alt="The Silver Wings">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Silver Wings</h4>
          <p class="musubi-desc">An evocative science-fiction dreamscape where mechanical wings catch the cold light of high altitude. Recreating the childhood fascination with flight and majestic clockwork structures.</p>
          <span class="musubi-tag">Aesthetic: Cybernetic / High-Contrast Metallic</span>
        </div>
      </div>
      <!-- Card 6 -->
      <div class="musubi-card">
        <div class="musubi-media-container video-only-container">
          <video autoplay loop muted playsinline class="video-only">
            <source src="/images/musubi/musubi-6.mp4" type="video/mp4">
          </video>
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Riverbank Ritual (Motion)</h4>
          <p class="musubi-desc">Traditional folding fans float in a perfect circular arrangement above dark, quiet river steps at dusk. Recreating the humid air and green-jade hues of an old memory.</p>
          <span class="musubi-tag">Aesthetic: Jade-Gold / Riverbank</span>
        </div>
      </div>
      <!-- Card 7 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/musubi-7.png" alt="The Moonlit Courtyard">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Moonlit Courtyard</h4>
          <p class="musubi-desc">A cold, moonlit ancient courtyard with paper lanterns casting a faint warm glow. Inspired by classical ghost stories (Liaozhai), capturing a tranquil yet eerie emptiness.</p>
          <span class="musubi-tag">Aesthetic: Liaozhai / Monochrome</span>
        </div>
      </div>
      <!-- Card 11 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/大鱼.png" alt="The Great Leviathan">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Great Leviathan</h4>
          <p class="musubi-desc">Recreating a recurring childhood dream of a giant, ancient celestial fish swimming silently above the tiled roofs of residential alleyways during a sudden summer shower.</p>
          <span class="musubi-tag">Aesthetic: Celestial Leviathan / Dreamscape</span>
        </div>
      </div>
      <!-- Card 13 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/梦中人.png" alt="The Dreamweaver">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Dreamweaver</h4>
          <p class="musubi-desc">Depicting a silent, glowing figure waiting on a foggy platform, symbolizing the personification of memories that we only meet in our sleep.</p>
          <span class="musubi-tag">Aesthetic: Ethereal Portrait / Low-Light</span>
        </div>
      </div>
      <!-- Card 15 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/游戏人生2.png" alt="Playing with Fate: Part II">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">Playing with Fate: Part II</h4>
          <p class="musubi-desc">The continuation of virtual journeys, focusing on the mechanical beauty of analog joysticks and a child's deep immersion into pixelated dream worlds.</p>
          <span class="musubi-tag">Aesthetic: CRT Nostalgia / Analog Tech</span>
        </div>
      </div>
      <!-- Card 17 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/自渡.png" alt="Self-Salvation">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">Self-Salvation</h4>
          <p class="musubi-desc">A deep, introspective scene of a single figure rowing a boat across a dark, starry sea towards a distant lighthouse, exploring themes of growth and self-crossing.</p>
          <span class="musubi-tag">Aesthetic: Starry Void / Introspective</span>
        </div>
      </div>
      <!-- Card 19 -->
      <div class="musubi-card">
        <div class="musubi-media-container">
          <img src="/images/musubi/鱼怪.png" alt="The Sea Spirit">
        </div>
        <div class="musubi-info">
          <h4 class="musubi-title">The Sea Spirit</h4>
          <p class="musubi-desc">Reconstructing folklore-inspired nightmares of a benign, multi-eyed river spirit rising from dark waters, blending childhood curiosity with ancient myths.</p>
          <span class="musubi-tag">Aesthetic: Folk Horror / Jade Dark</span>
        </div>
      </div>
    </div>
  </div>
</div>

### The Future: From Art to Asset
Project MUSUBI is the foundation for a 2060 vision where these memories are protected by the **Immutable Persona Protocol (IPP)** and managed within a **Digital Legacy Trust**. It proves that technology can navigate and soothe the human heart while creating long-term cultural value.

---
**Tech/Tools:** Midjourney (v6), Runway Gen-2 (for motion loops), Prompt Engineering, Adobe Photoshop (Post-processing), Secure Data Vaulting logic.

