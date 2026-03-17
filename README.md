<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Muhammad Javed — AI & Data Science</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #07070f;
    --bg2: #0d0d1a;
    --bg3: #111122;
    --border: rgba(255,255,255,0.07);
    --border2: rgba(255,255,255,0.13);
    --purple: #6157f6;
    --purple-dim: rgba(97,87,246,0.15);
    --green: #1dbb85;
    --green-dim: rgba(29,187,133,0.12);
    --text: #e8e4f0;
    --muted: #7a778f;
    --mono: 'DM Mono', monospace;
    --sans: 'Syne', sans-serif;
    --serif: 'Instrument Serif', serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    overflow-x: hidden;
    cursor: none;
  }

  /* CUSTOM CURSOR */
  .cursor {
    position: fixed; top: 0; left: 0; z-index: 9999;
    pointer-events: none;
  }
  .cursor-dot {
    width: 8px; height: 8px;
    background: var(--purple);
    border-radius: 50%;
    transform: translate(-50%, -50%);
    transition: transform 0.1s;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid rgba(97,87,246,0.5);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    transform: translate(-50%, -50%);
    transition: transform 0.12s ease, width 0.2s, height 0.2s, border-color 0.2s;
    pointer-events: none; z-index: 9998;
  }
  .cursor-ring.hover { width: 56px; height: 56px; border-color: var(--green); }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.4rem 3rem;
    backdrop-filter: blur(18px);
    background: rgba(7,7,15,0.85);
    border-bottom: 1px solid var(--border);
    transition: padding 0.3s;
  }
  .nav-logo {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--green);
    letter-spacing: 0.1em;
  }
  .nav-links { display: flex; gap: 2.5rem; }
  .nav-links a {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--text); }

  /* NOISE OVERLAY */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 0; opacity: 0.4;
  }

  /* SECTIONS */
  section { position: relative; z-index: 1; }

  /* ── HERO ── */
  #hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 8rem 3rem 5rem;
    max-width: 1200px; margin: 0 auto;
    position: relative;
  }

  .hero-grid {
    display: grid;
    grid-template-columns: 1fr 380px;
    gap: 4rem;
    align-items: center;
    width: 100%;
  }

  /* Ambient blobs */
  .blob {
    position: absolute;
    border-radius: 50%;
    filter: blur(90px);
    pointer-events: none;
  }
  .blob-1 {
    width: 500px; height: 500px;
    background: rgba(97,87,246,0.12);
    top: -100px; right: -100px;
  }
  .blob-2 {
    width: 300px; height: 300px;
    background: rgba(29,187,133,0.08);
    bottom: 0; left: -50px;
  }

  .hero-tag {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--green);
    display: inline-flex; align-items: center; gap: 8px;
    margin-bottom: 1.8rem;
  }
  .hero-tag::before {
    content: '';
    display: inline-block;
    width: 24px; height: 1px;
    background: var(--green);
  }

  .hero-name {
    font-size: clamp(3.5rem, 7vw, 6rem);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.03em;
    margin-bottom: 1.2rem;
  }
  .hero-name em {
    font-family: var(--serif);
    font-style: italic;
    color: var(--purple);
    font-weight: 400;
  }

  .hero-desc {
    font-size: 15px;
    line-height: 1.8;
    color: var(--muted);
    max-width: 480px;
    margin-bottom: 2.5rem;
    font-weight: 400;
  }
  .hero-desc strong { color: var(--text); font-weight: 600; }

  .hero-cta {
    display: flex; gap: 1rem; flex-wrap: wrap;
  }

  .btn {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 0.75rem 1.8rem;
    border-radius: 2px;
    text-decoration: none;
    transition: all 0.2s;
    cursor: none;
  }
  .btn-primary {
    background: var(--purple);
    color: #fff;
    border: 1px solid var(--purple);
  }
  .btn-primary:hover { background: transparent; color: var(--purple); }
  .btn-outline {
    background: transparent;
    color: var(--muted);
    border: 1px solid var(--border2);
  }
  .btn-outline:hover { border-color: var(--purple); color: var(--text); }

  /* PROFILE PHOTO */
  .hero-photo-wrap {
    position: relative;
    display: flex; justify-content: center;
  }
  .photo-frame {
    position: relative;
    width: 300px; height: 380px;
  }
  .photo-border {
    position: absolute;
    inset: -2px;
    border-radius: 4px;
    background: linear-gradient(135deg, var(--purple), var(--green));
    padding: 2px;
  }
  .photo-inner {
    width: 100%; height: 100%;
    border-radius: 3px;
    overflow: hidden;
    background: var(--bg3);
    position: relative;
  }
  .photo-inner img {
    width: 100%; height: 100%;
    object-fit: cover;
    display: block;
    filter: grayscale(20%);
    transition: filter 0.4s;
  }
  .photo-inner img:hover { filter: grayscale(0%); }

  /* If no image, show initials */
  .photo-placeholder {
    width: 100%; height: 100%;
    display: flex; align-items: center; justify-content: center;
    background: var(--bg3);
    font-size: 5rem;
    font-weight: 800;
    color: var(--purple);
    font-family: var(--sans);
    letter-spacing: -0.04em;
  }

  .photo-tag {
    position: absolute;
    bottom: -16px; right: -16px;
    background: var(--bg2);
    border: 1px solid var(--border2);
    border-radius: 3px;
    padding: 10px 16px;
    font-family: var(--mono);
    font-size: 11px;
    color: var(--green);
    letter-spacing: 0.08em;
  }
  .photo-tag span { color: var(--muted); display: block; font-size: 10px; margin-top: 2px; }

  .photo-tag2 {
    position: absolute;
    top: -16px; left: -16px;
    background: var(--purple-dim);
    border: 1px solid rgba(97,87,246,0.3);
    border-radius: 3px;
    padding: 8px 14px;
    font-family: var(--mono);
    font-size: 10px;
    color: var(--purple);
    letter-spacing: 0.1em;
  }

  /* ── SCROLL INDICATOR ── */
  .scroll-hint {
    position: absolute;
    bottom: 2.5rem; left: 3rem;
    display: flex; align-items: center; gap: 10px;
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
  }
  .scroll-line {
    width: 40px; height: 1px;
    background: var(--muted);
    position: relative; overflow: hidden;
  }
  .scroll-line::after {
    content: '';
    position: absolute;
    left: -100%; top: 0;
    width: 100%; height: 100%;
    background: var(--green);
    animation: slide 1.8s ease-in-out infinite;
  }
  @keyframes slide { 0%{left:-100%} 100%{left:100%} }

  /* ── SECTION WRAPPER ── */
  .section-wrap {
    max-width: 1100px; margin: 0 auto;
    padding: 6rem 3rem;
  }

  .section-header {
    display: flex; align-items: center; gap: 1.5rem;
    margin-bottom: 3.5rem;
  }
  .section-num {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--green);
    letter-spacing: 0.15em;
  }
  .section-title {
    font-size: clamp(1.8rem, 4vw, 2.8rem);
    font-weight: 700;
    letter-spacing: -0.02em;
  }
  .section-line {
    flex: 1; height: 1px;
    background: var(--border);
  }

  /* ── ABOUT ── */
  #about { border-top: 1px solid var(--border); }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }

  .about-text {
    font-size: 15px; line-height: 1.9;
    color: var(--muted); font-weight: 400;
  }
  .about-text p { margin-bottom: 1.2rem; }
  .about-text strong { color: var(--text); font-weight: 600; }

  .about-facts {
    display: grid; gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 4px; overflow: hidden;
  }
  .fact-row {
    display: flex;
    background: var(--bg2);
    padding: 1rem 1.25rem;
    gap: 1rem;
  }
  .fact-key {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--green);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    min-width: 90px;
    padding-top: 2px;
  }
  .fact-val {
    font-size: 13px;
    color: var(--text);
    line-height: 1.5;
  }

  /* CODE BLOCK */
  .code-block {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
    margin-top: 2rem;
  }
  .code-header {
    display: flex; align-items: center; gap: 6px;
    padding: 10px 16px;
    border-bottom: 1px solid var(--border);
    background: var(--bg3);
  }
  .code-dot { width: 10px; height: 10px; border-radius: 50%; }
  .cd1 { background: #ff5f57; }
  .cd2 { background: #febc2e; }
  .cd3 { background: #28c840; }
  .code-filename {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    margin-left: 6px;
  }
  .code-body {
    padding: 1.25rem 1.5rem;
    font-family: var(--mono);
    font-size: 12px;
    line-height: 1.9;
    overflow-x: auto;
  }
  .c-kw { color: #c792ea; }
  .c-fn { color: #82aaff; }
  .c-str { color: #c3e88d; }
  .c-cmt { color: #546e7a; font-style: italic; }
  .c-var { color: #f07178; }
  .c-num { color: #f78c6c; }
  .c-pun { color: #89ddff; }

  /* ── SKILLS ── */
  #skills { border-top: 1px solid var(--border); }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
  }

  .skill-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 1.5rem;
    transition: border-color 0.2s, transform 0.2s;
  }
  .skill-card:hover {
    border-color: var(--border2);
    transform: translateY(-2px);
  }

  .skill-card-header {
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 1.2rem;
  }
  .skill-icon {
    width: 36px; height: 36px;
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
  }
  .si-purple { background: var(--purple-dim); }
  .si-green { background: var(--green-dim); }
  .si-amber { background: rgba(239,159,39,0.12); }
  .si-pink { background: rgba(212,83,126,0.12); }
  .si-blue { background: rgba(55,138,221,0.12); }
  .si-red { background: rgba(226,75,74,0.12); }

  .skill-card-title {
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 0.02em;
  }
  .skill-card-sub {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 0.08em;
  }

  .tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    font-family: var(--mono);
    font-size: 10px;
    padding: 4px 10px;
    border-radius: 2px;
    border: 1px solid;
    letter-spacing: 0.04em;
  }
  .t-purple { color: #a89cf7; border-color: rgba(168,156,247,0.3); background: rgba(97,87,246,0.08); }
  .t-green  { color: #1dbb85; border-color: rgba(29,187,133,0.3); background: rgba(29,187,133,0.07); }
  .t-amber  { color: #ef9f27; border-color: rgba(239,159,39,0.3); background: rgba(239,159,39,0.07); }
  .t-pink   { color: #e0608e; border-color: rgba(224,96,142,0.3); background: rgba(212,83,126,0.07); }
  .t-blue   { color: #5da8f5; border-color: rgba(93,168,245,0.3); background: rgba(55,138,221,0.07); }
  .t-red    { color: #e87070; border-color: rgba(232,112,112,0.3); background: rgba(226,75,74,0.07); }

  /* ── PROJECTS ── */
  #projects { border-top: 1px solid var(--border); }

  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 1.5rem;
  }

  .project-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 2rem;
    display: flex; flex-direction: column;
    transition: border-color 0.25s, transform 0.25s;
    position: relative; overflow: hidden;
  }
  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--purple), var(--green));
    opacity: 0;
    transition: opacity 0.3s;
  }
  .project-card:hover { border-color: var(--border2); transform: translateY(-4px); }
  .project-card:hover::before { opacity: 1; }

  .project-meta {
    display: flex; justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 1.2rem;
  }
  .project-num {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
  }
  .project-domain {
    font-family: var(--mono);
    font-size: 10px;
    padding: 3px 10px;
    border-radius: 2px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }
  .pd-cnn   { color: #e0608e; background: rgba(212,83,126,0.1); border: 1px solid rgba(212,83,126,0.2); }
  .pd-nlp   { color: #5da8f5; background: rgba(55,138,221,0.1); border: 1px solid rgba(55,138,221,0.2); }
  .pd-data  { color: #1dbb85; background: rgba(29,187,133,0.1); border: 1px solid rgba(29,187,133,0.2); }

  .project-title {
    font-size: 1.3rem;
    font-weight: 700;
    letter-spacing: -0.01em;
    margin-bottom: 0.75rem;
  }
  .project-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.75;
    flex: 1;
    margin-bottom: 1.5rem;
  }
  .project-link {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--purple);
    text-decoration: none;
    display: inline-flex; align-items: center; gap: 6px;
    border-bottom: 1px solid rgba(97,87,246,0.3);
    padding-bottom: 2px;
    transition: gap 0.2s, color 0.2s;
  }
  .project-link:hover { gap: 10px; color: var(--green); border-color: rgba(29,187,133,0.3); }

  /* ── STATS ── */
  #stats { border-top: 1px solid var(--border); }

  .stats-note {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    margin-bottom: 2rem;
    letter-spacing: 0.05em;
  }

  .stats-imgs {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }
  .stats-imgs img {
    width: 100%; border-radius: 4px;
    border: 1px solid var(--border);
    transition: border-color 0.2s;
  }
  .stats-imgs img:hover { border-color: var(--border2); }

  .stats-full { margin-top: 1.5rem; }
  .stats-full img { width: 100%; border-radius: 4px; border: 1px solid var(--border); }

  .trophies-wrap { margin-top: 1.5rem; text-align: center; }
  .trophies-wrap img { max-width: 100%; border-radius: 4px; }

  /* ── ROADMAP ── */
  #roadmap { border-top: 1px solid var(--border); }

  .roadmap-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  .roadmap-item {
    display: flex; align-items: flex-start; gap: 14px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 1rem 1.25rem;
    transition: border-color 0.2s;
  }
  .roadmap-item:hover { border-color: var(--border2); }

  .ri-icon {
    width: 28px; height: 28px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 12px; flex-shrink: 0; margin-top: 2px;
  }
  .ri-done  { background: rgba(29,187,133,0.15); color: var(--green); }
  .ri-wip   { background: rgba(97,87,246,0.15); color: var(--purple); }
  .ri-plan  { background: rgba(255,255,255,0.05); color: var(--muted); }

  .ri-label { font-size: 13px; font-weight: 600; margin-bottom: 2px; }
  .ri-sub { font-family: var(--mono); font-size: 10px; color: var(--muted); letter-spacing: 0.06em; }

  /* ── CONTACT ── */
  #contact { border-top: 1px solid var(--border); }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
  }

  .contact-headline {
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 700;
    letter-spacing: -0.02em;
    line-height: 1.15;
    margin-bottom: 1.2rem;
  }
  .contact-headline em {
    font-family: var(--serif);
    font-style: italic;
    color: var(--green);
    font-weight: 400;
  }
  .contact-text {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.8;
    margin-bottom: 2rem;
  }

  .contact-links {
    display: flex; flex-direction: column; gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 4px; overflow: hidden;
  }
  .contact-link {
    display: flex; align-items: center; justify-content: space-between;
    background: var(--bg2);
    padding: 1rem 1.25rem;
    text-decoration: none;
    transition: background 0.2s;
  }
  .contact-link:hover { background: var(--bg3); }

  .cl-left { display: flex; align-items: center; gap: 12px; }
  .cl-platform {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }
  .cl-value { font-size: 13px; color: var(--text); }
  .cl-arrow {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--purple);
    transition: transform 0.2s;
  }
  .contact-link:hover .cl-arrow { transform: translateX(4px); }

  .cl-dot {
    width: 8px; height: 8px; border-radius: 50%;
    flex-shrink: 0;
  }
  .dot-li { background: #0A66C2; }
  .dot-gh { background: #6e5494; }
  .dot-ml { background: #ea4335; }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem 3rem;
    display: flex; justify-content: space-between; align-items: center;
    max-width: 1100px; margin: 0 auto;
  }
  .footer-copy {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.06em;
  }
  .footer-made {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.06em;
  }
  .footer-made span { color: var(--purple); }

  /* ── ANIMATIONS ── */
  .fade-up {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .fade-up.visible { opacity: 1; transform: none; }

  /* ── RESPONSIVE ── */
  @media (max-width: 900px) {
    nav { padding: 1.2rem 1.5rem; }
    .nav-links { gap: 1.5rem; }
    #hero, .section-wrap { padding-left: 1.5rem; padding-right: 1.5rem; }
    .hero-grid { grid-template-columns: 1fr; }
    .hero-photo-wrap { order: -1; }
    .photo-frame { width: 220px; height: 280px; }
    .about-grid, .contact-grid, .roadmap-grid { grid-template-columns: 1fr; }
    .stats-imgs { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 0.5rem; text-align: center; padding: 1.5rem; }
  }
</style>
</head>
<body>

<!-- CURSOR -->
<div class="cursor" id="cursorDot"><div class="cursor-dot"></div></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">MJ.dev</div>
  <div class="nav-links">
    <a href="#about">About</a>
    <a href="#skills">Skills</a>
    <a href="#projects">Projects</a>
    <a href="#stats">Stats</a>
    <a href="#contact">Contact</a>
  </div>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="blob blob-1"></div>
  <div class="blob blob-2"></div>

  <div class="hero-grid">
    <div>
      <div class="hero-tag fade-up">Available for Collaboration</div>
      <h1 class="hero-name fade-up">
        Muhammad<br><em>Javed.</em>
      </h1>
      <p class="hero-desc fade-up">
        <strong>Software Engineering student</strong> at UBIT, University of Karachi —
        specializing in <strong>Artificial Intelligence & Data Science</strong> through 
        the Saylani IT Mass Training Program. Building intelligent systems that make 
        a difference.
      </p>
      <div class="hero-cta fade-up">
        <a href="#projects" class="btn btn-primary">View Projects →</a>
        <a href="#contact" class="btn btn-outline">Get in Touch</a>
      </div>
    </div>

    <div class="hero-photo-wrap fade-up">
      <div class="photo-frame">
        <div class="photo-border">
          <div class="photo-inner">
            <!--
              ══════════════════════════════════════
              PROFILE PHOTO: Replace src below with
              your image. Example:
              src="profile.jpeg"
              ══════════════════════════════════════
            -->
            <img src="profile.jpeg" alt="Muhammad Javed"
                 onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';" />
            <div class="photo-placeholder" style="display:none">MJ</div>
          </div>
        </div>
        <div class="photo-tag2">3rd Semester · SE</div>
        <div class="photo-tag">
          AI & Data Science
          <span>Saylani IT Program</span>
        </div>
      </div>
    </div>
  </div>

  <div class="scroll-hint">
    <div class="scroll-line"></div>
    Scroll to explore
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-wrap">
    <div class="section-header fade-up">
      <span class="section-num">01</span>
      <h2 class="section-title">About Me</h2>
      <div class="section-line"></div>
    </div>

    <div class="about-grid">
      <div>
        <div class="about-text fade-up">
          <p>I am a passionate <strong>Software Engineering student</strong> at UBIT, University of Karachi, 
          currently in my 3rd semester. Alongside my degree, I'm enrolled in the 
          <strong>Saylani IT Mass Training Program</strong>, where I specialize in 
          <strong>Artificial Intelligence & Data Science</strong>.</p>

          <p>My core interests lie in building <strong>intelligent systems</strong>, working with 
          large-scale datasets, and applying cutting-edge Machine Learning and Deep Learning 
          techniques to solve real-world problems across healthcare, finance, and more.</p>

          <p>I believe in <strong>continuous learning</strong>, open collaboration, and mentoring 
          others — always aiming to contribute to impactful, data-driven solutions.</p>
        </div>

        <div class="code-block fade-up" style="margin-top: 2rem;">
          <div class="code-header">
            <div class="code-dot cd1"></div>
            <div class="code-dot cd2"></div>
            <div class="code-dot cd3"></div>
            <span class="code-filename">muhammad_javed.py</span>
          </div>
          <div class="code-body">
<span class="c-kw">class</span> <span class="c-fn">MuhammadJaved</span><span class="c-pun">:</span><br>
&nbsp;&nbsp;<span class="c-kw">def</span> <span class="c-fn">__init__</span><span class="c-pun">(</span><span class="c-var">self</span><span class="c-pun">):</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-var">self</span>.university &nbsp;<span class="c-pun">=</span> <span class="c-str">"UBIT, Karachi"</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-var">self</span>.semester &nbsp;&nbsp;&nbsp;<span class="c-pun">=</span> <span class="c-str">"3rd — Software Eng."</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-var">self</span>.training &nbsp;&nbsp;&nbsp;<span class="c-pun">=</span> <span class="c-str">"Saylani IT Program"</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-var">self</span>.focus &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-pun">=</span> <span class="c-pun">[</span><span class="c-str">"AI"</span><span class="c-pun">,</span> <span class="c-str">"ML"</span><span class="c-pun">,</span> <span class="c-str">"DL"</span><span class="c-pun">,</span> <span class="c-str">"NLP"</span><span class="c-pun">]</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-var">self</span>.location &nbsp;&nbsp;&nbsp;<span class="c-pun">=</span> <span class="c-str">"Karachi, Pakistan"</span><br>
<br>
&nbsp;&nbsp;<span class="c-kw">def</span> <span class="c-fn">passion</span><span class="c-pun">(</span><span class="c-var">self</span><span class="c-pun">):</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-kw">return</span> <span class="c-str">"Data → Intelligence → Impact"</span><br>
          </div>
        </div>
      </div>

      <div class="about-facts fade-up">
        <div class="fact-row"><span class="fact-key">Name</span><span class="fact-val">Muhammad Javed</span></div>
        <div class="fact-row"><span class="fact-key">University</span><span class="fact-val">UBIT, University of Karachi</span></div>
        <div class="fact-row"><span class="fact-key">Semester</span><span class="fact-val">3rd — Software Engineering</span></div>
        <div class="fact-row"><span class="fact-key">Training</span><span class="fact-val">Saylani IT Mass Training Program</span></div>
        <div class="fact-row"><span class="fact-key">Speciality</span><span class="fact-val">AI & Data Science</span></div>
        <div class="fact-row"><span class="fact-key">Location</span><span class="fact-val">Karachi, Pakistan 🇵🇰</span></div>
        <div class="fact-row"><span class="fact-key">Status</span><span class="fact-val" style="color:var(--green)">● Open to Collaborate</span></div>
        <div class="fact-row"><span class="fact-key">Email</span><span class="fact-val" style="font-size:12px">muhammadjaved.dh@gmail.com</span></div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-wrap">
    <div class="section-header fade-up">
      <span class="section-num">02</span>
      <h2 class="section-title">Technical Skills</h2>
      <div class="section-line"></div>
    </div>

    <div class="skills-grid">
      <div class="skill-card fade-up">
        <div class="skill-card-header">
          <div class="skill-icon si-purple">💻</div>
          <div>
            <div class="skill-card-title">Programming Languages</div>
            <div class="skill-card-sub">Core languages</div>
          </div>
        </div>
        <div class="tags">
          <span class="tag t-purple">C++</span>
          <span class="tag t-purple">Java</span>
          <span class="tag t-purple">Python</span>
        </div>
      </div>

      <div class="skill-card fade-up">
        <div class="skill-card-header">
          <div class="skill-icon si-green">📊</div>
          <div>
            <div class="skill-card-title">Data Analysis & Visualization</div>
            <div class="skill-card-sub">7 tools mastered</div>
          </div>
        </div>
        <div class="tags">
          <span class="tag t-green">NumPy</span>
          <span class="tag t-green">Pandas</span>
          <span class="tag t-green">Matplotlib</span>
          <span class="tag t-green">Seaborn</span>
          <span class="tag t-green">Excel</span>
          <span class="tag t-green">Power BI</span>
          <span class="tag t-green">SQL</span>
        </div>
      </div>

      <div class="skill-card fade-up">
        <div class="skill-card-header">
          <div class="skill-icon si-amber">🤖</div>
          <div>
            <div class="skill-card-title">Machine Learning</div>
            <div class="skill-card-sub">8 algorithms</div>
          </div>
        </div>
        <div class="tags">
          <span class="tag t-amber">Scikit-Learn</span>
          <span class="tag t-amber">Linear Regression</span>
          <span class="tag t-amber">Logistic Regression</span>
          <span class="tag t-amber">KNN</span>
          <span class="tag t-amber">SVM</span>
          <span class="tag t-amber">Random Forest</span>
          <span class="tag t-amber">XGBoost</span>
          <span class="tag t-amber">K-Means</span>
        </div>
      </div>

      <div class="skill-card fade-up">
        <div class="skill-card-header">
          <div class="skill-icon si-pink">🧠</div>
          <div>
            <div class="skill-card-title">Deep Learning</div>
            <div class="skill-card-sub">Frameworks & architectures</div>
          </div>
        </div>
        <div class="tags">
          <span class="tag t-pink">TensorFlow</span>
          <span class="tag t-pink">Keras</span>
          <span class="tag t-pink">PyTorch</span>
          <span class="tag t-pink">ANN</span>
          <span class="tag t-pink">CNN</span>
          <span class="tag t-pink">RNN</span>
          <span class="tag t-pink">DNN</span>
          <span class="tag t-pink">GAN</span>
        </div>
      </div>

      <div class="skill-card fade-up">
        <div class="skill-card-header">
          <div class="skill-icon si-blue">🗣️</div>
          <div>
            <div class="skill-card-title">Natural Language Processing</div>
            <div class="skill-card-sub">Text intelligence</div>
          </div>
        </div>
        <div class="tags">
          <span class="tag t-blue">NLP</span>
          <span class="tag t-blue">Text Cleaning</span>
          <span class="tag t-blue">Vectorization</span>
          <span class="tag t-blue">Text Classification</span>
        </div>
      </div>

      <div class="skill-card fade-up">
        <div class="skill-card-header">
          <div class="skill-icon si-red">👁️</div>
          <div>
            <div class="skill-card-title">Computer Vision</div>
            <div class="skill-card-sub">Image intelligence</div>
          </div>
        </div>
        <div class="tags">
          <span class="tag t-red">OpenCV</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-wrap">
    <div class="section-header fade-up">
      <span class="section-num">03</span>
      <h2 class="section-title">Featured Projects</h2>
      <div class="section-line"></div>
    </div>

    <div class="projects-grid">
      <div class="project-card fade-up">
        <div class="project-meta">
          <span class="project-num">01</span>
          <span class="project-domain pd-cnn">CNN · Medical AI</span>
        </div>
        <h3 class="project-title">Brain Tumor Detection</h3>
        <p class="project-desc">
          Deep learning-based medical image classification system using Convolutional Neural Networks 
          to detect and classify brain tumors from MRI scans with high accuracy.
        </p>
        <a href="https://github.com/Muhammad-Javed2005/Brain-Tumor-Detection-CNN" target="_blank" class="project-link">
          View on GitHub →
        </a>
      </div>

      <div class="project-card fade-up">
        <div class="project-meta">
          <span class="project-num">02</span>
          <span class="project-domain pd-nlp">ML · NLP</span>
        </div>
        <h3 class="project-title">Fake News Detection</h3>
        <p class="project-desc">
          Machine learning and NLP-powered pipeline for classifying fake vs. real news articles, 
          combating misinformation with automated text analysis and classification models.
        </p>
        <a href="https://github.com/Muhammad-Javed2005/FakeNews-Detection-ML" target="_blank" class="project-link">
          View on GitHub →
        </a>
      </div>

      <div class="project-card fade-up">
        <div class="project-meta">
          <span class="project-num">03</span>
          <span class="project-domain pd-data">Data Science</span>
        </div>
        <h3 class="project-title">Job Market Trend Monitor</h3>
        <p class="project-desc">
          Real-time analysis and dashboard of job market trends, in-demand skills, and 
          industry insights — helping professionals navigate the evolving tech landscape.
        </p>
        <a href="https://github.com/Muhammad-Javed2005/JobMarket-TrendMonitor" target="_blank" class="project-link">
          View on GitHub →
        </a>
      </div>
    </div>
  </div>
</section>

<!-- STATS -->
<section id="stats">
  <div class="section-wrap">
    <div class="section-header fade-up">
      <span class="section-num">04</span>
      <h2 class="section-title">GitHub Statistics</h2>
      <div class="section-line"></div>
    </div>

    <p class="stats-note fade-up">// Live data pulled from GitHub API</p>

    <div class="stats-imgs fade-up">
      <img src="https://github-readme-stats.vercel.app/api?username=Muhammad-Javed2005&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d0d1a&title_color=6157f6&icon_color=1dbb85&text_color=e8e4f0&rank_icon=github" alt="GitHub Stats" loading="lazy"/>
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=Muhammad-Javed2005&theme=tokyonight&hide_border=true&background=0d0d1a&ring=6157f6&fire=1dbb85&currStreakLabel=e8e4f0" alt="GitHub Streak" loading="lazy"/>
    </div>

    <div class="stats-full fade-up">
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Muhammad-Javed2005&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d0d1a&title_color=6157f6&text_color=e8e4f0&langs_count=8" alt="Top Languages" loading="lazy"/>
    </div>

    <div class="stats-full fade-up" style="margin-top:1.5rem">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=Muhammad-Javed2005&bg_color=0d0d1a&color=1dbb85&line=6157f6&point=ffffff&area=true&hide_border=true" alt="Contribution Graph" loading="lazy"/>
    </div>

    <div class="trophies-wrap fade-up">
      <img src="https://github-profile-trophy.vercel.app/?username=Muhammad-Javed2005&theme=tokyonight&no-frame=true&margin-w=8&column=6" alt="GitHub Trophies" loading="lazy"/>
    </div>

    <div class="stats-full fade-up" style="margin-top:1.5rem">
      <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=Muhammad-Javed2005&theme=tokyonight" alt="Profile Summary" loading="lazy"/>
    </div>
  </div>
</section>

<!-- ROADMAP -->
<section id="roadmap">
  <div class="section-wrap">
    <div class="section-header fade-up">
      <span class="section-num">05</span>
      <h2 class="section-title">Learning Roadmap</h2>
      <div class="section-line"></div>
    </div>

    <div class="roadmap-grid">
      <div class="roadmap-item fade-up"><div class="ri-icon ri-done">✓</div><div><div class="ri-label">Machine Learning Fundamentals</div><div class="ri-sub">Completed</div></div></div>
      <div class="roadmap-item fade-up"><div class="ri-icon ri-done">✓</div><div><div class="ri-label">Deep Learning — ANN, CNN, RNN, GAN</div><div class="ri-sub">Completed</div></div></div>
      <div class="roadmap-item fade-up"><div class="ri-icon ri-done">✓</div><div><div class="ri-label">Natural Language Processing Basics</div><div class="ri-sub">Completed</div></div></div>
      <div class="roadmap-item fade-up"><div class="ri-icon ri-done">✓</div><div><div class="ri-label">Computer Vision with OpenCV</div><div class="ri-sub">Completed</div></div></div>
      <div class="roadmap-item fade-up"><div class="ri-icon ri-wip">↻</div><div><div class="ri-label">LLMs & Prompt Engineering</div><div class="ri-sub">In Progress</div></div></div>
      <div class="roadmap-item fade-up"><div class="ri-icon ri-wip">↻</div><div><div class="ri-label">MLOps & Model Deployment</div><div class="ri-sub">In Progress</div></div></div>
      <div class="roadmap-item fade-up"><div class="ri-icon ri-plan">○</div><div><div class="ri-label">Transformers & Attention Mechanisms</div><div class="ri-sub">Planned</div></div></div>
      <div class="roadmap-item fade-up"><div class="ri-icon ri-plan">○</div><div><div class="ri-label">Cloud AI — AWS / GCP</div><div class="ri-sub">Planned</div></div></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-wrap">
    <div class="section-header fade-up">
      <span class="section-num">06</span>
      <h2 class="section-title">Get in Touch</h2>
      <div class="section-line"></div>
    </div>

    <div class="contact-grid">
      <div class="fade-up">
        <h3 class="contact-headline">Let's build something <em>intelligent</em> together.</h3>
        <p class="contact-text">
          Whether it's a collaboration on an AI project, a research idea, 
          or just a conversation about data science — my inbox is always open.
        </p>
        <a href="mailto:muhammadjaved.dh@gmail.com" class="btn btn-primary">Send Email →</a>
      </div>

      <div class="contact-links fade-up">
        <a href="https://www.linkedin.com/in/muhammad-javed-24b262369" target="_blank" class="contact-link">
          <div class="cl-left">
            <div class="cl-dot dot-li"></div>
            <div>
              <div class="cl-platform">LinkedIn</div>
              <div class="cl-value">Muhammad Javed</div>
            </div>
          </div>
          <span class="cl-arrow">→</span>
        </a>
        <a href="https://github.com/Muhammad-Javed2005" target="_blank" class="contact-link">
          <div class="cl-left">
            <div class="cl-dot dot-gh"></div>
            <div>
              <div class="cl-platform">GitHub</div>
              <div class="cl-value">Muhammad-Javed2005</div>
            </div>
          </div>
          <span class="cl-arrow">→</span>
        </a>
        <a href="mailto:muhammadjaved.dh@gmail.com" class="contact-link">
          <div class="cl-left">
            <div class="cl-dot dot-ml"></div>
            <div>
              <div class="cl-platform">Gmail (Primary)</div>
              <div class="cl-value">muhammadjaved.dh@gmail.com</div>
            </div>
          </div>
          <span class="cl-arrow">→</span>
        </a>
        <a href="mailto:muhammadjaved.tech5@gmail.com" class="contact-link">
          <div class="cl-left">
            <div class="cl-dot dot-ml"></div>
            <div>
              <div class="cl-platform">Gmail (Tech)</div>
              <div class="cl-value">muhammadjaved.tech5@gmail.com</div>
            </div>
          </div>
          <span class="cl-arrow">→</span>
        </a>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="footer-copy">© 2025 Muhammad Javed — Karachi, Pakistan</div>
  <div class="footer-made">Designed with <span>♥</span> & code</div>
</footer>

<script>
  // CURSOR
  const dot = document.getElementById('cursorDot');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animCursor() {
    dot.style.left = mx + 'px'; dot.style.top = my + 'px';
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animCursor);
  }
  animCursor();
  document.querySelectorAll('a, button').forEach(el => {
    el.addEventListener('mouseenter', () => ring.classList.add('hover'));
    el.addEventListener('mouseleave', () => ring.classList.remove('hover'));
  });

  // SCROLL FADE
  const observer = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

  // NAV active
  const sections = document.querySelectorAll('section[id]');
  const navLinks = document.querySelectorAll('.nav-links a');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => { if (window.scrollY >= s.offsetTop - 120) current = s.id; });
    navLinks.forEach(a => {
      a.style.color = a.getAttribute('href') === '#' + current ? '#e8e4f0' : '';
    });
  });
</script>
</body>
</html>
