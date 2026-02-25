<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mustafeez Shaikh — Web Dev · Data Science · Gen AI</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #050810;
    --surface: #0c1120;
    --surface2: #111827;
    --cyan: #00f5ff;
    --cyan-dim: rgba(0,245,255,0.12);
    --cyan-glow: rgba(0,245,255,0.35);
    --white: #f0f6ff;
    --muted: #6b7a99;
    --accent: #7c3aed;
    --accent-dim: rgba(124,58,237,0.15);
    --border: rgba(0,245,255,0.1);
    /* Domain colors */
    --web: #00f5ff;
    --web-dim: rgba(0,245,255,0.1);
    --ds: #f97316;
    --ds-dim: rgba(249,115,22,0.1);
    --ai: #a855f7;
    --ai-dim: rgba(168,85,247,0.1);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--white);
    font-family: 'Space Mono', monospace;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed; top: 0; left: 0;
    width: 12px; height: 12px;
    background: var(--cyan);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%,-50%);
    transition: transform 0.1s, width 0.2s, height 0.2s;
    mix-blend-mode: difference;
  }
  .cursor-ring {
    position: fixed; top: 0; left: 0;
    width: 36px; height: 36px;
    border: 1px solid var(--cyan);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%,-50%);
    transition: transform 0.15s ease, width 0.2s, height 0.2s, border-color 0.2s;
    opacity: 0.5;
  }

  /* Grid bg */
  body::before {
    content:'';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(0,245,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,245,255,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    z-index: 0;
    pointer-events: none;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 20px 60px;
    background: rgba(5,8,16,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800; font-size: 1.1rem;
    color: var(--cyan);
    letter-spacing: 0.05em;
  }
  .nav-logo span { color: var(--white); }
  .nav-links { display: flex; gap: 32px; list-style: none; }
  .nav-links a {
    color: var(--muted); text-decoration: none;
    font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase;
    transition: color 0.2s;
    position: relative;
  }
  .nav-links a::after {
    content: '';
    position: absolute; bottom: -4px; left: 0; right: 0;
    height: 1px; background: var(--cyan);
    transform: scaleX(0); transform-origin: left;
    transition: transform 0.3s;
  }
  .nav-links a:hover { color: var(--cyan); }
  .nav-links a:hover::after { transform: scaleX(1); }

  /* SECTIONS */
  section { position: relative; z-index: 1; }

  /* HERO */
  #hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center; align-items: center;
    text-align: center;
    padding: 120px 24px 80px;
    overflow: hidden;
  }
  .hero-glow {
    position: absolute;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(0,245,255,0.08) 0%, transparent 70%);
    border-radius: 50%;
    animation: pulse 4s ease-in-out infinite alternate;
  }
  @keyframes pulse {
    from { transform: scale(0.9); opacity: 0.6; }
    to { transform: scale(1.1); opacity: 1; }
  }
  .hero-tag {
    font-size: 0.7rem; letter-spacing: 0.25em; text-transform: uppercase;
    color: var(--cyan); background: var(--cyan-dim);
    border: 1px solid var(--border);
    padding: 6px 16px; border-radius: 2px;
    margin-bottom: 28px;
    animation: fadeUp 0.6s ease both;
  }
  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(3rem, 8vw, 7rem);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.02em;
    animation: fadeUp 0.7s 0.1s ease both;
  }
  .hero-name .line1 { display: block; color: var(--white); }
  .hero-name .line2 {
    display: block;
    background: linear-gradient(135deg, var(--cyan), var(--accent));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-sub {
    margin-top: 24px; max-width: 520px;
    color: var(--muted); font-size: 0.85rem; line-height: 1.8;
    animation: fadeUp 0.7s 0.2s ease both;
  }
  .hero-ctas {
    margin-top: 40px; display: flex; gap: 16px;
    animation: fadeUp 0.7s 0.3s ease both;
    flex-wrap: wrap; justify-content: center;
  }
  .btn-primary {
    padding: 14px 32px;
    background: var(--cyan);
    color: var(--bg);
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem; font-weight: 700;
    letter-spacing: 0.1em; text-transform: uppercase;
    text-decoration: none;
    border: none; cursor: none;
    clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 0 30px var(--cyan-glow);
  }
  .btn-outline {
    padding: 14px 32px;
    background: transparent;
    color: var(--cyan);
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem; font-weight: 700;
    letter-spacing: 0.1em; text-transform: uppercase;
    text-decoration: none;
    border: 1px solid var(--cyan);
    cursor: none;
    clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
    transition: background 0.2s, transform 0.2s;
  }
  .btn-outline:hover { background: var(--cyan-dim); transform: translateY(-2px); }

  /* scroll indicator */
  .scroll-hint {
    position: absolute; bottom: 36px; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    animation: fadeUp 0.7s 0.5s ease both;
  }
  .scroll-hint span { font-size: 0.6rem; letter-spacing: 0.2em; color: var(--muted); text-transform: uppercase; }
  .scroll-line {
    width: 1px; height: 50px;
    background: linear-gradient(to bottom, var(--cyan), transparent);
    animation: scrollLine 1.5s ease-in-out infinite;
  }
  @keyframes scrollLine {
    0% { transform: scaleY(0); transform-origin: top; }
    50% { transform: scaleY(1); transform-origin: top; }
    51% { transform: scaleY(1); transform-origin: bottom; }
    100% { transform: scaleY(0); transform-origin: bottom; }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* SECTION COMMON */
  .section-inner {
    max-width: 1100px; margin: 0 auto;
    padding: 100px 24px;
  }
  .section-label {
    font-size: 0.65rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--cyan); margin-bottom: 12px;
  }
  .section-label::before { content: '// '; }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(1.8rem, 4vw, 3rem);
    font-weight: 800; line-height: 1.1;
    margin-bottom: 60px;
  }
  .section-title .accent { color: var(--cyan); }

  /* ABOUT */
  #about { background: var(--surface); }
  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center;
  }
  .about-text p {
    color: var(--muted); line-height: 1.9; font-size: 0.85rem; margin-bottom: 16px;
  }
  .about-text .quote {
    margin-top: 32px; padding: 20px 24px;
    border-left: 2px solid var(--cyan);
    background: var(--cyan-dim);
    font-style: italic; font-size: 0.8rem; color: var(--white);
    line-height: 1.7;
  }
  .about-stats {
    display: grid; grid-template-columns: 1fr 1fr; gap: 20px;
  }
  .stat-card {
    padding: 28px 24px;
    background: var(--bg);
    border: 1px solid var(--border);
    position: relative; overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
  }
  .stat-card::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--cyan), transparent);
  }
  .stat-card:hover { border-color: var(--cyan); transform: translateY(-4px); }
  .stat-num {
    font-family: 'Syne', sans-serif; font-size: 2.5rem; font-weight: 800;
    color: var(--cyan); line-height: 1;
  }
  .stat-label { font-size: 0.7rem; color: var(--muted); margin-top: 8px; letter-spacing: 0.05em; }

  /* PROJECTS */
  #projects { background: var(--bg); }
  .projects-grid {
    display: grid; grid-template-columns: repeat(2, 1fr); gap: 24px;
  }
  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 36px 32px;
    position: relative; overflow: hidden;
    text-decoration: none; color: inherit;
    display: block;
    transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
    group: true;
  }
  .project-card::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, var(--cyan-dim), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .project-card:hover::before { opacity: 1; }
  .project-card:hover {
    transform: translateY(-6px);
    border-color: var(--cyan);
    box-shadow: 0 20px 60px rgba(0,245,255,0.08);
  }
  .project-icon { font-size: 2rem; margin-bottom: 20px; }
  .project-title {
    font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1.15rem;
    margin-bottom: 12px;
  }
  .project-desc { color: var(--muted); font-size: 0.78rem; line-height: 1.7; margin-bottom: 24px; }
  .project-tags { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 24px; }
  .tag {
    padding: 4px 10px; font-size: 0.65rem; letter-spacing: 0.08em;
    background: var(--bg); border: 1px solid var(--border);
    color: var(--cyan); text-transform: uppercase;
  }
  .project-link {
    font-size: 0.7rem; letter-spacing: 0.1em; text-transform: uppercase;
    color: var(--cyan); text-decoration: none;
    display: inline-flex; align-items: center; gap: 8px;
    transition: gap 0.2s;
  }
  .project-link:hover { gap: 14px; }
  .project-link::after { content: '→'; }

  /* TECH STACK */
  #stack { background: var(--surface); }
  .stack-grid {
    display: flex; flex-wrap: wrap; gap: 12px;
  }
  .tech-pill {
    display: flex; align-items: center; gap: 10px;
    padding: 10px 18px;
    background: var(--bg);
    border: 1px solid var(--border);
    font-size: 0.75rem; letter-spacing: 0.05em;
    color: var(--muted);
    transition: border-color 0.2s, color 0.2s, transform 0.2s;
    position: relative; overflow: hidden;
  }
  .tech-pill::before {
    content: ''; position: absolute; left: 0; top: 0; bottom: 0;
    width: 2px; background: var(--cyan);
    transform: scaleY(0); transform-origin: bottom;
    transition: transform 0.3s;
  }
  .tech-pill:hover { border-color: var(--cyan); color: var(--white); transform: translateY(-2px); }
  .tech-pill:hover::before { transform: scaleY(1); }
  .tech-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--cyan); flex-shrink: 0; }

  /* CONNECT */
  #connect { background: var(--bg); }
  .connect-inner { max-width: 700px; }
  .connect-links { display: flex; flex-wrap: wrap; gap: 16px; margin-top: 40px; }
  .connect-card {
    flex: 1; min-width: 180px;
    padding: 28px 24px;
    background: var(--surface);
    border: 1px solid var(--border);
    text-decoration: none; color: var(--white);
    display: flex; flex-direction: column; gap: 12px;
    transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
    position: relative; overflow: hidden;
  }
  .connect-card::after {
    content: ''; position: absolute; bottom: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--cyan), var(--accent));
    transform: scaleX(0); transform-origin: left; transition: transform 0.3s;
  }
  .connect-card:hover { border-color: var(--cyan); transform: translateY(-4px); box-shadow: 0 16px 40px rgba(0,245,255,0.06); }
  .connect-card:hover::after { transform: scaleX(1); }
  .connect-icon { font-size: 1.5rem; }
  .connect-platform { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 0.95rem; }
  .connect-handle { font-size: 0.7rem; color: var(--muted); }

  /* FOOTER */
  footer {
    position: relative; z-index: 1;
    border-top: 1px solid var(--border);
    padding: 40px 60px;
    display: flex; align-items: center; justify-content: space-between;
    background: var(--surface);
  }
  footer p { font-size: 0.7rem; color: var(--muted); }
  .footer-status {
    display: flex; align-items: center; gap: 8px;
    font-size: 0.7rem; color: var(--muted);
  }
  .status-dot {
    width: 8px; height: 8px; border-radius: 50%; background: #22c55e;
    box-shadow: 0 0 8px #22c55e;
    animation: blink 2s ease-in-out infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.4} }

  /* REVEAL ANIMATION */
  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* EXPERTISE / DOMAINS */
  #expertise { background: var(--bg); }
  .domains-grid {
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px;
  }
  .domain-card {
    padding: 44px 32px;
    border: 1px solid var(--border);
    position: relative; overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
  }
  .domain-card:hover { transform: translateY(-6px); }
  .domain-card::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px;
  }
  .domain-card.web { background: linear-gradient(160deg, rgba(0,245,255,0.05), var(--surface)); }
  .domain-card.web::before { background: var(--web); box-shadow: 0 0 20px var(--web); }
  .domain-card.web:hover { box-shadow: 0 20px 60px rgba(0,245,255,0.1); border-color: var(--web); }
  .domain-card.ds { background: linear-gradient(160deg, rgba(249,115,22,0.05), var(--surface)); }
  .domain-card.ds::before { background: var(--ds); box-shadow: 0 0 20px var(--ds); }
  .domain-card.ds:hover { box-shadow: 0 20px 60px rgba(249,115,22,0.1); border-color: var(--ds); }
  .domain-card.ai { background: linear-gradient(160deg, rgba(168,85,247,0.05), var(--surface)); }
  .domain-card.ai::before { background: var(--ai); box-shadow: 0 0 20px var(--ai); }
  .domain-card.ai:hover { box-shadow: 0 20px 60px rgba(168,85,247,0.1); border-color: var(--ai); }

  .domain-icon { font-size: 2.5rem; margin-bottom: 20px; display: block; }
  .domain-title {
    font-family: 'Syne', sans-serif; font-weight: 800; font-size: 1.2rem;
    margin-bottom: 12px;
  }
  .domain-card.web .domain-title { color: var(--web); }
  .domain-card.ds .domain-title { color: var(--ds); }
  .domain-card.ai .domain-title { color: var(--ai); }
  .domain-desc { color: var(--muted); font-size: 0.78rem; line-height: 1.8; margin-bottom: 24px; }
  .domain-skills { display: flex; flex-wrap: wrap; gap: 8px; }
  .domain-skill {
    padding: 4px 10px; font-size: 0.62rem; letter-spacing: 0.08em; text-transform: uppercase;
    border: 1px solid;
  }
  .domain-card.web .domain-skill { border-color: rgba(0,245,255,0.3); color: var(--web); background: var(--web-dim); }
  .domain-card.ds .domain-skill { border-color: rgba(249,115,22,0.3); color: var(--ds); background: var(--ds-dim); }
  .domain-card.ai .domain-skill { border-color: rgba(168,85,247,0.3); color: var(--ai); background: var(--ai-dim); }

  /* Domain badge on project cards */
  .project-badge {
    display: inline-block;
    font-size: 0.6rem; letter-spacing: 0.12em; text-transform: uppercase;
    padding: 3px 9px; margin-bottom: 16px;
    border: 1px solid;
    font-weight: 700;
  }
  .badge-web { border-color: var(--web); color: var(--web); background: var(--web-dim); }
  .badge-ds { border-color: var(--ds); color: var(--ds); background: var(--ds-dim); }
  .badge-ai { border-color: var(--ai); color: var(--ai); background: var(--ai-dim); }

  /* Stack categories */
  .stack-categories { display: flex; flex-direction: column; gap: 40px; }
  .stack-category-title {
    font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
    margin-bottom: 16px; padding-bottom: 8px;
    border-bottom: 1px solid var(--border);
  }
  .stack-category-title.web { color: var(--web); border-color: rgba(0,245,255,0.2); }
  .stack-category-title.ds { color: var(--ds); border-color: rgba(249,115,22,0.2); }
  .stack-category-title.ai { color: var(--ai); border-color: rgba(168,85,247,0.2); }
  .stack-category-title.devops { color: var(--muted); }

  .tech-pill.ds-pill { --pill-color: var(--ds); }
  .tech-pill.ai-pill { --pill-color: var(--ai); }
  .tech-pill.web-pill { --pill-color: var(--web); }
  .tech-pill { --pill-color: var(--muted); }

  .tech-pill.web-pill .tech-dot { background: var(--web); }
  .tech-pill.ds-pill .tech-dot { background: var(--ds); }
  .tech-pill.ai-pill .tech-dot { background: var(--ai); }

  .tech-pill.web-pill:hover { border-color: var(--web); color: var(--white); }
  .tech-pill.web-pill:hover::before { transform: scaleY(1); background: var(--web); }
  .tech-pill.ds-pill:hover { border-color: var(--ds); color: var(--white); }
  .tech-pill.ds-pill::before { background: var(--ds); }
  .tech-pill.ds-pill:hover::before { transform: scaleY(1); }
  .tech-pill.ai-pill:hover { border-color: var(--ai); color: var(--white); }
  .tech-pill.ai-pill::before { background: var(--ai); }
  .tech-pill.ai-pill:hover::before { transform: scaleY(1); }

  /* Hero typing roles */
  .hero-roles {
    display: flex; gap: 12px; justify-content: center; flex-wrap: wrap;
    margin-top: 20px; margin-bottom: 4px;
    animation: fadeUp 0.7s 0.15s ease both;
  }
  .role-badge {
    font-size: 0.68rem; letter-spacing: 0.12em; text-transform: uppercase;
    padding: 6px 14px; border: 1px solid; font-weight: 700;
  }
  .role-badge.web { border-color: var(--web); color: var(--web); background: var(--web-dim); }
  .role-badge.ds { border-color: var(--ds); color: var(--ds); background: var(--ds-dim); }
  .role-badge.ai { border-color: var(--ai); color: var(--ai); background: var(--ai-dim); }

  @media (max-width: 768px) {
    nav { padding: 16px 24px; }
    .nav-links { display: none; }
    .about-grid { grid-template-columns: 1fr; }
    .about-stats { grid-template-columns: 1fr 1fr; }
    .projects-grid { grid-template-columns: 1fr; }
    .domains-grid { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 12px; text-align: center; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<nav>
  <div class="nav-logo">MS<span>.</span></div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#expertise">Expertise</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#stack">Stack</a></li>
    <li><a href="#connect">Connect</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-glow"></div>
  <div class="hero-tag">Available for opportunities</div>
  <h1 class="hero-name">
    <span class="line1">Mustafeez</span>
    <span class="line2">Shaikh</span>
  </h1>
  <p class="hero-sub">
    CSE Student at the intersection of <strong style="color:var(--web)">Web Development</strong>, <strong style="color:var(--ds)">Data Science</strong> &amp; <strong style="color:var(--ai)">Generative AI</strong>.<br/>
    Building intelligent, scalable applications that solve real-world problems.
  </p>
  <div class="hero-roles">
    <span class="role-badge web">⚡ Web Dev</span>
    <span class="role-badge ds">📊 Data Science</span>
    <span class="role-badge ai">🤖 Gen AI</span>
  </div>
  <div class="hero-ctas">
    <a href="#projects" class="btn-primary">View Projects</a>
    <a href="#connect" class="btn-outline">Get in Touch</a>
  </div>
  <div class="scroll-hint">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-inner">
    <p class="section-label reveal">About</p>
    <h2 class="section-title reveal">Who I <span class="accent">Am.</span></h2>
    <div class="about-grid">
      <div class="about-text reveal">
        <p>I'm <strong style="color:var(--white)">Mustafeez Shaikh</strong>, a Computer Science Engineering student working at the intersection of <span style="color:var(--web)">Web Development</span>, <span style="color:var(--ds)">Data Science</span>, and <span style="color:var(--ai)">Generative AI</span>.</p>
        <p>I build scalable, responsive web applications, analyze data to uncover meaningful insights, and experiment with large language models and AI-powered tools to create the next generation of intelligent experiences.</p>
        <p style="color:var(--muted);font-size:0.78rem;line-height:1.8;">Focused on clean code, continuous learning, and turning real-world problems into elegant digital solutions.</p>
        <div class="quote">"Dream big. Code bigger."</div>
      </div>
      <div class="about-stats reveal">
        <div class="stat-card">
          <div class="stat-num">4+</div>
          <div class="stat-label">Projects Shipped</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">5+</div>
          <div class="stat-label">Technologies Mastered</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">∞</div>
          <div class="stat-label">Curiosity Level</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">CSE</div>
          <div class="stat-label">Engineering Student</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EXPERTISE -->
<section id="expertise">
  <div class="section-inner">
    <p class="section-label reveal">Domains</p>
    <h2 class="section-title reveal">Areas of <span class="accent">Expertise.</span></h2>
    <div class="domains-grid">

      <div class="domain-card web reveal">
        <span class="domain-icon">⚡</span>
        <div class="domain-title">Web Development</div>
        <p class="domain-desc">Crafting fast, responsive, and visually polished web experiences — from landing pages to full-stack applications with modern frameworks and clean architecture.</p>
        <div class="domain-skills">
          <span class="domain-skill">React</span>
          <span class="domain-skill">Node.js</span>
          <span class="domain-skill">MongoDB</span>
          <span class="domain-skill">Express</span>
          <span class="domain-skill">REST APIs</span>
          <span class="domain-skill">Responsive UI</span>
        </div>
      </div>

      <div class="domain-card ds reveal">
        <span class="domain-icon">📊</span>
        <div class="domain-title">Data Science</div>
        <p class="domain-desc">Exploring datasets to uncover hidden patterns, building predictive models, and translating raw numbers into actionable visual stories using Python and ML tools.</p>
        <div class="domain-skills">
          <span class="domain-skill">Python</span>
          <span class="domain-skill">Pandas</span>
          <span class="domain-skill">NumPy</span>
          <span class="domain-skill">Matplotlib</span>
          <span class="domain-skill">Scikit-Learn</span>
          <span class="domain-skill">EDA</span>
        </div>
      </div>

      <div class="domain-card ai reveal">
        <span class="domain-icon">🤖</span>
        <div class="domain-title">Generative AI</div>
        <p class="domain-desc">Building AI-powered applications using LLMs, prompt engineering, and OCR pipelines. Exploring the creative frontier of machine intelligence to solve practical problems.</p>
        <div class="domain-skills">
          <span class="domain-skill">LLMs</span>
          <span class="domain-skill">Prompt Eng.</span>
          <span class="domain-skill">Streamlit</span>
          <span class="domain-skill">OCR</span>
          <span class="domain-skill">RAG</span>
          <span class="domain-skill">AI Apps</span>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-inner">
    <p class="section-label reveal">Work</p>
    <h2 class="section-title reveal">Featured <span class="accent">Projects.</span></h2>
    <div class="projects-grid">

      <a class="project-card reveal" href="https://github.com/Musa-04/Ecommerce" target="_blank">
        <span class="project-badge badge-web">Web Dev</span>
        <div class="project-icon">🛍</div>
        <div class="project-title">E-Commerce Website</div>
        <p class="project-desc">Fully responsive e-commerce UI with clean layout and smooth animations. Designed for seamless product browsing and user experience.</p>
        <div class="project-tags">
          <span class="tag">HTML</span>
          <span class="tag">CSS</span>
          <span class="tag">JavaScript</span>
        </div>
        <span class="project-link">View on GitHub</span>
      </a>

      <a class="project-card reveal" href="https://github.com/Musa-04/quiz-app" target="_blank">
        <span class="project-badge badge-web">Web Dev</span>
        <div class="project-icon">🧠</div>
        <div class="project-title">Quiz App</div>
        <p class="project-desc">Interactive quiz application with dynamic score tracking, answer validation, and a clean result summary screen.</p>
        <div class="project-tags">
          <span class="tag">HTML</span>
          <span class="tag">CSS</span>
          <span class="tag">JavaScript</span>
        </div>
        <span class="project-link">View on GitHub</span>
      </a>

      <a class="project-card reveal" href="https://github.com/Musa-04/Modern_login_page" target="_blank">
        <span class="project-badge badge-web">Web Dev</span>
        <div class="project-icon">🔐</div>
        <div class="project-title">Modern Login Page</div>
        <p class="project-desc">Stylish authentication UI with smooth form validation, glassmorphism design elements, and pixel-perfect styling.</p>
        <div class="project-tags">
          <span class="tag">HTML</span>
          <span class="tag">CSS</span>
        </div>
        <span class="project-link">View on GitHub</span>
      </a>

      <a class="project-card reveal" href="https://github.com/Musa-04/Textify" target="_blank">
        <span class="project-badge badge-ai">Gen AI</span>
        <div class="project-icon">🤖</div>
        <div class="project-title">Textify — AI OCR Tool</div>
        <p class="project-desc">AI-powered OCR web app that extracts text from uploaded images instantly. Built with Python and deployed via Streamlit.</p>
        <div class="project-tags">
          <span class="tag">Python</span>
          <span class="tag">OCR</span>
          <span class="tag">Streamlit</span>
        </div>
        <span class="project-link">View on GitHub</span>
      </a>

    </div>
  </div>
</section>

<!-- STACK -->
<section id="stack">
  <div class="section-inner">
    <p class="section-label reveal">Tools</p>
    <h2 class="section-title reveal">Tech <span class="accent">Stack.</span></h2>
    <div class="stack-categories">

      <div class="reveal">
        <div class="stack-category-title web">⚡ Web Development</div>
        <div class="stack-grid">
          <div class="tech-pill web-pill"><span class="tech-dot"></span>HTML5</div>
          <div class="tech-pill web-pill"><span class="tech-dot"></span>CSS3</div>
          <div class="tech-pill web-pill"><span class="tech-dot"></span>JavaScript</div>
          <div class="tech-pill web-pill"><span class="tech-dot"></span>React</div>
          <div class="tech-pill web-pill"><span class="tech-dot"></span>Node.js</div>
          <div class="tech-pill web-pill"><span class="tech-dot"></span>Express.js</div>
          <div class="tech-pill web-pill"><span class="tech-dot"></span>MongoDB</div>
          <div class="tech-pill web-pill"><span class="tech-dot"></span>REST APIs</div>
        </div>
      </div>

      <div class="reveal">
        <div class="stack-category-title ds">📊 Data Science</div>
        <div class="stack-grid">
          <div class="tech-pill ds-pill"><span class="tech-dot"></span>Python</div>
          <div class="tech-pill ds-pill"><span class="tech-dot"></span>Pandas</div>
          <div class="tech-pill ds-pill"><span class="tech-dot"></span>NumPy</div>
          <div class="tech-pill ds-pill"><span class="tech-dot"></span>Matplotlib</div>
          <div class="tech-pill ds-pill"><span class="tech-dot"></span>Seaborn</div>
          <div class="tech-pill ds-pill"><span class="tech-dot"></span>Scikit-Learn</div>
          <div class="tech-pill ds-pill"><span class="tech-dot"></span>Jupyter</div>
        </div>
      </div>

      <div class="reveal">
        <div class="stack-category-title ai">🤖 Generative AI</div>
        <div class="stack-grid">
          <div class="tech-pill ai-pill"><span class="tech-dot"></span>LLMs</div>
          <div class="tech-pill ai-pill"><span class="tech-dot"></span>Prompt Engineering</div>
          <div class="tech-pill ai-pill"><span class="tech-dot"></span>Streamlit</div>
          <div class="tech-pill ai-pill"><span class="tech-dot"></span>OCR (Tesseract)</div>
          <div class="tech-pill ai-pill"><span class="tech-dot"></span>RAG Pipelines</div>
          <div class="tech-pill ai-pill"><span class="tech-dot"></span>LangChain</div>
        </div>
      </div>

      <div class="reveal">
        <div class="stack-category-title devops">⚙️ DevOps & Tools</div>
        <div class="stack-grid">
          <div class="tech-pill"><span class="tech-dot"></span>Git</div>
          <div class="tech-pill"><span class="tech-dot"></span>GitHub</div>
          <div class="tech-pill"><span class="tech-dot"></span>Docker</div>
          <div class="tech-pill"><span class="tech-dot"></span>Linux</div>
          <div class="tech-pill"><span class="tech-dot"></span>VS Code</div>
          <div class="tech-pill"><span class="tech-dot"></span>Figma</div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- CONNECT -->
<section id="connect">
  <div class="section-inner">
    <p class="section-label reveal">Contact</p>
    <h2 class="section-title reveal">Let's <span class="accent">Connect.</span></h2>
    <div class="connect-inner">
      <p class="reveal" style="color: var(--muted); font-size: 0.85rem; line-height: 1.8;">
        I'm always open to new opportunities, collaborations, and conversations. Whether you have a project idea or just want to say hi — reach out!
      </p>
      <div class="connect-links reveal">
        <a href="https://www.linkedin.com/in/mustafeez-shaikh-50b786306" target="_blank" class="connect-card">
          <div class="connect-icon">💼</div>
          <div class="connect-platform">LinkedIn</div>
          <div class="connect-handle">mustafeez-shaikh</div>
        </a>
        <a href="mailto:mustafeezshaikh@gmail.com" class="connect-card">
          <div class="connect-icon">📧</div>
          <div class="connect-platform">Gmail</div>
          <div class="connect-handle">mustafeezshaikh@gmail.com</div>
        </a>
        <a href="https://www.instagram.com/musa_shaikh_0404" target="_blank" class="connect-card">
          <div class="connect-icon">📸</div>
          <div class="connect-platform">Instagram</div>
          <div class="connect-handle">@musa_shaikh_0404</div>
        </a>
        <a href="https://github.com/Musa-04" target="_blank" class="connect-card">
          <div class="connect-icon">⌨️</div>
          <div class="connect-platform">GitHub</div>
          <div class="connect-handle">Musa-04</div>
        </a>
      </div>
    </div>
  </div>
</section>

<footer>
  <p>© 2025 Mustafeez Shaikh. Built with ♥ and lots of ☕</p>
  <div class="footer-status">
    <div class="status-dot"></div>
    <span>Open to opportunities</span>
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let rx = 0, ry = 0, mx = 0, my = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
  });
  function animateRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  document.querySelectorAll('a, button, .project-card, .connect-card, .stat-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.width = '20px'; cursor.style.height = '20px';
      ring.style.width = '54px'; ring.style.height = '54px';
      ring.style.borderColor = 'rgba(0,245,255,0.8)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.width = '12px'; cursor.style.height = '12px';
      ring.style.width = '36px'; ring.style.height = '36px';
      ring.style.borderColor = 'rgba(0,245,255,0.5)';
    });
  });

  // Reveal on scroll
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
add some knowledge and re design this
