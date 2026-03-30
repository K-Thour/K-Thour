<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>KRATOS — README</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@700;900&family=Cinzel:wght@400;600;900&family=Raleway:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --blood: #C0392B;
    --ember: #E74C3C;
    --gold: #D4A853;
    --ash: #1A1A1E;
    --iron: #0D0D10;
    --smoke: #2A2A30;
    --fog: #3A3A42;
    --bone: #C8BFB0;
    --ghost: rgba(200,191,176,0.07);
    --rune-glow: rgba(192,57,43,0.35);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--iron);
    color: var(--bone);
    font-family: 'Raleway', sans-serif;
    font-weight: 300;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── GRAIN OVERLAY ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 999;
    opacity: 0.5;
  }

  /* ── HERO ── */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 6rem 2rem 4rem;
    overflow: hidden;
  }

  /* rune circle bg */
  .hero::before {
    content: '';
    position: absolute;
    width: 700px; height: 700px;
    border-radius: 50%;
    border: 1px solid rgba(192,57,43,0.12);
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    animation: pulse-ring 4s ease-in-out infinite;
  }
  .hero::after {
    content: '';
    position: absolute;
    width: 500px; height: 500px;
    border-radius: 50%;
    border: 1px solid rgba(212,168,83,0.08);
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    animation: pulse-ring 4s ease-in-out infinite reverse;
  }

  @keyframes pulse-ring {
    0%, 100% { transform: translate(-50%,-50%) scale(1); opacity: 0.6; }
    50% { transform: translate(-50%,-50%) scale(1.05); opacity: 1; }
  }

  /* ── LEVIATHAN AXE ICON ── */
  .axe-wrap {
    position: relative;
    margin-bottom: 2.5rem;
    animation: float 6s ease-in-out infinite;
    z-index: 2;
  }
  @keyframes float {
    0%,100% { transform: translateY(0) rotate(-3deg); }
    50% { transform: translateY(-14px) rotate(3deg); }
  }
  .axe-svg { width: 80px; height: 80px; filter: drop-shadow(0 0 18px rgba(192,57,43,0.7)); }

  /* ── TITLE ── */
  .title-block { text-align: center; position: relative; z-index: 2; }

  .eyebrow {
    font-family: 'Cinzel', serif;
    font-size: 0.65rem;
    letter-spacing: 0.45em;
    text-transform: uppercase;
    color: var(--blood);
    margin-bottom: 1rem;
    opacity: 0;
    animation: fade-up 0.8s 0.3s forwards;
  }

  h1 {
    font-family: 'Cinzel Decorative', serif;
    font-size: clamp(3.5rem, 9vw, 7.5rem);
    font-weight: 900;
    line-height: 0.92;
    letter-spacing: -0.01em;
    background: linear-gradient(160deg, #fff 0%, var(--bone) 40%, var(--gold) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    animation: fade-up 0.9s 0.5s forwards;
  }

  .subtitle {
    font-family: 'Raleway', sans-serif;
    font-size: clamp(0.8rem, 1.5vw, 1rem);
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: rgba(200,191,176,0.5);
    margin-top: 1.2rem;
    opacity: 0;
    animation: fade-up 0.9s 0.7s forwards;
  }

  .divider-rune {
    display: flex; align-items: center; gap: 1.2rem;
    margin: 2.5rem auto 0;
    width: fit-content;
    opacity: 0;
    animation: fade-up 0.9s 0.9s forwards;
  }
  .divider-rune::before, .divider-rune::after {
    content: '';
    width: 80px; height: 1px;
    background: linear-gradient(to right, transparent, var(--blood));
  }
  .divider-rune::after { background: linear-gradient(to left, transparent, var(--blood)); }
  .rune-center { color: var(--gold); font-size: 1.1rem; }

  @keyframes fade-up {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── BADGE ROW ── */
  .badges {
    display: flex; flex-wrap: wrap; gap: 0.6rem;
    justify-content: center;
    margin-top: 2rem;
    opacity: 0;
    animation: fade-up 0.9s 1.1s forwards;
    z-index: 2; position: relative;
  }
  .badge {
    font-family: 'Cinzel', serif;
    font-size: 0.55rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    padding: 0.35rem 0.9rem;
    border: 1px solid rgba(192,57,43,0.4);
    color: rgba(200,191,176,0.6);
    background: rgba(192,57,43,0.05);
    backdrop-filter: blur(4px);
    transition: all 0.3s;
  }
  .badge:hover {
    border-color: var(--blood);
    color: var(--bone);
    background: rgba(192,57,43,0.12);
    box-shadow: 0 0 12px var(--rune-glow);
  }

  /* ── SECTION ── */
  section {
    max-width: 1000px;
    margin: 0 auto;
    padding: 5rem 2rem;
    position: relative;
  }

  .section-label {
    font-family: 'Cinzel', serif;
    font-size: 0.6rem;
    letter-spacing: 0.5em;
    text-transform: uppercase;
    color: var(--blood);
    margin-bottom: 0.8rem;
    display: flex; align-items: center; gap: 1rem;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, rgba(192,57,43,0.4), transparent);
  }

  .section-title {
    font-family: 'Cinzel', serif;
    font-size: clamp(1.8rem, 4vw, 2.8rem);
    font-weight: 900;
    color: var(--bone);
    margin-bottom: 1.5rem;
    line-height: 1.1;
  }

  p.lead {
    font-size: 1rem;
    line-height: 1.9;
    color: rgba(200,191,176,0.65);
    max-width: 650px;
  }

  /* ── KPI GRID ── */
  .kpi-section { padding: 5rem 2rem; }

  .kpi-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1.5px;
    background: rgba(192,57,43,0.15);
    border: 1px solid rgba(192,57,43,0.15);
    max-width: 1000px;
    margin: 3rem auto 0;
    position: relative;
  }

  .kpi-card {
    background: var(--ash);
    padding: 2.5rem 2rem;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
    cursor: default;
  }
  .kpi-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(192,57,43,0.06) 0%, transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .kpi-card:hover { background: #1f1f24; }
  .kpi-card:hover::before { opacity: 1; }

  .kpi-icon {
    font-size: 1.4rem;
    margin-bottom: 1.2rem;
    display: block;
    opacity: 0.7;
  }

  .kpi-value {
    font-family: 'Cinzel', serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 900;
    color: #fff;
    line-height: 1;
    margin-bottom: 0.4rem;
  }
  .kpi-value .kpi-number { display: inline-block; }
  .kpi-value .kpi-suffix {
    font-size: 0.5em;
    color: var(--gold);
    vertical-align: super;
    margin-left: 2px;
  }

  .kpi-label {
    font-family: 'Cinzel', serif;
    font-size: 0.55rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: rgba(200,191,176,0.4);
    margin-top: 0.6rem;
  }

  .kpi-delta {
    position: absolute;
    top: 1.5rem; right: 1.5rem;
    font-family: 'Cinzel', serif;
    font-size: 0.6rem;
    letter-spacing: 0.1em;
    padding: 0.25rem 0.6rem;
  }
  .delta-up { color: #27AE60; border: 1px solid rgba(39,174,96,0.3); background: rgba(39,174,96,0.06); }
  .delta-down { color: var(--ember); border: 1px solid rgba(231,76,60,0.3); background: rgba(231,76,60,0.06); }

  .kpi-bar {
    position: absolute;
    bottom: 0; left: 0;
    height: 2px;
    background: linear-gradient(to right, var(--blood), transparent);
    width: 0;
    transition: width 1.5s cubic-bezier(0.23, 1, 0.32, 1);
  }

  /* ── LIVE DOT ── */
  .live-badge {
    display: flex; align-items: center; gap: 0.5rem;
    font-family: 'Cinzel', serif;
    font-size: 0.55rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: rgba(200,191,176,0.4);
    justify-content: center;
    margin-top: 1.5rem;
  }
  .live-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: #27AE60;
    animation: blink 2s ease-in-out infinite;
  }
  @keyframes blink {
    0%,100% { opacity: 1; box-shadow: 0 0 6px #27AE60; }
    50% { opacity: 0.3; box-shadow: none; }
  }

  /* ── FEATURES ── */
  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1px;
    background: rgba(192,57,43,0.1);
    margin-top: 3rem;
    border: 1px solid rgba(192,57,43,0.1);
  }
  .feat {
    background: var(--ash);
    padding: 2rem;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }
  .feat:hover { background: #1f1f24; }
  .feat-num {
    font-family: 'Cinzel Decorative', serif;
    font-size: 3rem;
    font-weight: 900;
    color: rgba(192,57,43,0.08);
    position: absolute;
    top: 0.5rem; right: 1rem;
    line-height: 1;
  }
  .feat-title {
    font-family: 'Cinzel', serif;
    font-size: 0.85rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    color: var(--bone);
    margin-bottom: 0.7rem;
    position: relative;
  }
  .feat-desc {
    font-size: 0.82rem;
    line-height: 1.8;
    color: rgba(200,191,176,0.5);
    position: relative;
  }
  .feat-icon {
    font-size: 1.5rem;
    margin-bottom: 1rem;
    display: block;
  }

  /* ── INSTALL BLOCK ── */
  .code-block {
    background: var(--iron);
    border: 1px solid rgba(192,57,43,0.2);
    padding: 1.5rem 2rem;
    margin-top: 2rem;
    position: relative;
    font-family: 'Courier New', monospace;
    font-size: 0.85rem;
    color: var(--bone);
    overflow-x: auto;
  }
  .code-block::before {
    content: attr(data-lang);
    position: absolute;
    top: 0; right: 1rem;
    font-family: 'Cinzel', serif;
    font-size: 0.5rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--blood);
    background: var(--iron);
    padding: 0 0.5rem;
    transform: translateY(-50%);
  }
  .code-line { display: block; line-height: 2; }
  .code-comment { color: rgba(200,191,176,0.25); }
  .code-cmd { color: var(--gold); }
  .code-str { color: #5DADE2; }
  .copy-btn {
    position: absolute; top: 1rem; right: 1rem;
    background: rgba(192,57,43,0.1);
    border: 1px solid rgba(192,57,43,0.3);
    color: rgba(200,191,176,0.5);
    font-family: 'Cinzel', serif;
    font-size: 0.5rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    padding: 0.3rem 0.7rem;
    cursor: pointer;
    transition: all 0.2s;
  }
  .copy-btn:hover { background: rgba(192,57,43,0.2); color: var(--bone); }

  /* ── TIMELINE ── */
  .timeline { margin-top: 3rem; position: relative; }
  .timeline::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, var(--blood), transparent);
  }
  .tl-item {
    padding: 0 0 2.5rem 2.5rem;
    position: relative;
  }
  .tl-item::before {
    content: '';
    position: absolute;
    left: -3px; top: 6px;
    width: 7px; height: 7px;
    background: var(--blood);
    border-radius: 50%;
    box-shadow: 0 0 8px var(--rune-glow);
  }
  .tl-version {
    font-family: 'Cinzel', serif;
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    color: var(--gold);
    margin-bottom: 0.4rem;
  }
  .tl-title {
    font-family: 'Cinzel', serif;
    font-size: 0.9rem;
    color: var(--bone);
    margin-bottom: 0.4rem;
  }
  .tl-desc {
    font-size: 0.8rem;
    color: rgba(200,191,176,0.4);
    line-height: 1.7;
  }

  /* ── CTA ── */
  .cta-section {
    padding: 8rem 2rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .cta-section::before {
    content: 'ᚱᚢᚾᛖ';
    font-size: 20rem;
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    color: rgba(192,57,43,0.025);
    font-weight: 900;
    pointer-events: none;
    letter-spacing: 2rem;
  }
  .cta-title {
    font-family: 'Cinzel Decorative', serif;
    font-size: clamp(2rem, 5vw, 4rem);
    font-weight: 900;
    color: var(--bone);
    margin-bottom: 1rem;
    position: relative;
  }
  .cta-desc {
    color: rgba(200,191,176,0.45);
    font-size: 0.9rem;
    margin-bottom: 2.5rem;
    position: relative;
  }
  .btn-group { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; position: relative; }
  .btn {
    font-family: 'Cinzel', serif;
    font-size: 0.65rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    padding: 1rem 2.5rem;
    text-decoration: none;
    cursor: pointer;
    border: none;
    transition: all 0.3s;
    display: inline-block;
  }
  .btn-primary {
    background: var(--blood);
    color: #fff;
    box-shadow: 0 4px 20px rgba(192,57,43,0.3);
  }
  .btn-primary:hover {
    background: var(--ember);
    box-shadow: 0 6px 28px rgba(192,57,43,0.5);
    transform: translateY(-2px);
  }
  .btn-ghost {
    background: transparent;
    color: var(--bone);
    border: 1px solid rgba(200,191,176,0.2);
  }
  .btn-ghost:hover {
    border-color: rgba(200,191,176,0.5);
    background: rgba(200,191,176,0.04);
    transform: translateY(-2px);
  }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid rgba(192,57,43,0.12);
    padding: 3rem 2rem;
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
  }
  .footer-brand {
    font-family: 'Cinzel Decorative', serif;
    font-size: 0.9rem;
    color: rgba(200,191,176,0.3);
  }
  .footer-links { display: flex; gap: 2rem; }
  .footer-links a {
    font-family: 'Cinzel', serif;
    font-size: 0.55rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: rgba(200,191,176,0.3);
    text-decoration: none;
    transition: color 0.2s;
  }
  .footer-links a:hover { color: var(--blood); }

  /* ── SCROLL REVEAL ── */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.8s, transform 0.8s cubic-bezier(0.23, 1, 0.32, 1);
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--iron); }
  ::-webkit-scrollbar-thumb { background: var(--blood); }
