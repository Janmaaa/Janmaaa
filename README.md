<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Janma K Gowda — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Clash+Display:wght@400;500;600;700&family=Outfit:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --p1: #0d0015;
    --p2: #1a0030;
    --p3: #2d0050;
    --accent1: #8b2be2;
    --accent2: #b06af0;
    --accent3: #d4a8ff;
    --accent4: #ecdeff;
    --glow: rgba(139, 43, 226, 0.35);
    --glass-bg: rgba(255,255,255,0.04);
    --glass-border: rgba(255,255,255,0.10);
    --glass-hover: rgba(255,255,255,0.08);
    --text1: #ffffff;
    --text2: #d4a8ff;
    --text3: #9b7cc4;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Outfit', sans-serif;
    background: var(--p1);
    color: var(--text1);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── BACKGROUND ── */
  .bg-scene {
    position: fixed;
    inset: 0;
    z-index: 0;
    pointer-events: none;
    overflow: hidden;
  }
  .bg-scene::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 20% 20%, rgba(90,20,160,0.45) 0%, transparent 60%),
      radial-gradient(ellipse 60% 50% at 80% 70%, rgba(50,0,100,0.4) 0%, transparent 60%),
      radial-gradient(ellipse 50% 40% at 50% 100%, rgba(120,40,200,0.2) 0%, transparent 60%);
  }

  /* floating particles */
  .particle {
    position: absolute;
    border-radius: 50%;
    animation: floatParticle linear infinite;
    opacity: 0;
  }
  @keyframes floatParticle {
    0%   { transform: translateY(110vh) scale(0); opacity: 0; }
    10%  { opacity: 0.6; }
    90%  { opacity: 0.3; }
    100% { transform: translateY(-10vh) scale(1.2); opacity: 0; }
  }

  /* grid overlay */
  .bg-grid {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(139,43,226,0.06) 1px, transparent 1px),
      linear-gradient(90deg, rgba(139,43,226,0.06) 1px, transparent 1px);
    background-size: 60px 60px;
  }

  /* ── LAYOUT ── */
  .page {
    position: relative;
    z-index: 1;
    max-width: 1000px;
    margin: 0 auto;
    padding: 40px 24px 80px;
  }

  /* ── GLASS MIXIN ── */
  .glass {
    background: var(--glass-bg);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid var(--glass-border);
    border-radius: 20px;
    transition: all 0.35s ease;
  }
  .glass:hover {
    background: var(--glass-hover);
    border-color: rgba(139,43,226,0.3);
    box-shadow: 0 8px 40px rgba(139,43,226,0.15), inset 0 1px 0 rgba(255,255,255,0.1);
    transform: translateY(-2px);
  }

  /* ── HERO ── */
  .hero {
    display: flex;
    align-items: center;
    gap: 36px;
    padding: 44px 48px;
    margin-bottom: 28px;
    position: relative;
    overflow: hidden;
    animation: revealDown 0.7s cubic-bezier(0.16,1,0.3,1) both;
  }
  .hero::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 280px; height: 280px;
    background: radial-gradient(circle, rgba(139,43,226,0.25), transparent 70%);
    border-radius: 50%;
    pointer-events: none;
  }
  .hero::after {
    content: '';
    position: absolute;
    bottom: -40px; left: -40px;
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(80,0,140,0.2), transparent 70%);
    border-radius: 50%;
    pointer-events: none;
  }

  /* avatar */
  .avatar-shell {
    position: relative;
    flex-shrink: 0;
    width: 110px; height: 110px;
  }
  .avatar-ring-outer {
    position: absolute;
    inset: -4px;
    border-radius: 50%;
    background: conic-gradient(from 0deg, #8b2be2, #d4a8ff, #2d0050, #8b2be2);
    animation: spinRing 5s linear infinite;
  }
  @keyframes spinRing {
    to { transform: rotate(360deg); }
  }
  .avatar-ring-inner {
    position: absolute;
    inset: 3px;
    border-radius: 50%;
    background: var(--p1);
  }
  .avatar-core {
    position: absolute;
    inset: 6px;
    border-radius: 50%;
    background: linear-gradient(135deg, #2d0050, #1a0030);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Clash Display', sans-serif;
    font-size: 30px;
    font-weight: 700;
    color: var(--accent3);
    letter-spacing: 1px;
    border: 1px solid rgba(139,43,226,0.4);
  }

  /* hero text */
  .hero-text { flex: 1; }
  .hero-name {
    font-family: 'Clash Display', sans-serif;
    font-size: clamp(28px, 4vw, 42px);
    font-weight: 700;
    line-height: 1.1;
    letter-spacing: -0.5px;
    background: linear-gradient(135deg, #ffffff 0%, #d4a8ff 50%, #8b2be2 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 6px;
  }
  .hero-role {
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    color: var(--accent2);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 14px;
  }
  .hero-role span {
    color: var(--accent3);
    opacity: 0.6;
    margin: 0 6px;
  }
  .hero-chips {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
    margin-bottom: 16px;
  }
  .chip {
    font-size: 11px;
    font-weight: 500;
    padding: 4px 12px;
    border-radius: 30px;
    border: 1px solid rgba(139,43,226,0.45);
    color: var(--accent3);
    background: rgba(139,43,226,0.1);
    letter-spacing: 0.3px;
    transition: all 0.2s;
    cursor: default;
    font-family: 'Outfit', sans-serif;
  }
  .chip:hover {
    background: rgba(139,43,226,0.25);
    border-color: var(--accent2);
    color: #fff;
    transform: translateY(-1px);
    box-shadow: 0 4px 14px rgba(139,43,226,0.2);
  }
  .chip-green {
    border-color: rgba(80,220,120,0.4);
    color: #80ffaa;
    background: rgba(80,220,120,0.08);
  }
  .chip-green:hover {
    background: rgba(80,220,120,0.18);
    border-color: #80ffaa;
    color: #fff;
  }

  .status-row {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 12px;
    color: #80ffaa;
    font-family: 'JetBrains Mono', monospace;
  }
  .pulse {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: #80ffaa;
    box-shadow: 0 0 8px #80ffaa;
    animation: pulseGlow 2s ease-in-out infinite;
    flex-shrink: 0;
  }
  @keyframes pulseGlow {
    0%,100% { opacity: 1; transform: scale(1); box-shadow: 0 0 8px #80ffaa; }
    50% { opacity: 0.5; transform: scale(0.7); box-shadow: 0 0 3px #80ffaa; }
  }

  /* ── INFO GRID ── */
  .info-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 14px;
    margin-bottom: 28px;
  }

  .info-card {
    padding: 20px 18px;
    border-radius: 16px;
    position: relative;
    overflow: hidden;
    cursor: default;
    animation: revealUp 0.6s cubic-bezier(0.16,1,0.3,1) both;
  }
  .info-card::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--accent1), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .info-card:hover::before { opacity: 1; }

  .info-card:nth-child(1) { animation-delay: 0.1s; }
  .info-card:nth-child(2) { animation-delay: 0.15s; }
  .info-card:nth-child(3) { animation-delay: 0.2s; }
  .info-card:nth-child(4) { animation-delay: 0.25s; }
  .info-card:nth-child(5) { animation-delay: 0.3s; }
  .info-card:nth-child(6) { animation-delay: 0.35s; }

  .card-emoji { font-size: 22px; margin-bottom: 10px; display: block; }
  .card-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 9px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--accent1);
    margin-bottom: 5px;
  }
  .card-title {
    font-family: 'Clash Display', sans-serif;
    font-size: 15px;
    font-weight: 600;
    color: var(--text1);
    margin-bottom: 2px;
  }
  .card-sub {
    font-size: 12px;
    color: var(--text3);
    font-weight: 300;
  }

  /* ── STATS ── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 14px;
    margin-bottom: 28px;
    animation: revealUp 0.6s cubic-bezier(0.16,1,0.3,1) 0.4s both;
  }
  .stat-card {
    padding: 22px 12px;
    text-align: center;
    border-radius: 16px;
    cursor: default;
    position: relative;
    overflow: hidden;
  }
  .stat-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 50% 0%, rgba(139,43,226,0.15), transparent 70%);
    pointer-events: none;
  }
  .stat-num {
    font-family: 'Clash Display', sans-serif;
    font-size: 30px;
    font-weight: 700;
    background: linear-gradient(135deg, #fff, var(--accent3));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    display: block;
    line-height: 1;
    margin-bottom: 6px;
  }
  .stat-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 9px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--text3);
  }

  /* ── SECTION TITLE ── */
  .section-title {
    font-family: 'Clash Display', sans-serif;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent2);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(139,43,226,0.4), transparent);
  }

  /* ── SKILLS ── */
  .skills-wrap {
    margin-bottom: 28px;
    animation: revealUp 0.6s cubic-bezier(0.16,1,0.3,1) 0.45s both;
  }
  .skills-block {
    padding: 24px 28px;
    border-radius: 20px;
  }
  .skill-group {
    margin-bottom: 20px;
  }
  .skill-group:last-child { margin-bottom: 0; }
  .skill-group-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--text3);
    margin-bottom: 10px;
  }
  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .skill-tag {
    font-size: 12px;
    font-weight: 500;
    padding: 6px 14px;
    border-radius: 8px;
    border: 1px solid rgba(139,43,226,0.3);
    color: var(--accent3);
    background: rgba(139,43,226,0.08);
    font-family: 'Outfit', sans-serif;
    transition: all 0.2s;
    cursor: default;
  }
  .skill-tag:hover {
    background: rgba(139,43,226,0.2);
    border-color: var(--accent2);
    color: #fff;
    transform: translateY(-2px) scale(1.04);
    box-shadow: 0 6px 20px rgba(139,43,226,0.2);
  }

  /* ── PROJECTS ── */
  .projects-wrap {
    margin-bottom: 28px;
    animation: revealUp 0.6s cubic-bezier(0.16,1,0.3,1) 0.5s both;
  }
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
  }
  .project-card {
    padding: 26px 24px;
    border-radius: 18px;
    position: relative;
    overflow: hidden;
    cursor: default;
  }
  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent1), transparent);
  }
  .project-number {
    font-family: 'Clash Display', sans-serif;
    font-size: 52px;
    font-weight: 700;
    color: rgba(139,43,226,0.12);
    position: absolute;
    top: 10px; right: 16px;
    line-height: 1;
    pointer-events: none;
    user-select: none;
  }
  .project-icon { font-size: 28px; margin-bottom: 12px; display: block; }
  .project-name {
    font-family: 'Clash Display', sans-serif;
    font-size: 18px;
    font-weight: 600;
    color: var(--text1);
    margin-bottom: 8px;
    line-height: 1.2;
  }
  .project-desc {
    font-size: 13px;
    color: var(--text3);
    line-height: 1.6;
    font-weight: 300;
    margin-bottom: 14px;
  }
  .project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  .project-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    padding: 3px 9px;
    border-radius: 5px;
    background: rgba(139,43,226,0.15);
    border: 1px solid rgba(139,43,226,0.25);
    color: var(--accent2);
  }

  /* ── WORK EXPERIENCE ── */
  .work-wrap {
    margin-bottom: 28px;
    animation: revealUp 0.6s cubic-bezier(0.16,1,0.3,1) 0.55s both;
  }
  .work-card {
    padding: 28px 32px;
    border-radius: 20px;
    position: relative;
    overflow: hidden;
  }
  .work-card::before {
    content: '';
    position: absolute;
    left: 0; top: 20%; bottom: 20%;
    width: 3px;
    background: linear-gradient(180deg, transparent, var(--accent1), transparent);
    border-radius: 2px;
  }
  .work-header {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    margin-bottom: 6px;
    gap: 12px;
    flex-wrap: wrap;
  }
  .work-company {
    font-family: 'Clash Display', sans-serif;
    font-size: 20px;
    font-weight: 700;
    color: var(--text1);
  }
  .work-badge {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    padding: 4px 12px;
    border-radius: 20px;
    background: rgba(80,220,120,0.1);
    border: 1px solid rgba(80,220,120,0.3);
    color: #80ffaa;
    letter-spacing: 1px;
    flex-shrink: 0;
  }
  .work-role {
    font-size: 13px;
    color: var(--accent2);
    letter-spacing: 1px;
    margin-bottom: 18px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    text-transform: uppercase;
  }
  .work-points { list-style: none; }
  .work-points li {
    font-size: 13.5px;
    color: var(--text3);
    padding: 6px 0;
    padding-left: 18px;
    position: relative;
    font-weight: 300;
    line-height: 1.5;
    border-bottom: 1px solid rgba(255,255,255,0.04);
  }
  .work-points li:last-child { border-bottom: none; }
  .work-points li::before {
    content: '▸';
    position: absolute;
    left: 0;
    color: var(--accent1);
    font-size: 11px;
    top: 7px;
  }

  /* ── BOTTOM ROW ── */
  .bottom-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
    margin-bottom: 28px;
    animation: revealUp 0.6s cubic-bezier(0.16,1,0.3,1) 0.6s both;
  }
  .mini-glass {
    padding: 24px 24px;
    border-radius: 18px;
  }

  /* languages */
  .lang-item {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 14px;
  }
  .lang-item:last-child { margin-bottom: 0; }
  .lang-name {
    font-size: 13px;
    color: var(--text2);
    width: 72px;
    flex-shrink: 0;
    font-weight: 400;
  }
  .lang-track {
    flex: 1;
    height: 4px;
    background: rgba(139,43,226,0.12);
    border-radius: 4px;
    overflow: hidden;
  }
  .lang-fill {
    height: 100%;
    border-radius: 4px;
    background: linear-gradient(90deg, var(--accent1), var(--accent3));
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 1.2s cubic-bezier(0.4,0,0.2,1);
  }
  .lang-fill.animated { transform: scaleX(1); }
  .lang-pct {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    color: var(--text3);
    width: 30px;
    text-align: right;
    flex-shrink: 0;
  }

  /* goals */
  .goal-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    padding: 10px 0;
    border-bottom: 1px solid rgba(255,255,255,0.04);
    font-size: 13px;
    color: var(--text3);
    font-weight: 300;
    line-height: 1.5;
  }
  .goal-item:last-child { border-bottom: none; }
  .goal-icon { color: var(--accent1); font-size: 14px; flex-shrink: 0; margin-top: 1px; }

  /* ── CONTACT ── */
  .contact-wrap {
    animation: revealUp 0.6s cubic-bezier(0.16,1,0.3,1) 0.65s both;
  }
  .contact-card {
    padding: 36px;
    border-radius: 20px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .contact-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 50% 0%, rgba(139,43,226,0.12), transparent 60%);
    pointer-events: none;
  }
  .contact-headline {
    font-family: 'Clash Display', sans-serif;
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 8px;
    background: linear-gradient(135deg, #fff, var(--accent3));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .contact-sub {
    font-size: 13px;
    color: var(--text3);
    margin-bottom: 26px;
    font-weight: 300;
  }
  .contact-links {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 12px;
  }
  .contact-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 11px 22px;
    border-radius: 12px;
    border: 1px solid rgba(139,43,226,0.35);
    background: rgba(139,43,226,0.1);
    color: var(--accent3);
    font-size: 13px;
    font-weight: 500;
    font-family: 'Outfit', sans-serif;
    text-decoration: none;
    transition: all 0.25s;
  }
  .contact-btn:hover {
    background: rgba(139,43,226,0.25);
    border-color: var(--accent2);
    color: #fff;
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(139,43,226,0.25);
  }

  /* ── ACHIEVEMENTS ── */
  .ach-wrap {
    margin-bottom: 28px;
    animation: revealUp 0.6s cubic-bezier(0.16,1,0.3,1) 0.62s both;
  }
  .ach-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
  }
  .ach-item {
    padding: 18px 20px;
    border-radius: 14px;
    display: flex;
    align-items: center;
    gap: 14px;
  }
  .ach-icon { font-size: 26px; flex-shrink: 0; }
  .ach-title {
    font-family: 'Clash Display', sans-serif;
    font-size: 14px;
    font-weight: 600;
    color: var(--text1);
    margin-bottom: 2px;
  }
  .ach-detail {
    font-size: 11.5px;
    color: var(--text3);
    font-weight: 300;
  }

  /* ── ANIMATIONS ── */
  @keyframes revealDown {
    from { opacity: 0; transform: translateY(-20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes revealUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding-top: 16px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--text3);
    letter-spacing: 1px;
    animation: revealUp 0.6s 0.7s both;
  }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--p1); }
  ::-webkit-scrollbar-thumb { background: var(--accent1); border-radius: 3px; }

  /* ── RESPONSIVE ── */
  @media (max-width: 640px) {
    .hero { flex-direction: column; text-align: center; padding: 28px 24px; }
    .hero-chips { justify-content: center; }
    .status-row { justify-content: center; }
    .info-grid { grid-template-columns: 1fr 1fr; }
    .stats-row { grid-template-columns: 1fr 1fr; }
    .projects-grid { grid-template-columns: 1fr; }
    .bottom-row { grid-template-columns: 1fr; }
    .ach-grid { grid-template-columns: 1fr; }
    .avatar-shell { margin: 0 auto; }
  }
