[Jordan Rivas.html](https://github.com/user-attachments/files/34035385/Jordan.Rivas.html)
<!doctype html><html><head><meta charset=utf8><meta name=viewport content="width=device-width,initial-scale=1,viewport-fit=cover"><style>:root{color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}html{scroll-padding-top:env(safe-area-inset-top,0px)}body{margin:0;padding:0;font:14px -apple-system,BlinkMacSystemFont,sans-serif;background:#fff;color:#000}img{max-width:100%}[hidden]:not([hidden=until-found i]){display:none!important}</style></head><body>
<title>Jordan Rivas</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@600;700;800&family=IBM+Plex+Mono:wght@400;500&family=Work+Sans:wght@400;500;600&display=swap">
<style>
  /*
    Layout concept: the whole page sits on a black cutting mat. A fine
    measuring grid fills the ground, a ruler strip runs along the top edge,
    and squares on the grid light up in the accent colors under the pointer.
    A centered marquee name wobbles forever, a tight strip of pill filters
    sits right under it, and a mosaic of differently sized project images
    floats over the grid (title and medium live inside each image). A clicked
    project morphs into a centered card with a picture carousel. Contact and
    bio are centered at the foot, with a pair of eyes that watch the pointer.
    Committed single dark theme (deliberate choice: lighting and production
    work reads best on black), with one vivid accent per medium.
  */
  :root {
    color-scheme: dark;
    --bg: #000000;
    --surface: #101010;
    --surface-raised: #161616;
    --line: rgba(245, 241, 232, 0.16);
    --line-soft: rgba(245, 241, 232, 0.08);
    --grid-minor: rgba(245, 241, 232, 0.055);
    --grid-major: rgba(245, 241, 232, 0.12);
    --tick: rgba(245, 241, 232, 0.28);
    --tick-strong: rgba(245, 241, 232, 0.5);
    --text: #f5f1e8;
    --text-dim: rgba(245, 241, 232, 0.72);
    --text-faint: rgba(245, 241, 232, 0.56);
    --accent: #ccff33;
    --ink-on-vivid: #0b0a06;

    --font-display: "Big Shoulders Display", "Arial Narrow", sans-serif;
    --font-body: "Work Sans", system-ui, sans-serif;
    --font-mono: "IBM Plex Mono", ui-monospace, monospace;

    --wrap: 1180px;
  }

  * { box-sizing: border-box; }

  /* Cutting mat: major lines every 120px, minor lines every 24px. */
  body {
    background-color: var(--bg);
    background-image:
      linear-gradient(var(--grid-major) 1px, transparent 1px),
      linear-gradient(90deg, var(--grid-major) 1px, transparent 1px),
      linear-gradient(var(--grid-minor) 1px, transparent 1px),
      linear-gradient(90deg, var(--grid-minor) 1px, transparent 1px);
    background-size: 120px 120px, 120px 120px, 24px 24px, 24px 24px;
    color: var(--text);
    font-family: var(--font-body);
    padding-inline: 0;
  }

  /* Lit grid squares are drawn on this canvas, under the page content. */
  #trail {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
    pointer-events: none;
  }

  .page {
    position: relative;
    z-index: 1;
  }

  .wrap {
    max-width: var(--wrap);
    margin-inline: auto;
    padding-inline: clamp(20px, 5vw, 56px);
  }

  a { color: inherit; }

  :focus-visible {
    outline: 2px solid var(--accent);
    outline-offset: 3px;
  }

  button {
    font: inherit;
    color: inherit;
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;
    text-align: left;
  }

  .sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    overflow: hidden;
    clip: rect(0 0 0 0);
    white-space: nowrap;
  }

  /* Ruler strip along the mat's top edge, ticks aligned to the grid. */
  .ruler {
    height: 16px;
    background-image:
      linear-gradient(90deg, var(--tick) 1px, transparent 1px),
      linear-gradient(90deg, var(--tick-strong) 1px, transparent 1px);
    background-size: 24px 7px, 120px 16px;
    background-position: 0 0, 0 0;
    background-repeat: repeat-x;
  }

  /* ---------- View Transitions (card to centered detail morph) ---------- */
  .detail { view-transition-name: detail-box; }
  .scrim { view-transition-name: scrim; }

  ::view-transition-group(morph-plate),
  ::view-transition-group(morph-title) {
    animation-duration: 0.55s;
    animation-timing-function: cubic-bezier(.2, .8, .2, 1);
  }
  ::view-transition-old(root),
  ::view-transition-new(root) {
    animation: none;
    mix-blend-mode: normal;
  }
  ::view-transition-new(detail-box) {
    animation: boxIn 0.45s cubic-bezier(.2, .9, .25, 1.15) both;
  }
  ::view-transition-old(detail-box) {
    animation: boxOut 0.2s ease both;
  }
  @keyframes boxIn {
    from { opacity: 0; transform: scale(0.94); }
    to   { opacity: 1; transform: scale(1); }
  }
  @keyframes boxOut {
    from { opacity: 1; transform: scale(1); }
    to   { opacity: 0; transform: scale(0.96); }
  }

  /* ---------- Topbar ---------- */
  .topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
    padding-top: clamp(12px, 2.5vw, 22px);
  }

  .mark {
    font-family: var(--font-mono);
    font-size: 0.8rem;
    letter-spacing: 0.08em;
    border: 1px solid var(--line);
    padding: 6px 10px;
    border-radius: 8px;
    background: var(--bg);
  }

  .navlinks {
    display: flex;
    gap: clamp(16px, 3vw, 32px);
    font-size: 0.95rem;
  }

  .navlinks a {
    text-decoration: none;
    border-bottom: 1px solid transparent;
    padding-bottom: 2px;
  }
  .navlinks a:hover { border-bottom-color: var(--accent); }

  /* ---------- Hero (centered) ---------- */
  .hero {
    padding-bottom: 0;
    text-align: center;
  }

  .name {
    margin: clamp(6px, 2vw, 18px) 0 0;
    font-family: var(--font-display);
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: -0.01em;
    line-height: 0.92;
    font-size: clamp(3rem, 11vw, 7.5rem);
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    column-gap: clamp(0.3em, 2vw, 0.45em);
  }

  .word { display: inline-flex; }

  /* Each letter reveals once, then rocks gently forever, offset from its neighbor. */
  .letter {
    display: inline-block;
    opacity: 0;
    color: var(--accent);
    transform-origin: 50% 85%;
    text-shadow: 0 0 28px rgba(204, 255, 51, 0);
    animation:
      spotlightReveal 0.95s cubic-bezier(.2,.75,.25,1) var(--rd, 0s) forwards,
      wobble 3.2s ease-in-out var(--wd, 1s) infinite;
  }

  @keyframes spotlightReveal {
    0% {
      opacity: 0;
      color: var(--accent);
      transform: translateY(0.12em);
      text-shadow: 0 0 0 rgba(204, 255, 51, 0);
    }
    45% {
      opacity: 1;
      color: var(--accent);
      transform: translateY(0);
      text-shadow: 0 0 30px rgba(204, 255, 51, 0.55);
    }
    100% {
      opacity: 1;
      color: var(--text);
      transform: translateY(0);
      text-shadow: 0 0 0 rgba(204, 255, 51, 0);
    }
  }

  @keyframes wobble {
    0%, 100% { transform: translateY(0) rotate(0deg); }
    20%      { transform: translateY(-0.05em) rotate(-3deg); }
    50%      { transform: translateY(0.02em) rotate(2.5deg); }
    75%      { transform: translateY(-0.03em) rotate(-1.5deg); }
  }

  @media (prefers-reduced-motion: reduce) {
    .letter {
      animation: none;
      opacity: 1;
      color: var(--text);
    }
    .detail, .scrim, .card, .card-plate, .tile, .slides, .eye { transition: none; animation: none; }
  }

  .role {
    margin: 6px auto 0;
    font-size: clamp(1.05rem, 2.2vw, 1.3rem);
    color: var(--text-dim);
    max-width: 46ch;
    text-shadow: 0 0 10px #000, 0 0 3px #000;
  }

  .marquee-rule {
    margin-top: clamp(12px, 2.2vw, 20px);
    height: 10px;
    background-image: radial-gradient(circle, var(--accent) 1.4px, transparent 1.6px);
    background-size: 20px 10px;
    background-position: center;
    opacity: 0.55;
  }

  /* ---------- Filters ---------- */
  .filters-section {
    padding-block: clamp(10px, 1.8vw, 16px);
  }

  .filters-row {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
  }

  .filter-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tag {
    --tag-color: var(--accent);
    font-family: var(--font-mono);
    font-size: 0.85rem;
    padding: 7px 15px;
    border: 1px solid var(--line);
    border-radius: 999px;
    color: var(--text-dim);
    background: var(--bg);
    transition: background-color 0.15s ease, color 0.15s ease, border-color 0.15s ease;
  }

  .tag:hover { border-color: var(--tag-color); color: var(--text); }

  .tag[aria-pressed="true"] {
    background: var(--tag-color);
    border-color: var(--tag-color);
    color: var(--ink-on-vivid);
  }

  .count {
    font-family: var(--font-mono);
    font-size: 0.85rem;
    color: var(--text-faint);
    white-space: nowrap;
    text-shadow: 0 0 10px #000, 0 0 3px #000;
  }

  /* ---------- Gallery: mosaic of differently sized images floating over the grid ---------- */
  .gallery-section { padding-block: 4px clamp(24px, 4vw, 40px); }

  /*
    One grid cell is a square (--u). Tiles span whole cells, so a tile's shape
    is set by its column and row span, and the shapes scale with the page.
  */
  .gallery {
    --gap: clamp(12px, 1.8vw, 20px);
    --cols: 12;
    --content: calc(min(100vw, 1180px) - 2 * clamp(20px, 5vw, 56px));
    --u: calc((var(--content) - (var(--cols) - 1) * var(--gap)) / var(--cols));
    display: grid;
    grid-template-columns: repeat(var(--cols), minmax(0, 1fr));
    grid-auto-rows: var(--u);
    grid-auto-flow: dense;
    gap: var(--gap);
  }

  .k1 { --c: 6; --r: 6; }
  .k2 { --c: 3; --r: 3; }
  .k3 { --c: 6; --r: 3; }
  .k4 { --c: 3; --r: 5; }
  .k5 { --c: 4; --r: 5; }
  .k6 { --c: 4; --r: 5; }
  .k7 { --c: 6; --r: 5; }

  @media (max-width: 699px) {
    .gallery { --cols: 6; }
    .k5 { --c: 3; --r: 4; }
    .k6 { --c: 6; --r: 4; }
  }

  .tile {
    position: relative;
    grid-column: span var(--c);
    grid-row: span var(--r);
    min-width: 0;
    transition:
      opacity 0.7s ease var(--delay, 0s),
      translate 0.8s cubic-bezier(.2, .8, .2, 1) var(--delay, 0s);
  }

  /* Hidden until scrolled into view (set by script only when it can reveal them). */
  .tile.pre {
    opacity: 0;
    translate: 0 42px;
  }

  .card {
    position: absolute;
    inset: 0;
    display: block;
    border-radius: 22px;
    transition: transform 0.2s ease;
  }

  .card:hover { transform: translateY(-4px); }

  .card-plate {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    padding: 12px;
    overflow: hidden;
    border-radius: 22px;
    background:
      radial-gradient(circle at var(--hx, 22%) var(--hy, 14%), rgba(255, 255, 255, 0.4), transparent 55%),
      linear-gradient(var(--ang, 145deg), var(--cat-color), color-mix(in srgb, var(--cat-color) 50%, #000));
    box-shadow: 0 16px 30px -22px color-mix(in srgb, var(--cat-color) 40%, transparent);
    transition: box-shadow 0.2s ease;
  }

  /* Darkens the lower part of the image so the title stays readable. */
  .card-plate::after {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(0, 0, 0, 0.62), rgba(0, 0, 0, 0) 52%);
    pointer-events: none;
  }

  .card:hover .card-plate {
    box-shadow: 0 22px 38px -22px color-mix(in srgb, var(--cat-color) 55%, transparent);
  }

  .tile-img {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .chip {
    position: relative;
    z-index: 1;
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 4px 10px;
    border-radius: 999px;
    background: rgba(0, 0, 0, 0.5);
    color: #fff;
    font-family: var(--font-mono);
    font-size: 0.68rem;
    line-height: 1.3;
    -webkit-backdrop-filter: blur(6px);
    backdrop-filter: blur(6px);
  }
  .chip-dim { color: rgba(255, 255, 255, 0.74); }

  .card-title {
    position: relative;
    z-index: 1;
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 1rem;
    line-height: 1.1;
    letter-spacing: 0.01em;
    color: #fff;
    text-shadow: 0 1px 8px rgba(0, 0, 0, 0.55);
  }

  .k1 .card-title, .k7 .card-title { font-size: 1.5rem; }
  .k3 .card-title, .k5 .card-title, .k6 .card-title { font-size: 1.2rem; }

  /* ---------- Detail card (centered) ---------- */
  .scrim {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.72);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.25s ease;
    z-index: 10;
  }
  .scrim.is-open { opacity: 1; pointer-events: auto; }

  .detail {
    position: fixed;
    inset: 0;
    margin: auto;
    z-index: 11;
    width: min(560px, calc(100% - 32px));
    height: fit-content;
    max-height: calc(100% - 32px);
    overflow-y: auto;
    background: var(--surface-raised);
    border: 1px solid var(--line-soft);
    border-radius: 26px;
    box-shadow: 0 30px 80px -40px color-mix(in srgb, var(--cat-color, #ffffff) 40%, transparent);
    opacity: 0;
    transform: scale(0.94);
    transition: opacity 0.2s ease, transform 0.3s cubic-bezier(.2, .9, .25, 1.15);
  }
  .detail.is-open { opacity: 1; transform: none; }

  /* While a view transition runs, the open/closed state must change instantly. */
  .detail.vt, .scrim.vt { transition: none; }

  .detail-inner {
    position: relative;
    padding: 18px 18px 26px;
  }

  .detail-close {
    position: absolute;
    top: 32px;
    right: 32px;
    z-index: 3;
    width: 36px;
    height: 36px;
    display: grid;
    place-items: center;
    border-radius: 50%;
    background: rgba(0, 0, 0, 0.55);
    color: #fff;
    -webkit-backdrop-filter: blur(6px);
    backdrop-filter: blur(6px);
  }
  .detail-close:hover { background: rgba(0, 0, 0, 0.78); }

  /* Carousel */
  .detail-plate {
    position: relative;
    aspect-ratio: 16 / 10;
    border-radius: 18px;
    overflow: hidden;
    touch-action: pan-y;
    background: var(--surface);
  }

  .slides {
    display: flex;
    height: 100%;
    transition: transform 0.45s cubic-bezier(.2, .8, .2, 1);
  }

  .slide {
    position: relative;
    flex: 0 0 100%;
    height: 100%;
    background:
      radial-gradient(circle at var(--hx, 22%) var(--hy, 14%), rgba(255, 255, 255, 0.4), transparent 55%),
      linear-gradient(var(--ang, 145deg), var(--cat-color, #888), color-mix(in srgb, var(--cat-color, #888) 50%, #000));
  }

  .slide img {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    user-select: none;
    -webkit-user-drag: none;
  }

  .detail-chip {
    position: absolute;
    top: 14px;
    left: 14px;
    z-index: 2;
  }

  .nav {
    position: absolute;
    top: 50%;
    translate: 0 -50%;
    z-index: 2;
    width: 40px;
    height: 40px;
    display: grid;
    place-items: center;
    border-radius: 50%;
    background: rgba(0, 0, 0, 0.5);
    color: #fff;
    -webkit-backdrop-filter: blur(6px);
    backdrop-filter: blur(6px);
    transition: background-color 0.15s ease;
  }
  .nav:hover { background: rgba(0, 0, 0, 0.75); }
  .nav-prev { left: 10px; }
  .nav-next { right: 10px; }

  .dots {
    position: absolute;
    left: 50%;
    bottom: 8px;
    translate: -50% 0;
    z-index: 2;
    display: flex;
    padding: 2px 6px;
    border-radius: 999px;
    background: rgba(0, 0, 0, 0.4);
  }

  .dot {
    width: 22px;
    height: 22px;
    display: grid;
    place-items: center;
  }
  .dot::before {
    content: "";
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.5);
    transition: background-color 0.2s ease, transform 0.2s ease;
  }
  .dot[aria-current="true"]::before {
    background: #fff;
    transform: scale(1.25);
  }

  .detail-title {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: clamp(1.8rem, 5vw, 2.4rem);
    margin: 20px 4px 0;
    line-height: 1.05;
  }

  .detail-meta {
    margin: 18px 4px 0;
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 8px 16px;
    font-size: 0.92rem;
  }
  .detail-meta dt {
    font-family: var(--font-mono);
    color: var(--text-faint);
  }
  .detail-meta dd { margin: 0; color: var(--text); }

  .detail-desc {
    margin: 20px 4px 0;
    color: var(--text-dim);
    line-height: 1.65;
    font-size: 0.98rem;
  }

  /* ---------- Contact (with bio), centered ---------- */
  .contact-section {
    border-top: 1px solid var(--line);
    padding-block: clamp(28px, 5vw, 44px) clamp(12px, 2vw, 20px);
    text-align: center;
  }

  .contact-heading {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: clamp(1.8rem, 5vw, 2.6rem);
    text-transform: uppercase;
    margin: 0 0 12px;
  }

  .contact-bio {
    margin: 0 auto 28px;
    max-width: 60ch;
    color: var(--text-dim);
    line-height: 1.65;
    font-size: 1rem;
    text-shadow: 0 0 10px #000, 0 0 3px #000;
  }

  .contact-grid {
    max-width: 900px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 18px 32px;
  }

  .contact-row dt {
    font-family: var(--font-mono);
    font-size: 0.8rem;
    color: var(--text-faint);
    margin-bottom: 4px;
  }
  .contact-row dd {
    margin: 0;
    font-size: 1.05rem;
  }

  .note {
    margin: 22px 0 0;
    font-size: 0.9rem;
    color: var(--text-faint);
  }

  /* ---------- Eyes that watch the pointer ---------- */
  .eyes {
    display: flex;
    justify-content: center;
    gap: 14px;
    padding-block: 12px 24px;
  }

  .eye {
    position: relative;
    width: 68px;
    height: 68px;
    display: grid;
    place-items: center;
    overflow: hidden;
    border-radius: 50%;
    background: var(--text);
    box-shadow: inset 0 -8px 14px rgba(0, 0, 0, 0.18), 0 0 0 1px rgba(255, 255, 255, 0.1);
    animation: blink 6s infinite;
  }

  @keyframes blink {
    0%, 92%, 100% { transform: scaleY(1); }
    95%           { transform: scaleY(0.1); }
  }

  .iris {
    position: relative;
    width: 34px;
    height: 34px;
    border-radius: 50%;
    background: radial-gradient(circle, #0b0a06 0 30%, var(--accent) 32% 100%);
    transform: translate(var(--ox, 0px), var(--oy, 0px));
  }
  .iris::after {
    content: "";
    position: absolute;
    top: 6px;
    left: 7px;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: #fff;
    opacity: 0.9;
  }

  footer.site-footer {
    padding-block: 16px;
    border-top: 1px solid var(--line);
    font-family: var(--font-mono);
    font-size: 0.78rem;
    color: var(--text-faint);
    display: flex;
    justify-content: center;
    text-align: center;
    flex-wrap: wrap;
    gap: 6px 24px;
  }

  [hidden] { display: none !important; }
</style>

<canvas id="trail" aria-hidden="true"></canvas>

<div class="page">
  <div class="ruler" aria-hidden="true"></div>

  <header class="topbar wrap">
    <span class="mark">JR</span>
    <nav class="navlinks">
      <a href="#work">Work</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <section class="hero wrap" id="top">
      <h1 class="name" aria-label="Jordan Rivas">
        <span class="word" id="nameFirst" aria-hidden="true"></span>
        <span class="word" id="nameLast" aria-hidden="true"></span>
      </h1>
      <p class="role">Director of photography &amp; multidisciplinary visual artist</p>
      <div class="marquee-rule" aria-hidden="true"></div>
    </section>

    <section class="filters-section" id="work">
      <div class="wrap filters-row">
        <div class="filter-tags" id="filterTags" role="group" aria-label="Filter projects by category"></div>
        <p class="count" id="resultCount" aria-live="polite"></p>
      </div>
    </section>

    <section class="gallery-section wrap">
      <div class="gallery" id="gallery"></div>
    </section>
  </main>

  <div class="scrim" id="scrim" hidden></div>
  <aside class="detail" id="detail" role="dialog" aria-modal="true" aria-labelledby="detailTitle" hidden>
    <div class="detail-inner">
      <button class="detail-close" id="detailClose" type="button" aria-label="Close project details">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round">
          <line x1="2" y1="2" x2="14" y2="14"/>
          <line x1="14" y1="2" x2="2" y2="14"/>
        </svg>
      </button>

      <div class="detail-plate" id="detailPlate" role="group" aria-roledescription="carousel" aria-label="Project pictures">
        <div class="slides" id="slides"></div>
        <span class="detail-chip" id="detailChip"></span>
        <button class="nav nav-prev" id="slidePrev" type="button" aria-label="Previous picture">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="11,3 5,9 11,15"/></svg>
        </button>
        <button class="nav nav-next" id="slideNext" type="button" aria-label="Next picture">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="7,3 13,9 7,15"/></svg>
        </button>
        <div class="dots" id="slideDots"></div>
        <span class="sr-only" id="slideStatus" aria-live="polite"></span>
      </div>

      <h2 class="detail-title" id="detailTitle"></h2>
      <dl class="detail-meta" id="detailMeta"></dl>
      <p class="detail-desc" id="detailDesc"></p>
    </div>
  </aside>

  <section class="contact-section wrap" id="contact">
    <h2 class="contact-heading">Contact</h2>
    <p class="contact-bio">Placeholder bio. Working across film, live events, theater, and photography, with a focus on practical light and unfussy coverage. Swap this paragraph for your own.</p>
    <dl class="contact-grid">
      <div class="contact-row">
        <dt>Email</dt>
        <dd>hello@jordanrivas.com</dd>
      </div>
      <div class="contact-row">
        <dt>Instagram</dt>
        <dd>@jordanrivas</dd>
      </div>
      <div class="contact-row">
        <dt>Based in</dt>
        <dd>Los Angeles, CA</dd>
      </div>
      <div class="contact-row">
        <dt>Reel / resume</dt>
        <dd>Link on request</dd>
      </div>
    </dl>
    <p class="note">Placeholder contact details. Replace with your own before publishing.</p>
  </section>

  <div class="eyes" aria-hidden="true">
    <div class="eye"><span class="iris"></span></div>
    <div class="eye"><span class="iris"></span></div>
  </div>

  <footer class="site-footer wrap">
    <span id="year"></span>
    <span>Available for select bookings</span>
  </footer>
</div>

<script>
  // ---------------------------------------------------------------
  // WordPress integration config
  // Set this to a WordPress site URL (e.g. "https://yoursite.com")
  // once you have one, and the gallery will try to load projects
  // from its REST API (/wp-json/wp/v2/projects, falling back to
  // /wp-json/wp/v2/posts) instead of the placeholder list below.
  // Leave it blank to keep using placeholder projects.
  // ---------------------------------------------------------------
  const WP_API_BASE = "";

  // One vivid accent per medium, used for filter chips, project images, and glows.
  const CATEGORIES = {
    film:    { label: "Film",        color: "#FF4D8D" },
    live:    { label: "Live Events", color: "#00E0BF" },
    theater: { label: "Theater",     color: "#FFB020" },
    photo:   { label: "Photography", color: "#8C6BFF" }
  };
  const FALLBACK_CATEGORY = { label: "Project", color: "#6F7BFF" };

  const PLACEHOLDER_PROJECTS = [
    { id: "f1", category: "film", title: "Midnight Harvest", year: 2025, role: "Director of Photography", blurb: "A late-summer short about two sisters and a failing orchard.", description: "Shot over nine days on location, leaning on available light and a single bounce to keep the orchard scenes grounded and unforced.", credits: "Independent production" },
    { id: "f2", category: "film", title: "Low Tide", year: 2024, role: "Camera Operator", blurb: "Feature documentary following three fishing families through a single season.", description: "Handheld and run-and-gun coverage across four coastal towns, built around early mornings and long weather delays.", credits: "Commissioned by Tern Films" },
    { id: "f3", category: "film", title: "Paper Moons", year: 2024, role: "Director of Photography", blurb: "A narrative short shot entirely on practical and available light.", description: "No additional fixtures were brought to set; every scene was lit with what was already in the room or the sky.", credits: "Festival selection, regional circuit" },
    { id: "f4", category: "film", title: "The Long Weekend", year: 2023, role: "Additional Photography", blurb: "Feature film production covering second-unit and insert photography.", description: "Second-unit and insert work across a six-week shoot, matching the first unit's look on a tighter schedule.", credits: "Studio production" },
    { id: "f5", category: "film", title: "Static", year: 2023, role: "Director / DP", blurb: "Experimental short exploring analog interference as a visual language.", description: "Built around deliberately degraded video signal and re-photographed CRT playback, cut to an original score.", credits: "Self-produced" },

    { id: "le1", category: "live", title: "Lantern Festival", year: 2025, role: "Live Visuals & Projection", blurb: "Projection mapping and live visual mixing for a three-night outdoor festival.", description: "Real-time visuals mapped onto a 40-foot structure, mixed live alongside the house lighting board each night.", credits: "Produced with Lantern Collective" },
    { id: "le2", category: "live", title: "Horizon Music Festival", year: 2025, role: "Stage Photography", blurb: "Official stage and backstage photography across two weekends.", description: "Pit, stage, and backstage coverage for the full lineup, delivered same-day for the festival's press team.", credits: "Official festival photography" },
    { id: "le3", category: "live", title: "Northbound Conference", year: 2024, role: "Event Coverage", blurb: "Full-day coverage of keynotes, breakouts, and the closing reception.", description: "Single-camera coverage across three simultaneous tracks, with a same-week highlight edit for the organizers.", credits: "Commissioned event coverage" },
    { id: "le4", category: "live", title: "Harvest Moon Gala", year: 2024, role: "Live Event Direction", blurb: "On-site direction of lighting, run-of-show, and photography for a 400-guest gala.", description: "Oversaw the lighting plot and cue timing while directing a two-photographer team through the evening's program.", credits: "Private client" },
    { id: "le5", category: "live", title: "Open Air Cinema Series", year: 2023, role: "Production Photography", blurb: "Documenting a summer-long outdoor screening series across four venues.", description: "Twelve screenings across a summer, photographing setup, audience, and the screen itself at dusk.", credits: "Municipal arts program" },

    { id: "t1", category: "theater", title: "A Doll's House", year: 2025, role: "Lighting Design", blurb: "A new staging of Ibsen's drama for a 120-seat black box.", description: "A restrained plot built around four practical sources, reinforcing the play's sense of a closing room.", credits: "Riverside Theater Co." },
    { id: "t2", category: "theater", title: "The Glass Menagerie", year: 2024, role: "Production Photography", blurb: "Archival and promotional photography for a regional theater run.", description: "Dress rehearsal coverage used for both the season's archive and the production's print campaign.", credits: "Regional theater commission" },
    { id: "t3", category: "theater", title: "Midsummer, Reimagined", year: 2024, role: "Set & Lighting", blurb: "A stripped-down, promenade staging of Shakespeare's comedy.", description: "Designed a portable rig that moved with the audience through three performance spaces in one evening.", credits: "Independent ensemble" },
    { id: "t4", category: "theater", title: "Her Quiet Room", year: 2023, role: "Production Photography", blurb: "Photography for the world premiere of an original one-act play.", description: "Full technical and dress rehearsal coverage for a playwright's first produced work.", credits: "New works festival" },
    { id: "t5", category: "theater", title: "The Understudy", year: 2023, role: "Production Stills", blurb: "Stills coverage across a six-week repertory run.", description: "Weekly stills sessions tracking how the production evolved across its run, used for the company's retrospective.", credits: "Repertory company" },

    { id: "p1", category: "photo", title: "Coastal Light", year: 2025, role: "Editorial Series", blurb: "A six-image editorial series shot along the northern coastline at low light.", description: "Shot entirely within an hour of sunrise across four consecutive days, chasing a consistent fog line.", credits: "Editorial commission" },
    { id: "p2", category: "photo", title: "Portraits in Motion", year: 2024, role: "Personal Project", blurb: "A study of movement and blur in natural-light portraiture.", description: "Slow shutter speeds and window light, exploring how much motion a portrait can hold before it stops reading as one.", credits: "Self-directed" },
    { id: "p3", category: "photo", title: "After Hours", year: 2024, role: "Street Photography", blurb: "A personal series documenting a city after its shops close.", description: "A year of late-night walks through the same six blocks, returning to the same corners in different weather.", credits: "Self-directed" },
    { id: "p4", category: "photo", title: "Field Notes", year: 2023, role: "Travel Photography", blurb: "Images and observations from six weeks on the road.", description: "A working journal in photographs, shot on a single prime lens to keep the series visually consistent.", credits: "Self-directed" },
    { id: "p5", category: "photo", title: "Still Frame", year: 2023, role: "Studio Portrait Series", blurb: "A set of studio portraits built around a single hard light source.", description: "Twelve sitters, one light, one background — a deliberate constraint to focus on expression over setup.", credits: "Self-directed" }
  ];

  let projects = PLACEHOLDER_PROJECTS;
  let activeFilter = "all";
  let lastFocused = null;
  let openCard = null; // { plateEl, titleEl } of the card shown in the detail view
  let closeTimer = null;
  let slideIndex = 0;
  let slideTotal = 0;
  let revealObserver = null;
  let letterIndex = 0;

  // Tile shapes repeat in modules that fill the grid exactly (see the .k classes in the CSS).
  const TILE_PATTERN = ["k1", "k2", "k2", "k3", "k4", "k4", "k7", "k5", "k5", "k6"];

  function prefersReducedMotion() {
    return window.matchMedia("(prefers-reduced-motion: reduce)").matches;
  }

  function stripHtml(html) {
    const tmp = document.createElement("div");
    tmp.innerHTML = html || "";
    return (tmp.textContent || "").trim();
  }

  // ---------- WordPress ----------
  function guessCategory(names) {
    const t = names.join(" ").toLowerCase();
    if (/film|cinema|movie/.test(t)) return "film";
    if (/live|event|festival|concert/.test(t)) return "live";
    if (/theat|stage|play/.test(t)) return "theater";
    return "photo";
  }

  function wpToProject(post) {
    const embedded = post._embedded || {};
    const terms = [].concat(...(embedded["wp:term"] || [])).map(t => (t && t.name) || "");
    const images = [];
    const featured = embedded["wp:featuredmedia"] && embedded["wp:featuredmedia"][0];
    if (featured && featured.source_url) images.push(featured.source_url);
    const doc = new DOMParser().parseFromString((post.content && post.content.rendered) || "", "text/html");
    doc.querySelectorAll("img").forEach(img => {
      const src = img.getAttribute("src");
      if (src && /^https?:/i.test(src) && !images.includes(src)) images.push(src);
    });
    return {
      id: "wp-" + post.id,
      category: guessCategory(terms),
      title: stripHtml(post.title && post.title.rendered) || "Untitled",
      year: post.date ? new Date(post.date).getFullYear() : "",
      role: terms[0] || "From WordPress",
      blurb: stripHtml(post.excerpt && post.excerpt.rendered).slice(0, 140),
      description: stripHtml(post.content && post.content.rendered).slice(0, 400),
      credits: "Synced from WordPress",
      images
    };
  }

  async function tryLoadFromWordPress(base) {
    if (!base) return;
    const root = base.replace(/\/$/, "");
    const endpoints = ["/wp-json/wp/v2/projects?per_page=100&_embed", "/wp-json/wp/v2/posts?per_page=100&_embed"];
    for (const path of endpoints) {
      try {
        const res = await fetch(root + path, { mode: "cors" });
        if (!res.ok) continue;
        const data = await res.json();
        if (!Array.isArray(data) || data.length === 0) continue;
        projects = data.map(wpToProject);
        activeFilter = "all";
        applyFilter();
        return;
      } catch (err) {
        console.warn("WordPress fetch failed for", path, err);
      }
    }
  }

  // ---------- Name ----------
  function buildNameLetters(containerId, text) {
    const el = document.getElementById(containerId);
    text.split("").forEach((ch) => {
      const span = document.createElement("span");
      span.className = "letter";
      span.textContent = ch;
      span.style.setProperty("--rd", (letterIndex * 0.055) + "s");
      span.style.setProperty("--wd", (1 + letterIndex * 0.16) + "s");
      letterIndex++;
      el.appendChild(span);
    });
  }

  // ---------- Filters ----------
  function renderFilters() {
    const used = Array.from(new Set(projects.map(p => p.category)));
    const wrap = document.getElementById("filterTags");
    wrap.innerHTML = "";
    const makeTag = (key, label, color) => {
      const btn = document.createElement("button");
      btn.className = "tag";
      btn.type = "button";
      btn.textContent = label;
      btn.style.setProperty("--tag-color", color || "var(--accent)");
      btn.setAttribute("aria-pressed", key === activeFilter ? "true" : "false");
      btn.addEventListener("click", () => {
        activeFilter = key;
        applyFilter();
      });
      return btn;
    };
    wrap.appendChild(makeTag("all", "All", "var(--accent)"));
    used.forEach(key => {
      const cat = CATEGORIES[key] || FALLBACK_CATEGORY;
      wrap.appendChild(makeTag(key, cat.label, cat.color));
    });
  }

  // ---------- Placeholder image looks ----------
  function hashStr(s) {
    let h = 0;
    for (let i = 0; i < s.length; i++) h = (h * 31 + s.charCodeAt(i)) >>> 0;
    return h;
  }

  // A deterministic gradient angle and highlight position per project and picture.
  function applyLook(el, p, k) {
    const h = hashStr(String(p.id)) + k * 97;
    el.style.setProperty("--ang", ((h * 47) % 360) + "deg");
    el.style.setProperty("--hx", (15 + (h * 13) % 70) + "%");
    el.style.setProperty("--hy", (10 + (h * 29) % 70) + "%");
  }

  function realImages(p) {
    return Array.isArray(p.images) ? p.images : [];
  }

  function pictureCount(p) {
    const real = realImages(p).length;
    return real || 3 + (hashStr(String(p.id)) % 3);
  }

  function makeChip(cat, year) {
    const chip = document.createElement("span");
    chip.className = "chip";
    const label = document.createElement("span");
    label.textContent = cat.label;
    chip.appendChild(label);
    if (year) {
      const yr = document.createElement("span");
      yr.className = "chip-dim";
      yr.textContent = String(year);
      chip.appendChild(yr);
    }
    return chip;
  }

  // ---------- Gallery ----------
  function onReveal(entries, observer) {
    const visible = entries
      .filter(e => e.isIntersecting)
      .sort((a, b) => a.boundingClientRect.top - b.boundingClientRect.top || a.boundingClientRect.left - b.boundingClientRect.left);
    visible.forEach((entry, k) => {
      entry.target.style.setProperty("--delay", (Math.min(k, 8) * 0.07) + "s");
      entry.target.classList.remove("pre");
      observer.unobserve(entry.target);
    });
  }

  function renderGallery(list) {
    const gallery = document.getElementById("gallery");
    gallery.innerHTML = "";
    if (revealObserver) revealObserver.disconnect();
    const reveal = "IntersectionObserver" in window && !prefersReducedMotion();

    list.forEach((p, i) => {
      const cat = CATEGORIES[p.category] || FALLBACK_CATEGORY;
      const tile = document.createElement("div");
      tile.className = "tile " + TILE_PATTERN[i % TILE_PATTERN.length];
      if (reveal) tile.classList.add("pre");

      const card = document.createElement("button");
      card.className = "card";
      card.type = "button";
      card.setAttribute("aria-haspopup", "dialog");
      card.addEventListener("click", () => openDetail(p, card));

      const plate = document.createElement("span");
      plate.className = "card-plate";
      plate.style.setProperty("--cat-color", cat.color);
      applyLook(plate, p, 0);

      const real = realImages(p);
      if (real.length) {
        const img = document.createElement("img");
        img.className = "tile-img";
        img.src = real[0];
        img.alt = "";
        img.loading = "lazy";
        plate.appendChild(img);
      }

      const title = document.createElement("span");
      title.className = "card-title";
      title.textContent = p.title;

      plate.append(makeChip(cat, p.year), title);
      card.appendChild(plate);
      tile.appendChild(card);
      gallery.appendChild(tile);
    });

    if (reveal) {
      revealObserver = new IntersectionObserver(onReveal, { rootMargin: "0px 0px -6% 0px", threshold: 0.08 });
      gallery.querySelectorAll(".tile.pre").forEach(t => revealObserver.observe(t));
      // Safety net: never leave tiles near the top of the page hidden if the observer is slow.
      setTimeout(() => {
        gallery.querySelectorAll(".tile.pre").forEach(t => {
          if (t.getBoundingClientRect().top < window.innerHeight * 1.2) t.classList.remove("pre");
        });
      }, 2500);
    }

    const countEl = document.getElementById("resultCount");
    countEl.textContent = list.length + (list.length === 1 ? " project" : " projects");
  }

  function applyFilter() {
    renderFilters();
    const list = activeFilter === "all" ? projects : projects.filter(p => p.category === activeFilter);
    renderGallery(list);
  }

  // ---------- Detail card and carousel ----------
  function supportsMorph() {
    return typeof document.startViewTransition === "function" && !prefersReducedMotion();
  }

  function renderSlides(p, cat) {
    const track = document.getElementById("slides");
    const dots = document.getElementById("slideDots");
    track.innerHTML = "";
    dots.innerHTML = "";
    const real = realImages(p);
    slideTotal = pictureCount(p);

    for (let k = 0; k < slideTotal; k++) {
      const slide = document.createElement("div");
      slide.className = "slide";
      slide.style.setProperty("--cat-color", cat.color);
      applyLook(slide, p, k);
      if (real[k]) {
        const img = document.createElement("img");
        img.src = real[k];
        img.alt = p.title + ", picture " + (k + 1) + " of " + slideTotal;
        img.draggable = false;
        slide.appendChild(img);
      }
      track.appendChild(slide);

      const dot = document.createElement("button");
      dot.type = "button";
      dot.className = "dot";
      dot.setAttribute("aria-label", "Show picture " + (k + 1) + " of " + slideTotal);
      dot.addEventListener("click", () => goToSlide(k));
      dots.appendChild(dot);
    }

    const multiple = slideTotal > 1;
    document.getElementById("slidePrev").hidden = !multiple;
    document.getElementById("slideNext").hidden = !multiple;
    dots.hidden = !multiple;
    goToSlide(0, true);
  }

  function goToSlide(i, instant) {
    if (!slideTotal) return;
    slideIndex = (i + slideTotal) % slideTotal;
    const track = document.getElementById("slides");
    if (instant) track.style.transition = "none";
    track.style.transform = "translateX(" + (-100 * slideIndex) + "%)";
    if (instant) {
      void track.offsetWidth;
      track.style.transition = "";
    }
    document.querySelectorAll("#slideDots .dot").forEach((dot, k) => {
      dot.setAttribute("aria-current", k === slideIndex ? "true" : "false");
    });
    document.getElementById("slideStatus").textContent = "Picture " + (slideIndex + 1) + " of " + slideTotal;
  }

  function fillDetailContent(p, cat) {
    document.getElementById("detail").style.setProperty("--cat-color", cat.color);

    const chipSlot = document.getElementById("detailChip");
    chipSlot.innerHTML = "";
    chipSlot.appendChild(makeChip(cat, p.year));

    renderSlides(p, cat);

    document.getElementById("detailTitle").textContent = p.title;
    document.getElementById("detailDesc").textContent = p.description;

    const meta = document.getElementById("detailMeta");
    meta.innerHTML = "";
    const rows = [["Category", cat.label], ["Year", String(p.year)], ["Role", p.role], ["Credits", p.credits]];
    rows.forEach(([k, v]) => {
      const dt = document.createElement("dt");
      dt.textContent = k;
      const dd = document.createElement("dd");
      dd.textContent = v;
      meta.appendChild(dt);
      meta.appendChild(dd);
    });
  }

  function openDetail(p, triggerEl) {
    clearTimeout(closeTimer);
    lastFocused = triggerEl;
    const cat = CATEGORIES[p.category] || FALLBACK_CATEGORY;
    const detail = document.getElementById("detail");
    const scrim = document.getElementById("scrim");
    const closeBtn = document.getElementById("detailClose");
    const plateEl = triggerEl.querySelector(".card-plate");
    const titleEl = triggerEl.querySelector(".card-title");
    openCard = { plateEl, titleEl };

    if (supportsMorph() && plateEl && titleEl) {
      const detailPlate = document.getElementById("detailPlate");
      const detailTitle = document.getElementById("detailTitle");
      plateEl.style.viewTransitionName = "morph-plate";
      titleEl.style.viewTransitionName = "morph-title";
      detail.classList.add("vt");
      scrim.classList.add("vt");
      const transition = document.startViewTransition(() => {
        plateEl.style.viewTransitionName = "";
        titleEl.style.viewTransitionName = "";
        detailPlate.style.viewTransitionName = "morph-plate";
        detailTitle.style.viewTransitionName = "morph-title";
        fillDetailContent(p, cat);
        detail.hidden = false;
        scrim.hidden = false;
        detail.classList.add("is-open");
        scrim.classList.add("is-open");
        closeBtn.focus({ preventScroll: true });
      });
      transition.finished.catch(() => {}).then(() => {
        detail.classList.remove("vt");
        scrim.classList.remove("vt");
      });
    } else {
      fillDetailContent(p, cat);
      detail.hidden = false;
      scrim.hidden = false;
      void detail.offsetWidth; // let the browser register the closed state before opening
      detail.classList.add("is-open");
      scrim.classList.add("is-open");
      closeBtn.focus({ preventScroll: true });
    }
  }

  function closeDetail() {
    const detail = document.getElementById("detail");
    const scrim = document.getElementById("scrim");
    if (detail.hidden) return;
    const card = openCard;
    const canMorph = supportsMorph() && card && card.plateEl && card.titleEl &&
      card.plateEl.isConnected && card.titleEl.isConnected;
    const returnFocus = () => {
      if (lastFocused && lastFocused.isConnected) lastFocused.focus({ preventScroll: true });
      openCard = null;
    };

    if (canMorph) {
      const detailPlate = document.getElementById("detailPlate");
      const detailTitle = document.getElementById("detailTitle");
      detail.classList.add("vt");
      scrim.classList.add("vt");
      const transition = document.startViewTransition(() => {
        detailPlate.style.viewTransitionName = "";
        detailTitle.style.viewTransitionName = "";
        card.plateEl.style.viewTransitionName = "morph-plate";
        card.titleEl.style.viewTransitionName = "morph-title";
        detail.classList.remove("is-open");
        scrim.classList.remove("is-open");
        detail.hidden = true;
        scrim.hidden = true;
      });
      transition.finished.catch(() => {}).then(() => {
        card.plateEl.style.viewTransitionName = "";
        card.titleEl.style.viewTransitionName = "";
        detail.classList.remove("vt");
        scrim.classList.remove("vt");
        returnFocus();
      });
    } else {
      detail.classList.remove("is-open");
      scrim.classList.remove("is-open");
      clearTimeout(closeTimer);
      closeTimer = setTimeout(() => {
        detail.hidden = true;
        scrim.hidden = true;
      }, 320);
      returnFocus();
    }
  }

  function initDetailControls() {
    document.getElementById("detailClose").addEventListener("click", closeDetail);
    document.getElementById("scrim").addEventListener("click", closeDetail);
    document.getElementById("slidePrev").addEventListener("click", () => goToSlide(slideIndex - 1));
    document.getElementById("slideNext").addEventListener("click", () => goToSlide(slideIndex + 1));

    document.addEventListener("keydown", (e) => {
      if (document.getElementById("detail").hidden) return;
      if (e.key === "Escape") closeDetail();
      else if (e.key === "ArrowLeft") goToSlide(slideIndex - 1);
      else if (e.key === "ArrowRight") goToSlide(slideIndex + 1);
    });

    // Swipe or drag sideways on the picture to flick through.
    const plate = document.getElementById("detailPlate");
    let startX = null;
    plate.addEventListener("pointerdown", (e) => { startX = e.clientX; });
    plate.addEventListener("pointerup", (e) => {
      if (startX === null) return;
      const dx = e.clientX - startX;
      startX = null;
      if (Math.abs(dx) > 40) goToSlide(slideIndex + (dx < 0 ? 1 : -1));
    });
    plate.addEventListener("pointercancel", () => { startX = null; });
  }

  // ---------- Pointer trail: grid squares light up under the mouse ----------
  function initTrail() {
    const canvas = document.getElementById("trail");
    if (!canvas || prefersReducedMotion()) return;
    const ctx = canvas.getContext("2d");
    if (!ctx) return;

    const CELL = 24;      // matches the minor grid lines
    const FADE = 1400;    // ms for a lit square to fade out
    const COLORS = [[255, 77, 141], [0, 224, 191], [255, 176, 32], [140, 107, 255], [204, 255, 51]];
    const lit = new Map();
    let running = false;
    let last = null;

    function resize() {
      const dpr = Math.min(window.devicePixelRatio || 1, 2);
      canvas.width = Math.round(window.innerWidth * dpr);
      canvas.height = Math.round(window.innerHeight * dpr);
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    }

    function addCell(cx, cy) {
      const key = cx + "," + cy;
      lit.delete(key);
      lit.set(key, { cx, cy, color: COLORS[Math.floor(Math.random() * COLORS.length)], t: performance.now() });
      if (lit.size > 260) lit.delete(lit.keys().next().value);
    }

    function lightAt(px, py) {
      const cx = Math.floor(px / CELL);
      const cy = Math.floor(py / CELL);
      addCell(cx, cy);
      if (Math.random() < 0.35) {
        addCell(cx + Math.floor(Math.random() * 3) - 1, cy + Math.floor(Math.random() * 3) - 1);
      }
    }

    function frame() {
      const now = performance.now();
      ctx.clearRect(0, 0, window.innerWidth, window.innerHeight);
      const sx = window.scrollX;
      const sy = window.scrollY;
      lit.forEach((c, key) => {
        const age = now - c.t;
        if (age > FADE) { lit.delete(key); return; }
        const a = Math.pow(1 - age / FADE, 1.6) * 0.62;
        ctx.fillStyle = "rgba(" + c.color[0] + "," + c.color[1] + "," + c.color[2] + "," + a.toFixed(3) + ")";
        ctx.fillRect(c.cx * CELL - sx + 1, c.cy * CELL - sy + 1, CELL - 1, CELL - 1);
      });
      if (lit.size) requestAnimationFrame(frame);
      else running = false;
    }

    window.addEventListener("pointermove", (e) => {
      const px = e.clientX + window.scrollX;
      const py = e.clientY + window.scrollY;
      if (last) {
        const dx = px - last.x;
        const dy = py - last.y;
        const dist = Math.hypot(dx, dy);
        if (dist < 600) {
          const steps = Math.max(1, Math.ceil(dist / (CELL * 0.75)));
          for (let s = 1; s <= steps; s++) lightAt(last.x + dx * s / steps, last.y + dy * s / steps);
        } else {
          lightAt(px, py);
        }
      } else {
        lightAt(px, py);
      }
      last = { x: px, y: py };
      if (!running) {
        running = true;
        requestAnimationFrame(frame);
      }
    }, { passive: true });

    window.addEventListener("resize", resize);
    resize();
  }

  // ---------- Eyes that follow the pointer ----------
  function initEyes() {
    const eyes = Array.from(document.querySelectorAll(".eye"));
    if (!eyes.length) return;
    let px = window.innerWidth / 2;
    let py = window.innerHeight / 2;
    let queued = false;

    function update() {
      queued = false;
      eyes.forEach((eye) => {
        const r = eye.getBoundingClientRect();
        const dx = px - (r.left + r.width / 2);
        const dy = py - (r.top + r.height / 2);
        const dist = Math.hypot(dx, dy);
        const reach = r.width * 0.2;
        const k = dist ? (reach * Math.min(1, dist / 160)) / dist : 0;
        eye.style.setProperty("--ox", (dx * k).toFixed(1) + "px");
        eye.style.setProperty("--oy", (dy * k).toFixed(1) + "px");
      });
    }

    function schedule() {
      if (!queued) {
        queued = true;
        requestAnimationFrame(update);
      }
    }

    window.addEventListener("pointermove", (e) => { px = e.clientX; py = e.clientY; schedule(); }, { passive: true });
    window.addEventListener("scroll", schedule, { passive: true });
    window.addEventListener("resize", schedule);
    schedule();
  }

  // ---------- Start ----------
  buildNameLetters("nameFirst", "JORDAN");
  buildNameLetters("nameLast", "RIVAS");
  document.getElementById("year").textContent = String(new Date().getFullYear());

  initDetailControls();
  renderFilters();
  applyFilter();
  tryLoadFromWordPress(WP_API_BASE);
  initTrail();
  initEyes();
</script>

</body></html>