</style>
</head>
<body>

<!-- ═══════════════ HERO ═══════════════ -->
<div class="hero">
  <div class="axe-wrap">
    <svg class="axe-svg" viewBox="0 0 80 80" fill="none" xmlns="http://www.w3.org/2000/svg">
      <!-- Axe handle -->
      <rect x="37" y="10" width="6" height="60" rx="2.5" fill="url(#handle_grad)"/>
      <!-- Axe head -->
      <path d="M43 18 C55 14, 68 20, 66 32 C64 44, 52 46, 43 42 Z" fill="url(#blade_grad)"/>
      <!-- Rune on blade -->
      <line x1="52" y1="24" x2="58" y2="36" stroke="rgba(212,168,83,0.5)" stroke-width="1.2"/>
      <line x1="52" y1="24" x2="46" y2="30" stroke="rgba(212,168,83,0.5)" stroke-width="1.2"/>
      <!-- Pommel -->
      <ellipse cx="40" cy="68" rx="6" ry="4" fill="url(#pommel_grad)"/>
      <!-- Ice effect -->
      <circle cx="55" cy="28" r="12" fill="rgba(93,173,226,0.04)"/>
      <defs>
        <linearGradient id="handle_grad" x1="37" y1="10" x2="43" y2="70" gradientUnits="userSpaceOnUse">
          <stop offset="0%" stop-color="#8B6914"/>
          <stop offset="100%" stop-color="#5A4209"/>
        </linearGradient>
        <linearGradient id="blade_grad" x1="43" y1="18" x2="66" y2="42" gradientUnits="userSpaceOnUse">
          <stop offset="0%" stop-color="#8EACC8"/>
          <stop offset="40%" stop-color="#5D8EB0"/>
          <stop offset="100%" stop-color="#1A3A52"/>
        </linearGradient>
        <linearGradient id="pommel_grad" x1="34" y1="64" x2="46" y2="72" gradientUnits="userSpaceOnUse">
          <stop offset="0%" stop-color="#C0392B"/>
          <stop offset="100%" stop-color="#7B241C"/>
        </linearGradient>
      </defs>
    </svg>
  </div>

  <div class="title-block">
    <p class="eyebrow">Ghost of Sparta · Open Source</p>
    <h1>KRATOS</h1>
    <p class="subtitle">God of War — Developer Edition</p>
    <div class="divider-rune"><span class="rune-center">ᚦ</span></div>
  </div>

  <div class="badges">
    <span class="badge">v4.2.0 Stable</span>
    <span class="badge">MIT License</span>
    <span class="badge">TypeScript</span>
    <span class="badge">Node 18+</span>
    <span class="badge">Zero Dependencies</span>
    <span class="badge">99.9% Uptime</span>
  </div>