</style>
</head>
<body>

<!-- background -->
<div class="bg-scene">
  <div class="bg-grid"></div>
</div>

<div class="page">

  <!-- ── HERO ── -->
  <div class="hero glass">
    <div class="avatar-shell">
      <div class="avatar-ring-outer"></div>
      <div class="avatar-ring-inner"></div>
      <div class="avatar-core">JKG</div>
    </div>
    <div class="hero-text">
      <div class="hero-name">Janma K Gowda</div>
      <div class="hero-role">Full Stack Developer <span>//</span> ML Enthusiast <span>//</span> ISE · 2026</div>
      <div class="hero-chips">
        <span class="chip">React.js</span>
        <span class="chip">Python</span>
        <span class="chip">Machine Learning</span>
        <span class="chip">JavaScript</span>
        <span class="chip">AI</span>
        <span class="chip chip-green">⚡ Open to Work</span>
      </div>
      <div class="status-row">
        <div class="pulse"></div>
        Interning @ Inventeron Technologies · Mysuru, Karnataka
      </div>
    </div>
  </div>

  <!-- ── INFO CARDS ── -->
  <div class="info-grid">
    <div class="info-card glass">
      <span class="card-emoji">🎓</span>
      <div class="card-label">Education</div>
      <div class="card-title">B.E. – ISE</div>
      <div class="card-sub">MIT Mysuru · 2022–2026</div>
    </div>
    <div class="info-card glass">
      <span class="card-emoji">📍</span>
      <div class="card-label">Location</div>
      <div class="card-title">Mysuru</div>
      <div class="card-sub">Karnataka, India</div>
    </div>
    <div class="info-card glass">
      <span class="card-emoji">💼</span>
      <div class="card-label">Experience</div>
      <div class="card-title">Full Stack Intern</div>
      <div class="card-sub">Inventeron Technologies</div>
    </div>
    <div class="info-card glass">
      <span class="card-emoji">🤖</span>
      <div class="card-label">Focus Area</div>
      <div class="card-title">AI & Machine Learning</div>
      <div class="card-sub">AIML Certified · Tejas Pro</div>
    </div>
    <div class="info-card glass">
      <span class="card-emoji">🎂</span>
      <div class="card-label">Date of Birth</div>
      <div class="card-title">June 19, 2004</div>
      <div class="card-sub">Mysuru, Karnataka</div>
    </div>
    <div class="info-card glass">
      <span class="card-emoji">🌍</span>
      <div class="card-label">Community</div>
      <div class="card-title">NSS Volunteer</div>
      <div class="card-sub">Certified · Social Development</div>
    </div>
  </div>

  <!-- ── STATS ── -->
  <div class="stats-row">
    <div class="stat-card glass">
      <span class="stat-num">8.67</span>
      <div class="stat-label">CGPA</div>
    </div>
    <div class="stat-card glass">
      <span class="stat-num">2+</span>
      <div class="stat-label">Projects</div>
    </div>
    <div class="stat-card glass">
      <span class="stat-num">6</span>
      <div class="stat-label">Prog Langs</div>
    </div>
    <div class="stat-card glass">
      <span class="stat-num">94.4%</span>
      <div class="stat-label">10th Score</div>
    </div>
  </div>

  <!-- ── SKILLS ── -->
  <div class="skills-wrap">
    <div class="section-title">🛠 Tech Arsenal</div>
    <div class="skills-block glass">
      <div class="skill-group">
        <div class="skill-group-label">// Languages</div>
        <div class="skill-tags">
          <span class="skill-tag">C</span>
          <span class="skill-tag">Java</span>
          <span class="skill-tag">Python</span>
          <span class="skill-tag">JavaScript</span>
          <span class="skill-tag">HTML5</span>
          <span class="skill-tag">CSS3</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">// Frameworks & Tech</div>
        <div class="skill-tags">
          <span class="skill-tag">React.js</span>
          <span class="skill-tag">Node.js</span>
          <span class="skill-tag">REST APIs</span>
          <span class="skill-tag">Machine Learning</span>
          <span class="skill-tag">Data Analysis</span>
          <span class="skill-tag">Artificial Intelligence</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">// Tools & Platforms</div>
        <div class="skill-tags">
          <span class="skill-tag">VS Code</span>
          <span class="skill-tag">PyCharm</span>
          <span class="skill-tag">Jupyter Notebook</span>
          <span class="skill-tag">Git</span>
          <span class="skill-tag">GitHub</span>
        </div>
      </div>
    </div>
  </div>

  <!-- ── PROJECTS ── -->
  <div class="projects-wrap">
    <div class="section-title">🚀 Featured Projects</div>
    <div class="projects-grid">
      <div class="project-card glass">
        <div class="project-number">01</div>
        <span class="project-icon">🪑</span>
        <div class="project-name">Exam Seat Allotment System</div>
        <div class="project-desc">Designed and implemented a system that automates exam seat allocation by managing student data and hall capacity, generating accurate seating arrangements with minimal manual effort.</div>
        <div class="project-tags">
          <span class="project-tag">Python</span>
          <span class="project-tag">Automation</span>
          <span class="project-tag">Data Management</span>
        </div>
      </div>
      <div class="project-card glass">
        <div class="project-number">02</div>
        <span class="project-icon">🔤</span>
        <div class="project-name">Halegannada Script Recognition</div>
        <div class="project-desc">Built a machine learning model to recognize and classify ancient Halegannada script characters — involving dataset creation, preprocessing, and classification techniques to improve accuracy.</div>
        <div class="project-tags">
          <span class="project-tag">Python</span>
          <span class="project-tag">Scikit-Learn</span>
          <span class="project-tag">OpenCV</span>
          <span class="project-tag">ML</span>
        </div>
      </div>
    </div>
  </div>

  <!-- ── WORK EXPERIENCE ── -->
  <div class="work-wrap">
    <div class="section-title">💼 Work Experience</div>
    <div class="work-card glass">
      <div class="work-header">
        <div class="work-company">Inventeron Technologies</div>
        <div class="work-badge">● CURRENT</div>
      </div>
      <div class="work-role">Full Stack Developer Intern</div>
      <ul class="work-points">
        <li>Building responsive web applications using modern frontend and backend technologies</li>
        <li>Designing user interfaces and seamless user experiences with React.js</li>
        <li>Integrating RESTful APIs and managing server-side logic</li>
        <li>Gaining hands-on experience in full stack architecture and deployment workflows</li>
      </ul>
    </div>
  </div>

  <!-- ── ACHIEVEMENTS ── -->
  <div class="ach-wrap">
    <div class="section-title">🏆 Achievements & Certifications</div>
    <div class="ach-grid">
      <div class="ach-item glass">
        <span class="ach-icon">🤖</span>
        <div>
          <div class="ach-title">AIML Training</div>
          <div class="ach-detail">Tejas Pro — Hands-on ML & practical implementations</div>
        </div>
      </div>
      <div class="ach-item glass">
        <span class="ach-icon">🌍</span>
        <div>
          <div class="ach-title">NSS Volunteer</div>
          <div class="ach-detail">Certified for community & social development</div>
        </div>
      </div>
      <div class="ach-item glass">
        <span class="ach-icon">🎓</span>
        <div>
          <div class="ach-title">Academic Excellence</div>
          <div class="ach-detail">CGPA 8.67 / 10.0 in B.E. ISE</div>
        </div>
      </div>
      <div class="ach-item glass">
        <span class="ach-icon">📚</span>
        <div>
          <div class="ach-title">High School Topper</div>
          <div class="ach-detail">94.4% in 10th State Board Examinations</div>
        </div>
      </div>
    </div>
  </div>

  <!-- ── BOTTOM ROW ── -->
  <div class="bottom-row">
    <div class="mini-glass glass">
      <div class="section-title">🗣 Languages Spoken</div>
      <div class="lang-item">
        <span class="lang-name">Kannada</span>
        <div class="lang-track"><div class="lang-fill" data-w="1"></div></div>
        <span class="lang-pct">Native</span>
      </div>
      <div class="lang-item">
        <span class="lang-name">English</span>
        <div class="lang-track"><div class="lang-fill" data-w="0.9"></div></div>
        <span class="lang-pct">Fluent</span>
      </div>
      <div class="lang-item">
        <span class="lang-name">Hindi</span>
        <div class="lang-track"><div class="lang-fill" data-w="0.7"></div></div>
        <span class="lang-pct">Good</span>
      </div>
    </div>

    <div class="mini-glass glass">
      <div class="section-title">🚀 Currently Pursuing</div>
      <div class="goal-item">
        <span class="goal-icon">▸</span>
        Building responsive web apps with React.js & modern stack
      </div>
      <div class="goal-item">
        <span class="goal-icon">▸</span>
        Exploring AI & ML through real-world projects
      </div>
      <div class="goal-item">
        <span class="goal-icon">▸</span>
        Seeking full-time SWE / ML roles for 2026
      </div>
    </div>
  </div>

  <!-- ── CONTACT ── -->
  <div class="contact-wrap">
    <div class="contact-card glass">
      <div class="contact-headline">Let's Connect ✨</div>
      <div class="contact-sub">Open to opportunities, collaborations & exciting projects</div>
      <div class="contact-links">
        <a class="contact-btn" href="mailto:janmakgowda19@gmail.com">📧 janmakgowda19@gmail.com</a>
        <a class="contact-btn" href="https://linkedin.com/in/janmakgowda" target="_blank">🔗 LinkedIn</a>
        <a class="contact-btn" href="https://github.com/janmakgowda" target="_blank">🐙 GitHub</a>
        <a class="contact-btn" href="#">📍 Mysuru, Karnataka</a>
      </div>
    </div>
  </div>

  <div class="footer">
    crafted with 💜 by janma k gowda · 2026
  </div>

</div>

<script>
  // ── PARTICLES ──
  const scene = document.querySelector('.bg-scene');
  const colors = ['rgba(139,43,226,0.5)','rgba(180,100,255,0.4)','rgba(80,0,140,0.5)','rgba(200,150,255,0.3)'];
  for (let i = 0; i < 28; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    const size = Math.random() * 4 + 2;
    p.style.cssText = `
      width:${size}px; height:${size}px;
      left:${Math.random()*100}%;
      background:${colors[Math.floor(Math.random()*colors.length)]};
      animation-duration:${Math.random()*18+12}s;
      animation-delay:${Math.random()*10}s;
    `;
    scene.appendChild(p);
  }

  // ── LANG BARS ──
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        document.querySelectorAll('.lang-fill').forEach(bar => {
          const w = parseFloat(bar.dataset.w);
          setTimeout(() => {
            bar.style.transform = `scaleX(${w})`;
          }, 200);
        });
        observer.disconnect();
      }
    });
  }, { threshold: 0.3 });

  const langSection = document.querySelector('.lang-track');
  if (langSection) observer.observe(langSection);
</script>
</body>
</html>