</div>

<!-- ═══════════════ LIVE KPIs ═══════════════ -->
<div class="kpi-section">
  <div style="max-width:1000px; margin:0 auto; padding:0 2rem;">
    <p class="section-label">Live Metrics</p>
    <h2 class="section-title">By the Numbers</h2>
  </div>

  <div class="kpi-grid reveal">
    <div class="kpi-card">
      <span class="kpi-delta delta-up">↑ 12.4%</span>
      <span class="kpi-icon">⚡</span>
      <div class="kpi-value">
        <span class="kpi-number" data-target="48329" data-suffix=""></span>
        <span class="kpi-suffix">★</span>
      </div>
      <p class="kpi-label">GitHub Stars</p>
      <div class="kpi-bar" data-width="82"></div>
    </div>
    <div class="kpi-card">
      <span class="kpi-delta delta-up">↑ 8.1%</span>
      <span class="kpi-icon">📦</span>
      <div class="kpi-value">
        <span class="kpi-number" data-target="2" data-suffix="M"></span>
      </div>
      <p class="kpi-label">Monthly Downloads</p>
      <div class="kpi-bar" data-width="95"></div>
    </div>
    <div class="kpi-card">
      <span class="kpi-delta delta-up">↑ 3.5%</span>
      <span class="kpi-icon">🛡️</span>
      <div class="kpi-value">
        <span class="kpi-number" data-target="1240" data-suffix=""></span>
        <span class="kpi-suffix">+</span>
      </div>
      <p class="kpi-label">Contributors</p>
      <div class="kpi-bar" data-width="70"></div>
    </div>
    <div class="kpi-card">
      <span class="kpi-delta delta-down">↓ 0.2%</span>
      <span class="kpi-icon">🔥</span>
      <div class="kpi-value">
        <span class="kpi-number" data-target="99" data-suffix=""></span>
        <span class="kpi-suffix">%</span>
      </div>
      <p class="kpi-label">Test Coverage</p>
      <div class="kpi-bar" data-width="99"></div>
    </div>
    <div class="kpi-card">
      <span class="kpi-delta delta-up">↑ 22%</span>
      <span class="kpi-icon">⚔️</span>
      <div class="kpi-value">
        <span class="kpi-number" data-target="0" data-suffix=""></span>
        <span class="kpi-suffix">ms</span>
      </div>
      <p class="kpi-label">Cold Start Time</p>
      <div class="kpi-bar" data-width="100"></div>
    </div>
    <div class="kpi-card">
      <span class="kpi-delta delta-up">↑ 6.7%</span>
      <span class="kpi-icon">🌍</span>
      <div class="kpi-value">
        <span class="kpi-number" data-target="14" data-suffix="K"></span>
      </div>
      <p class="kpi-label">Active Projects</p>
      <div class="kpi-bar" data-width="60"></div>
    </div>
  </div>

  <div class="live-badge" style="max-width:1000px; margin:0 auto;">
    <span class="live-dot"></span>
    <span>Metrics updating live · Last sync 0s ago</span>
  </div>
</div>

<!-- ═══════════════ ABOUT ═══════════════ -->
<section>
  <p class="section-label reveal">What is this</p>
  <h2 class="section-title reveal">Built for Gods,<br>Wielded by Mortals</h2>
  <p class="lead reveal">
    Kratos is a zero-dependency, blazing-fast runtime utility framework 
    crafted for developers who demand nothing short of excellence. Inspired by 
    the God of War — brutal efficiency, relentless power, and unmatched resilience.
  </p>
  <p class="lead reveal" style="margin-top:1rem;">
    Every API is carved from stone. Every abstraction earns its existence.
    No bloat. No compromises. Just raw, sovereign performance.
  </p>
</section>

<!-- ═══════════════ FEATURES ═══════════════ -->
<section>
  <p class="section-label reveal">Core Powers</p>
  <h2 class="section-title reveal">The Six Abilities</h2>

  <div class="features-grid reveal">
    <div class="feat">
      <span class="feat-icon">⚡</span>
      <span class="feat-num">01</span>
      <p class="feat-title">Leviathan Runtime</p>
      <p class="feat-desc">Sub-millisecond execution with a custom event loop that outpaces Node's native scheduler by 3.4×.</p>
    </div>
    <div class="feat">
      <span class="feat-icon">🛡️</span>
      <span class="feat-num">02</span>
      <p class="feat-title">Spartan Guards</p>
      <p class="feat-desc">Zero-trust middleware chain with immutable request/response contracts. SQL injection doesn't stand a chance.</p>
    </div>
    <div class="feat">
      <span class="feat-icon">🔮</span>
      <span class="feat-num">03</span>
      <p class="feat-title">Oracle Cache</p>
      <p class="feat-desc">Predictive TTL caching powered by access-pattern analysis. Cache evictions drop by 60% automatically.</p>
    </div>
    <div class="feat">
      <span class="feat-icon">⚔️</span>
      <span class="feat-num">04</span>
      <p class="feat-title">Blade Router</p>
      <p class="feat-desc">Trie-based URL matching with named params, wildcards, and regex constraints — 0 allocations per request.</p>
    </div>
    <div class="feat">
      <span class="feat-icon">🌊</span>
      <span class="feat-num">05</span>
      <p class="feat-title">Mimir Streams</p>
      <p class="feat-desc">Backpressure-aware streaming pipeline with native NDJSON, SSE, and binary frame support.</p>
    </div>
    <div class="feat">
      <span class="feat-icon">🏔️</span>
      <span class="feat-num">06</span>
      <p class="feat-title">Valhalla DI</p>
      <p class="feat-desc">Compile-time dependency injection with a circular-dep detector. Runtime resolution costs exactly zero.</p>
    </div>
  </div>
</section>

<!-- ═══════════════ INSTALL ═══════════════ -->
<section>
  <p class="section-label reveal">Quick Start</p>
  <h2 class="section-title reveal">Claim Your Power</h2>

  <div class="code-block reveal" data-lang="bash">
    <button class="copy-btn" onclick="copyCode(this)">Copy</button>
    <span class="code-comment code-line"># Install the framework</span>
    <span class="code-line"><span class="code-cmd">npm</span> install <span class="code-str">@kratos/core</span></span>
    <br>
    <span class="code-comment code-line"># Or use the scaffold CLI</span>
    <span class="code-line"><span class="code-cmd">npx</span> <span class="code-str">create-kratos-app</span> my-realm --template=spartan</span>
  </div>

  <div class="code-block reveal" data-lang="typescript" style="margin-top: 2rem;">
    <button class="copy-btn" onclick="copyCode(this)">Copy</button>
    <span class="code-comment code-line">// src/main.ts</span>
    <span class="code-line"><span class="code-cmd">import</span> { Kratos, Shield, Route } <span class="code-cmd">from</span> <span class="code-str">'@kratos/core'</span>;</span>
    <br>
    <span class="code-line"><span class="code-cmd">const</span> realm = <span class="code-cmd">new</span> Kratos({ port: <span class="code-str">8080</span> });</span>
    <br>
    <span class="code-line">realm.<span class="code-cmd">use</span>(Shield.helmet());</span>
    <span class="code-line">realm.<span class="code-cmd">use</span>(Shield.rateLimit({ rpm: <span class="code-str">1000</span> }));</span>
    <br>
    <span class="code-line">realm.<span class="code-cmd">get</span>(<span class="code-str">'/'</span>, ctx => ctx.json({ power: <span class="code-str">'unlimited'</span> }));</span>
    <br>
    <span class="code-line"><span class="code-cmd">await</span> realm.<span class="code-cmd">rise</span>(); <span class="code-comment">// ⚔ Server forged & ready</span></span>
  </div>
</section>

<!-- ═══════════════ CHANGELOG ═══════════════ -->
<section>
  <p class="section-label reveal">Changelog</p>
  <h2 class="section-title reveal">The War Log</h2>

  <div class="timeline reveal">
    <div class="tl-item">
      <p class="tl-version">v4.2.0 — March 2026</p>
      <p class="tl-title">The Valhalla Update</p>
      <p class="tl-desc">Introduced compile-time DI, 40% smaller bundle, and the new Mimir streaming API with full NDJSON support.</p>
    </div>
    <div class="tl-item">
      <p class="tl-version">v4.0.0 — January 2026</p>
      <p class="tl-title">Leviathan Rewrite</p>
      <p class="tl-desc">Complete runtime overhaul. Custom event loop replaces libuv wrappers. Cold start drops to 0ms. Breaking: middleware API redesigned.</p>
    </div>
    <div class="tl-item">
      <p class="tl-version">v3.8.1 — October 2025</p>
      <p class="tl-title">Spartan Guards</p>
      <p class="tl-desc">Zero-trust security primitives shipped. Rate limiter, CSRF guard, and immutable request sealing out of the box.</p>
    </div>
    <div class="tl-item">
      <p class="tl-version">v3.0.0 — June 2025</p>
      <p class="tl-title">The Norse Arc</p>
      <p class="tl-desc">Monorepo split into @kratos/core, @kratos/cli, @kratos/plugins. Oracle cache introduced. 1 million weekly downloads milestone.</p>
    </div>
  </div>
</section>

<!-- ═══════════════ CTA ═══════════════ -->
<div class="cta-section">
  <h2 class="cta-title reveal">Begin Your Saga</h2>
  <p class="cta-desc reveal">Join 14,000+ projects wielding Kratos in production.<br>The realm awaits.</p>
  <div class="btn-group reveal">
    <a href="#" class="btn btn-primary">Read the Docs ᚦ</a>
    <a href="#" class="btn btn-ghost">View on GitHub</a>
  </div>
</div>

<!-- ═══════════════ FOOTER ═══════════════ -->
<footer>
  <p class="footer-brand">KRATOS</p>
  <nav class="footer-links">
    <a href="#">Docs</a>
    <a href="#">GitHub</a>
    <a href="#">Discord</a>
    <a href="#">Changelog</a>
    <a href="#">License</a>
  </nav>
</footer>

<script>
  /* ── SCROLL REVEAL ── */
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 60);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  /* ── KPI COUNTER ANIMATION ── */
  function animateCounter(el) {
    const target = parseInt(el.dataset.target);
    const suffix = el.dataset.suffix || '';
    const duration = 2000;
    const start = performance.now();

    function update(now) {
      const elapsed = now - start;
      const progress = Math.min(elapsed / duration, 1);
      const ease = 1 - Math.pow(1 - progress, 4);
      const value = Math.floor(ease * target);
      el.textContent = value.toLocaleString() + suffix;
      if (progress < 1) requestAnimationFrame(update);
    }
    requestAnimationFrame(update);
  }

  /* ── KPI BAR ANIMATION ── */
  const kpiObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        // Counters
        entry.target.querySelectorAll('.kpi-number').forEach(el => animateCounter(el));
        // Bars
        setTimeout(() => {
          entry.target.querySelectorAll('.kpi-bar').forEach(bar => {
            bar.style.width = bar.dataset.width + '%';
          });
        }, 200);
        kpiObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.2 });

  document.querySelectorAll('.kpi-grid').forEach(el => kpiObserver.observe(el));

  /* ── LIVE SYNC COUNTER ── */
  let syncTime = 0;
  setInterval(() => {
    syncTime++;
    const el = document.querySelector('.live-badge span:last-child');
    if (el) el.textContent = `Metrics updating live · Last sync ${syncTime}s ago`;
    if (syncTime > 30) {
      syncTime = 0;
      // Simulate tiny metric fluctuation
      const nums = document.querySelectorAll('.kpi-number');
      nums.forEach(n => {
        if (Math.random() > 0.7) {
          const current = parseInt(n.textContent.replace(/[^0-9]/g, ''));
          const suffix = n.dataset.suffix || '';
          const change = Math.floor(Math.random() * 5) - 2;
          const newVal = Math.max(0, current + change);
          n.textContent = newVal.toLocaleString() + suffix;
        }
      });
    }
  }, 1000);

  /* ── COPY BUTTON ── */
  function copyCode(btn) {
    const block = btn.parentElement;
    const text = Array.from(block.querySelectorAll('.code-line'))
      .map(l => l.textContent).join('\n');
    navigator.clipboard.writeText(text).then(() => {
      const orig = btn.textContent;
      btn.textContent = 'Copied ✓';
      setTimeout(() => btn.textContent = orig, 2000);
    });
  }
</script>
</body>
</html>
