# poragislam
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Porag Islam — Portfolio</title>
  <meta name="description" content="Full-Stack Engineer & Researcher. Building robust systems and exploring the intersection of AI and human-computer interaction." />
  <meta property="og:title" content="Alex Morgan — Portfolio" />
  <meta property="og:description" content="Full-Stack Engineer & Researcher" />
  <meta property="og:type" content="website" />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Mono:ital,wght@0,300;0,400;1,300&family=Syne:wght@400;500;700;800&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
 
    :root {
      --ink: #0d0d0d;
      --paper: #f5f2ec;
      --accent: #c8543a;
      --accent-muted: #e8a090;
      --ink-60: rgba(13,13,13,0.6);
      --ink-20: rgba(13,13,13,0.12);
      --serif: 'Cormorant Garamond', Georgia, serif;
      --sans: 'Syne', sans-serif;
      --mono: 'DM Mono', monospace;
      --max: 1200px;
      --gutter: clamp(1.5rem, 5vw, 4rem);
    }
 
    html { scroll-behavior: smooth; font-size: 16px; }
 
    body {
      background: var(--paper);
      color: var(--ink);
      font-family: var(--serif);
      font-weight: 300;
      line-height: 1.7;
      overflow-x: hidden;
      cursor: none;
    }
 
    /* ── Custom Cursor ── */
    .cursor {
      position: fixed; top: 0; left: 0; z-index: 9999;
      pointer-events: none;
    }
    .cursor-dot {
      width: 6px; height: 6px;
      background: var(--accent);
      border-radius: 50%;
      position: absolute;
      transform: translate(-50%, -50%);
      transition: transform 0.1s ease;
    }
    .cursor-ring {
      width: 36px; height: 36px;
      border: 1px solid var(--ink-60);
      border-radius: 50%;
      position: absolute;
      transform: translate(-50%, -50%);
      transition: width 0.3s ease, height 0.3s ease, border-color 0.3s ease, transform 0.1s ease;
    }
    .cursor-ring.hover { width: 60px; height: 60px; border-color: var(--accent); }
 
    /* ── Noise Texture Overlay ── */
    body::before {
      content: '';
      position: fixed; inset: 0; z-index: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
      pointer-events: none;
      opacity: 0.4;
    }
 
    /* ── Navigation ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      padding: 1.5rem var(--gutter);
      display: flex; align-items: center; justify-content: space-between;
      background: transparent;
      transition: background 0.4s ease, backdrop-filter 0.4s ease;
    }
    nav.scrolled {
      background: rgba(245,242,236,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--ink-20);
    }
    .nav-logo {
      font-family: var(--sans);
      font-weight: 800;
      font-size: 1rem;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      color: var(--ink);
      text-decoration: none;
    }
    .nav-logo span { color: var(--accent); }
    .nav-links { display: flex; gap: 2.5rem; list-style: none; }
    .nav-links a {
      font-family: var(--mono);
      font-size: 0.72rem;
      letter-spacing: 0.08em;
      color: var(--ink-60);
      text-decoration: none;
      text-transform: uppercase;
      position: relative;
      transition: color 0.25s;
    }
    .nav-links a::after {
      content: '';
      position: absolute; bottom: -2px; left: 0;
      width: 0; height: 1px;
      background: var(--accent);
      transition: width 0.3s ease;
    }
    .nav-links a:hover { color: var(--ink); }
    .nav-links a:hover::after { width: 100%; }
 
    .nav-hamburger {
      display: none; flex-direction: column; gap: 5px;
      cursor: pointer; background: none; border: none; padding: 4px;
    }
    .nav-hamburger span {
      display: block; width: 24px; height: 1px;
      background: var(--ink);
      transition: transform 0.3s, opacity 0.3s;
    }
    .nav-hamburger.open span:nth-child(1) { transform: translateY(6px) rotate(45deg); }
    .nav-hamburger.open span:nth-child(2) { opacity: 0; }
    .nav-hamburger.open span:nth-child(3) { transform: translateY(-6px) rotate(-45deg); }
 
    .mobile-menu {
      display: none; position: fixed; inset: 0; z-index: 99;
      background: var(--paper);
      flex-direction: column; align-items: center; justify-content: center;
      gap: 2.5rem;
    }
    .mobile-menu.open { display: flex; }
    .mobile-menu a {
      font-family: var(--sans); font-size: 2.5rem; font-weight: 700;
      color: var(--ink); text-decoration: none;
      transition: color 0.2s;
    }
    .mobile-menu a:hover { color: var(--accent); }
 
    /* ── Section Wrappers ── */
    section { position: relative; z-index: 1; }
    .container { max-width: var(--max); margin: 0 auto; padding: 0 var(--gutter); }
 
    /* ── Hero ── */
    #hero {
      min-height: 100svh;
      display: flex; flex-direction: column; justify-content: flex-end;
      padding-bottom: 6rem;
      overflow: hidden;
    }
    .hero-bg-number {
      position: absolute; top: 50%; right: -0.05em;
      transform: translateY(-50%);
      font-family: var(--sans);
      font-size: clamp(18rem, 35vw, 42rem);
      font-weight: 800;
      color: transparent;
      -webkit-text-stroke: 1px var(--ink-20);
      line-height: 1;
      pointer-events: none;
      user-select: none;
    }
    .hero-label {
      font-family: var(--mono);
      font-size: 0.72rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 1.5rem;
      opacity: 0; animation: fadeUp 0.8s 0.2s forwards;
    }
    .hero-name {
      font-family: var(--sans);
      font-size: clamp(3.5rem, 9vw, 8rem);
      font-weight: 800;
      line-height: 0.9;
      letter-spacing: -0.03em;
      margin-bottom: 1.8rem;
      opacity: 0; animation: fadeUp 0.8s 0.4s forwards;
    }
    .hero-name em {
      font-family: var(--serif);
      font-style: italic;
      font-weight: 300;
      color: var(--accent);
    }
    .hero-tagline {
      font-family: var(--serif);
      font-size: clamp(1.1rem, 2.5vw, 1.6rem);
      font-weight: 300;
      color: var(--ink-60);
      max-width: 560px;
      margin-bottom: 3rem;
      opacity: 0; animation: fadeUp 0.8s 0.6s forwards;
    }
    .hero-cta {
      display: flex; gap: 1.2rem; flex-wrap: wrap;
      opacity: 0; animation: fadeUp 0.8s 0.8s forwards;
    }
    .btn {
      font-family: var(--mono);
      font-size: 0.72rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 0.85rem 2rem;
      text-decoration: none;
      display: inline-block;
      transition: all 0.3s ease;
      position: relative; overflow: hidden;
    }
    .btn-primary {
      background: var(--ink);
      color: var(--paper);
      border: 1px solid var(--ink);
    }
    .btn-primary::before {
      content: ''; position: absolute; inset: 0;
      background: var(--accent);
      transform: translateX(-100%);
      transition: transform 0.4s ease;
    }
    .btn-primary:hover::before { transform: translateX(0); }
    .btn-primary span { position: relative; z-index: 1; }
    .btn-outline {
      background: transparent;
      color: var(--ink);
      border: 1px solid var(--ink-20);
    }
    .btn-outline:hover {
      border-color: var(--ink);
      background: var(--ink);
      color: var(--paper);
    }
    .hero-scroll {
      position: absolute; bottom: 2.5rem; right: var(--gutter);
      display: flex; flex-direction: column; align-items: center; gap: 0.6rem;
      opacity: 0; animation: fadeUp 1s 1.2s forwards;
    }
    .hero-scroll span {
      font-family: var(--mono); font-size: 0.6rem;
      letter-spacing: 0.15em; text-transform: uppercase;
      color: var(--ink-60);
      writing-mode: vertical-rl;
    }
    .scroll-line {
      width: 1px; height: 60px;
      background: linear-gradient(to bottom, var(--ink-60), transparent);
      animation: scrollPulse 2s 1.5s infinite;
    }
 
    /* ── About ── */
    #about {
      padding: clamp(5rem, 12vw, 10rem) 0;
      border-top: 1px solid var(--ink-20);
    }
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 2fr;
      gap: clamp(3rem, 8vw, 7rem);
      align-items: start;
    }
    .about-sticky { position: sticky; top: 8rem; }
    .section-label {
      font-family: var(--mono);
      font-size: 0.68rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 1rem;
      display: flex; align-items: center; gap: 1rem;
    }
    .section-label::before {
      content: ''; display: block;
      width: 2rem; height: 1px; background: var(--accent);
    }
    .section-title {
      font-family: var(--sans);
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 700;
      line-height: 1.1;
      letter-spacing: -0.02em;
    }
    .about-avatar {
      width: 100%; aspect-ratio: 3/4;
      background: var(--ink-20);
      position: relative; overflow: hidden;
      margin-top: 2rem;
    }
    .about-avatar-inner {
      position: absolute; inset: 0;
      background: linear-gradient(135deg, #e8d5c4 0%, #c4b5a8 40%, #9a8880 100%);
      display: flex; align-items: center; justify-content: center;
    }
    .avatar-initials {
      font-family: var(--sans); font-size: 4rem; font-weight: 800;
      color: rgba(255,255,255,0.5); letter-spacing: -0.04em;
    }
    .about-avatar::after {
      content: '';
      position: absolute; bottom: -1px; left: -1px; right: -1px;
      height: 40%;
      background: linear-gradient(to top, var(--paper), transparent);
    }
    .about-body p {
      font-size: clamp(1rem, 1.8vw, 1.2rem);
      color: var(--ink-60);
      margin-bottom: 1.5rem;
    }
    .about-body p strong { color: var(--ink); font-weight: 400; }
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
      gap: 0.75rem;
      margin-top: 2.5rem;
    }
    .skill-chip {
      font-family: var(--mono); font-size: 0.68rem;
      letter-spacing: 0.06em; text-transform: uppercase;
      padding: 0.6rem 1rem;
      border: 1px solid var(--ink-20);
      color: var(--ink-60);
      text-align: center;
      transition: all 0.25s;
      cursor: default;
    }
    .skill-chip:hover {
      border-color: var(--accent);
      color: var(--accent);
      background: rgba(200,84,58,0.04);
    }
 
    /* ── Experience ── */
    #experience {
      padding: clamp(5rem, 12vw, 10rem) 0;
      background: var(--ink);
      color: var(--paper);
    }
    #experience .section-label { color: var(--accent-muted); }
    #experience .section-label::before { background: var(--accent-muted); }
    #experience .section-title { color: var(--paper); }
    .timeline { margin-top: 4rem; position: relative; }
    .timeline::before {
      content: '';
      position: absolute; top: 0; bottom: 0; left: 0;
      width: 1px;
      background: rgba(245,242,236,0.15);
    }
    .timeline-item {
      display: grid;
      grid-template-columns: 200px 1fr;
      gap: 3rem;
      padding: 2.5rem 0 2.5rem 0;
      border-bottom: 1px solid rgba(245,242,236,0.08);
      position: relative;
    }
    .timeline-item::before {
      content: '';
      position: absolute; left: -4px; top: 3rem;
      width: 9px; height: 9px;
      border-radius: 50%;
      background: var(--accent);
      border: 2px solid var(--ink);
    }
    .timeline-date {
      font-family: var(--mono); font-size: 0.7rem;
      letter-spacing: 0.08em; text-transform: uppercase;
      color: rgba(245,242,236,0.4);
      padding-top: 0.3rem;
      padding-left: 2rem;
    }
    .timeline-role {
      font-family: var(--sans); font-size: 1.2rem; font-weight: 700;
      letter-spacing: -0.01em; margin-bottom: 0.25rem;
    }
    .timeline-org {
      font-family: var(--mono); font-size: 0.72rem;
      letter-spacing: 0.06em; color: var(--accent-muted);
      margin-bottom: 1rem;
    }
    .timeline-desc {
      font-size: 0.95rem; color: rgba(245,242,236,0.55);
      line-height: 1.7;
    }
    .timeline-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1rem; }
    .tag {
      font-family: var(--mono); font-size: 0.6rem;
      letter-spacing: 0.08em; text-transform: uppercase;
      padding: 0.35rem 0.8rem;
      border: 1px solid rgba(245,242,236,0.15);
      color: rgba(245,242,236,0.4);
    }
 
    /* ── Projects ── */
    #projects {
      padding: clamp(5rem, 12vw, 10rem) 0;
      border-top: 1px solid var(--ink-20);
    }
    .projects-header {
      display: flex; align-items: flex-end; justify-content: space-between;
      margin-bottom: 4rem; flex-wrap: wrap; gap: 1.5rem;
    }
    .view-all {
      font-family: var(--mono); font-size: 0.68rem;
      letter-spacing: 0.12em; text-transform: uppercase;
      color: var(--accent); text-decoration: none;
      display: flex; align-items: center; gap: 0.5rem;
      transition: gap 0.2s;
    }
    .view-all:hover { gap: 1rem; }
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 1.5rem;
    }
    .project-card {
      background: white;
      border: 1px solid var(--ink-20);
      overflow: hidden;
      position: relative;
      transition: transform 0.4s cubic-bezier(0.16,1,0.3,1), box-shadow 0.4s ease;
    }
    .project-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 24px 60px rgba(13,13,13,0.1);
    }
    .project-card:nth-child(1) { grid-column: span 7; }
    .project-card:nth-child(2) { grid-column: span 5; }
    .project-card:nth-child(3) { grid-column: span 5; }
    .project-card:nth-child(4) { grid-column: span 7; }
    .project-visual {
      width: 100%; aspect-ratio: 16/9;
      overflow: hidden; position: relative;
    }
    .project-visual-inner {
      position: absolute; inset: 0;
      transition: transform 0.6s ease;
      display: flex; align-items: center; justify-content: center;
    }
    .project-card:hover .project-visual-inner { transform: scale(1.05); }
    .pv-1 { background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%); }
    .pv-2 { background: linear-gradient(135deg, #2d2013 0%, #5a3e28 50%, #8b6245 100%); }
    .pv-3 { background: linear-gradient(135deg, #0d2b1d 0%, #1a5c3a 50%, #2d8c5c 100%); }
    .pv-4 { background: linear-gradient(135deg, #2b1a2d 0%, #5c2d5e 50%, #8c3d90 100%); }
    .pv-icon {
      font-size: 3rem; opacity: 0.3;
      user-select: none;
    }
    .project-body { padding: 1.8rem; }
    .project-number {
      font-family: var(--mono); font-size: 0.6rem;
      letter-spacing: 0.15em; color: var(--accent);
      margin-bottom: 0.75rem;
    }
    .project-title {
      font-family: var(--sans); font-size: 1.15rem; font-weight: 700;
      letter-spacing: -0.01em; margin-bottom: 0.6rem;
    }
    .project-desc {
      font-size: 0.9rem; color: var(--ink-60); line-height: 1.65;
      margin-bottom: 1.2rem;
    }
    .project-footer {
      display: flex; align-items: center; justify-content: space-between;
      flex-wrap: wrap; gap: 0.75rem;
    }
    .project-stack { display: flex; gap: 0.5rem; flex-wrap: wrap; }
    .stack-tag {
      font-family: var(--mono); font-size: 0.6rem;
      letter-spacing: 0.06em;
      padding: 0.25rem 0.65rem;
      background: var(--ink-20);
      color: var(--ink-60);
    }
    .project-links { display: flex; gap: 1rem; }
    .project-link {
      font-family: var(--mono); font-size: 0.65rem;
      letter-spacing: 0.1em; text-transform: uppercase;
      color: var(--accent); text-decoration: none;
      transition: opacity 0.2s;
    }
    .project-link:hover { opacity: 0.7; }
 
    /* ── Publications ── */
    #publications {
      padding: clamp(5rem, 12vw, 10rem) 0;
      background: #f0ece3;
      border-top: 1px solid var(--ink-20);
    }
    .pub-list { margin-top: 3rem; }
    .pub-item {
      padding: 2rem 0;
      border-bottom: 1px solid var(--ink-20);
      display: grid;
      grid-template-columns: 80px 1fr;
      gap: 2rem;
      align-items: start;
      transition: background 0.2s;
    }
    .pub-year {
      font-family: var(--mono); font-size: 0.7rem;
      letter-spacing: 0.08em; color: var(--ink-60);
      padding-top: 0.25rem;
    }
    .pub-title {
      font-family: var(--serif); font-size: 1.15rem;
      font-weight: 400; margin-bottom: 0.35rem;
      line-height: 1.4;
    }
    .pub-venue {
      font-family: var(--mono); font-size: 0.68rem;
      letter-spacing: 0.06em; color: var(--accent);
      margin-bottom: 0.5rem;
    }
    .pub-authors { font-size: 0.88rem; color: var(--ink-60); }
    .pub-authors strong { color: var(--ink); font-weight: 400; text-decoration: underline; }
    .pub-badge {
      display: inline-block; margin-left: 0.75rem;
      font-family: var(--mono); font-size: 0.58rem;
      letter-spacing: 0.1em; text-transform: uppercase;
      padding: 0.2rem 0.6rem;
      background: var(--accent);
      color: white;
      vertical-align: middle;
    }
 
    /* ── Contact ── */
    #contact {
      padding: clamp(5rem, 12vw, 10rem) 0;
      border-top: 1px solid var(--ink-20);
    }
    .contact-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: clamp(3rem, 8vw, 7rem);
      align-items: start;
    }
    .contact-headline {
      font-family: var(--sans); font-size: clamp(2.5rem, 5vw, 4.5rem);
      font-weight: 800; letter-spacing: -0.03em; line-height: 1;
    }
    .contact-headline em {
      font-family: var(--serif); font-style: italic; font-weight: 300;
      color: var(--accent); display: block;
    }
    .contact-sub {
      font-size: 1rem; color: var(--ink-60); margin-top: 1.5rem; max-width: 360px;
    }
    .contact-links { margin-top: 2.5rem; display: flex; flex-direction: column; gap: 1rem; }
    .contact-link-item {
      display: flex; align-items: center; gap: 1rem;
      text-decoration: none; color: var(--ink);
      font-family: var(--mono); font-size: 0.78rem;
      letter-spacing: 0.08em; text-transform: uppercase;
      padding-bottom: 1rem;
      border-bottom: 1px solid var(--ink-20);
      transition: color 0.2s;
    }
    .contact-link-item:hover { color: var(--accent); }
    .contact-link-icon { font-size: 1rem; min-width: 1.5rem; }
    .contact-form { display: flex; flex-direction: column; gap: 1.2rem; }
    .form-group { display: flex; flex-direction: column; gap: 0.4rem; }
    .form-label {
      font-family: var(--mono); font-size: 0.62rem;
      letter-spacing: 0.15em; text-transform: uppercase;
      color: var(--ink-60);
    }
    .form-input, .form-textarea {
      font-family: var(--serif); font-size: 1rem;
      background: transparent;
      border: none; border-bottom: 1px solid var(--ink-20);
      padding: 0.75rem 0;
      color: var(--ink);
      outline: none;
      transition: border-color 0.3s;
      width: 100%;
      resize: none;
    }
    .form-input:focus, .form-textarea:focus { border-color: var(--ink); }
    .form-textarea { min-height: 120px; }
    .form-btn {
      align-self: flex-start;
      margin-top: 0.5rem;
    }
 
    /* ── Footer ── */
    footer {
      padding: 2.5rem var(--gutter);
      border-top: 1px solid var(--ink-20);
      display: flex; align-items: center; justify-content: space-between;
      flex-wrap: wrap; gap: 1rem;
      position: relative; z-index: 1;
    }
    .footer-copy {
      font-family: var(--mono); font-size: 0.65rem;
      letter-spacing: 0.1em; color: var(--ink-60);
    }
    .footer-made {
      font-family: var(--mono); font-size: 0.65rem;
      letter-spacing: 0.08em; color: var(--ink-60);
    }
    .footer-made a { color: var(--accent); text-decoration: none; }
 
    /* ── Animations ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes scrollPulse {
      0%, 100% { opacity: 0.4; transform: scaleY(1); }
      50%       { opacity: 1;   transform: scaleY(1.15); }
    }
    .reveal {
      opacity: 0; transform: translateY(30px);
      transition: opacity 0.8s cubic-bezier(0.16,1,0.3,1), transform 0.8s cubic-bezier(0.16,1,0.3,1);
    }
    .reveal.visible { opacity: 1; transform: translateY(0); }
    .reveal-delay-1 { transition-delay: 0.15s; }
    .reveal-delay-2 { transition-delay: 0.3s; }
    .reveal-delay-3 { transition-delay: 0.45s; }
 
    /* ── Responsive ── */
    @media (max-width: 900px) {
      .nav-links { display: none; }
      .nav-hamburger { display: flex; }
      .about-grid { grid-template-columns: 1fr; }
      .about-sticky { position: static; }
      .about-avatar { max-width: 280px; }
      .timeline-item { grid-template-columns: 1fr; gap: 0.5rem; }
      .timeline-item::before { display: none; }
      .timeline-date { padding-left: 0; }
      .projects-grid { grid-template-columns: 1fr; }
      .project-card:nth-child(n) { grid-column: span 1; }
      .contact-inner { grid-template-columns: 1fr; }
      .pub-item { grid-template-columns: 60px 1fr; gap: 1rem; }
    }
    @media (max-width: 600px) {
      .hero-name { font-size: clamp(2.8rem, 12vw, 4.5rem); }
      footer { flex-direction: column; align-items: flex-start; }
    }
    @media (hover: none) {
      body { cursor: auto; }
      .cursor { display: none; }
    }
  </style>
</head>
<body>
 
  <!-- Custom Cursor -->
  <div class="cursor">
    <div class="cursor-dot" id="cursorDot"></div>
    <div class="cursor-ring" id="cursorRing"></div>
  </div>
 
  <!-- Navigation -->
  <nav id="navbar">
    <a href="#hero" class="nav-logo">A<span>.</span>M</a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#publications">Research</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <button class="nav-hamburger" id="hamburger" aria-label="Menu">
      <span></span><span></span><span></span>
    </button>
  </nav>
 
  <!-- Mobile Menu -->
  <div class="mobile-menu" id="mobileMenu">
    <a href="#about" class="mobile-nav-link">About</a>
    <a href="#experience" class="mobile-nav-link">Experience</a>
    <a href="#projects" class="mobile-nav-link">Projects</a>
    <a href="#publications" class="mobile-nav-link">Research</a>
    <a href="#contact" class="mobile-nav-link">Contact</a>
  </div>
 
  <!-- ── HERO ── -->
  <section id="hero">
    <div class="hero-bg-number">AM</div>
    <div class="container">
      <p class="hero-label">Available for opportunities · 2025</p>
      <h1 class="hero-name">Alex<br /><em>Morgan</em></h1>
      <p class="hero-tagline">Full-Stack Engineer & Researcher. Building robust systems at the intersection of AI and human-computer interaction.</p>
      <div class="hero-cta">
        <a href="#projects" class="btn btn-primary"><span>View My Work</span></a>
        <a href="#contact" class="btn btn-outline">Get In Touch</a>
      </div>
    </div>
    <div class="hero-scroll">
      <div class="scroll-line"></div>
      <span>Scroll</span>
    </div>
  </section>
 
  <!-- ── ABOUT ── -->
  <section id="about">
    <div class="container">
      <div class="about-grid">
        <div class="about-sticky">
          <div class="section-label reveal">About Me</div>
          <h2 class="section-title reveal reveal-delay-1">Engineer.<br/>Researcher.<br/>Builder.</h2>
          <div class="about-avatar reveal reveal-delay-2">
            <div class="about-avatar-inner">
              <span class="avatar-initials">AM</span>
            </div>
          </div>
        </div>
        <div class="about-body">
          <p class="reveal">I'm a <strong>full-stack software engineer and researcher</strong> with 5+ years of experience building scalable web systems and conducting applied AI research. Currently pursuing my PhD at MIT CSAIL, where I work on human-centered machine learning.</p>
          <p class="reveal reveal-delay-1">Previously, I interned at <strong>Google DeepMind</strong> and <strong>Stripe</strong>, shipping products used by millions. My research has been published at NeurIPS, ICML, and ACL — I care about building technology that is not only powerful, but <strong>understandable and trustworthy.</strong></p>
          <p class="reveal reveal-delay-2">Outside the lab, I'm an occasional writer, an enthusiastic cook, and a very mediocre chess player. I believe the best engineers are those who can read both code and people.</p>
          <div class="skills-grid reveal reveal-delay-3">
            <div class="skill-chip">Python</div>
            <div class="skill-chip">TypeScript</div>
            <div class="skill-chip">React</div>
            <div class="skill-chip">Node.js</div>
            <div class="skill-chip">PyTorch</div>
            <div class="skill-chip">JAX</div>
            <div class="skill-chip">PostgreSQL</div>
            <div class="skill-chip">GraphQL</div>
            <div class="skill-chip">Kubernetes</div>
            <div class="skill-chip">AWS/GCP</div>
            <div class="skill-chip">Rust</div>
            <div class="skill-chip">Go</div>
          </div>
        </div>
      </div>
    </div>
  </section>
 
  <!-- ── EXPERIENCE ── -->
  <section id="experience">
    <div class="container">
      <div class="section-label reveal">Work History</div>
      <h2 class="section-title reveal reveal-delay-1">Where I've<br/>Made an Impact</h2>
      <div class="timeline">
        <div class="timeline-item reveal">
          <div class="timeline-date">2022 – Present</div>
          <div>
            <div class="timeline-role">PhD Researcher — CSAIL</div>
            <div class="timeline-org">MIT · Cambridge, MA</div>
            <p class="timeline-desc">Conducting research on interpretability and alignment in large language models. Developed novel probing techniques for understanding internal representations. Advisor: Prof. Sarah Chen. NSF GRFP Fellow.</p>
            <div class="timeline-tags">
              <span class="tag">LLM Interpretability</span>
              <span class="tag">PyTorch</span>
              <span class="tag">Research</span>
            </div>
          </div>
        </div>
        <div class="timeline-item reveal reveal-delay-1">
          <div class="timeline-date">Summer 2023</div>
          <div>
            <div class="timeline-role">Research Intern</div>
            <div class="timeline-org">Google DeepMind · London, UK</div>
            <p class="timeline-desc">Worked on the Gemini evaluation team. Designed benchmark suites for measuring compositional reasoning and factual grounding. Contributed to internal red-teaming frameworks.</p>
            <div class="timeline-tags">
              <span class="tag">JAX</span>
              <span class="tag">Benchmarking</span>
              <span class="tag">Safety</span>
            </div>
          </div>
        </div>
        <div class="timeline-item reveal reveal-delay-2">
          <div class="timeline-date">2020 – 2022</div>
          <div>
            <div class="timeline-role">Software Engineer II</div>
            <div class="timeline-org">Stripe · San Francisco, CA</div>
            <p class="timeline-desc">Led frontend architecture for the Stripe Dashboard's reporting suite. Reduced P95 load time by 62% through lazy loading and edge caching. Mentored 3 junior engineers; co-authored internal design system.</p>
            <div class="timeline-tags">
              <span class="tag">TypeScript</span>
              <span class="tag">React</span>
              <span class="tag">Performance</span>
              <span class="tag">GraphQL</span>
            </div>
          </div>
        </div>
        <div class="timeline-item reveal reveal-delay-3">
          <div class="timeline-date">2019 – 2020</div>
          <div>
            <div class="timeline-role">Software Engineer</div>
            <div class="timeline-org">Figma · San Francisco, CA</div>
            <p class="timeline-desc">Worked on real-time collaboration infrastructure using WebSockets and CRDTs. Contributed to the plugin API system, enabling a third-party ecosystem that grew to 500+ plugins within 6 months.</p>
            <div class="timeline-tags">
              <span class="tag">CRDTs</span>
              <span class="tag">WebSockets</span>
              <span class="tag">TypeScript</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
 
  <!-- ── PROJECTS ── -->
  <section id="projects">
    <div class="container">
      <div class="projects-header">
        <div>
          <div class="section-label reveal">Selected Work</div>
          <h2 class="section-title reveal reveal-delay-1">Projects &<br/>Experiments</h2>
        </div>
        <a href="#" class="view-all reveal reveal-delay-2">View All Projects →</a>
      </div>
      <div class="projects-grid">
        <div class="project-card reveal">
          <div class="project-visual">
            <div class="project-visual-inner pv-1">
              <div class="pv-icon">🔭</div>
            </div>
          </div>
          <div class="project-body">
            <div class="project-number">01 / Featured</div>
            <div class="project-title">LensAI — Multimodal Search Engine</div>
            <p class="project-desc">A semantic search engine combining CLIP embeddings with retrieval-augmented generation. Supports image, text, and audio queries across a 50M+ item corpus with sub-100ms latency.</p>
            <div class="project-footer">
              <div class="project-stack">
                <span class="stack-tag">Python</span>
                <span class="stack-tag">CLIP</span>
                <span class="stack-tag">Faiss</span>
                <span class="stack-tag">FastAPI</span>
              </div>
              <div class="project-links">
                <a href="#" class="project-link">GitHub</a>
                <a href="#" class="project-link">Demo →</a>
              </div>
            </div>
          </div>
        </div>
        <div class="project-card reveal reveal-delay-1">
          <div class="project-visual">
            <div class="project-visual-inner pv-2">
              <div class="pv-icon">📊</div>
            </div>
          </div>
          <div class="project-body">
            <div class="project-number">02</div>
            <div class="project-title">Arbor — Financial Data Viz</div>
            <p class="project-desc">Open-source charting library for financial time series data. 15k GitHub stars, used by fintechs and hedge funds.</p>
            <div class="project-footer">
              <div class="project-stack">
                <span class="stack-tag">TypeScript</span>
                <span class="stack-tag">D3.js</span>
                <span class="stack-tag">WebGL</span>
              </div>
              <div class="project-links">
                <a href="#" class="project-link">GitHub</a>
              </div>
            </div>
          </div>
        </div>
        <div class="project-card reveal reveal-delay-2">
          <div class="project-visual">
            <div class="project-visual-inner pv-3">
              <div class="pv-icon">🌱</div>
            </div>
          </div>
          <div class="project-body">
            <div class="project-number">03</div>
            <div class="project-title">Canopy — Carbon Footprint Tracker</div>
            <p class="project-desc">Mobile app that uses ML to estimate personal carbon emissions from receipt photos and bank statements. 20k+ active users.</p>
            <div class="project-footer">
              <div class="project-stack">
                <span class="stack-tag">React Native</span>
                <span class="stack-tag">PyTorch</span>
                <span class="stack-tag">AWS</span>
              </div>
              <div class="project-links">
                <a href="#" class="project-link">GitHub</a>
                <a href="#" class="project-link">App Store →</a>
              </div>
            </div>
          </div>
        </div>
        <div class="project-card reveal reveal-delay-3">
          <div class="project-visual">
            <div class="project-visual-inner pv-4">
              <div class="pv-icon">🧬</div>
            </div>
          </div>
          <div class="project-body">
            <div class="project-number">04 / Featured</div>
            <div class="project-title">ProbeKit — LLM Interpretability Toolkit</div>
            <p class="project-desc">A Python library for probing internal representations of transformer-based language models. Implements 12 probing methodologies, used in 40+ academic papers. Featured at NeurIPS 2023 workshop.</p>
            <div class="project-footer">
              <div class="project-stack">
                <span class="stack-tag">Python</span>
                <span class="stack-tag">PyTorch</span>
                <span class="stack-tag">HuggingFace</span>
                <span class="stack-tag">Scikit-learn</span>
              </div>
              <div class="project-links">
                <a href="#" class="project-link">GitHub</a>
                <a href="#" class="project-link">Docs →</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
 
  <!-- ── PUBLICATIONS ── -->
  <section id="publications">
    <div class="container">
      <div class="section-label reveal">Academic Work</div>
      <h2 class="section-title reveal reveal-delay-1">Selected<br/>Publications</h2>
      <div class="pub-list">
        <div class="pub-item reveal">
          <div class="pub-year">2024</div>
          <div>
            <div class="pub-title">Probing Factual Consistency in Large Language Models via Contrastive Activation Analysis <span class="pub-badge">Best Paper</span></div>
            <div class="pub-venue">NeurIPS 2024 · Advances in Neural Information Processing Systems</div>
            <div class="pub-authors"><strong>A. Morgan</strong>, S. Chen, R. Patel, J. Liu</div>
          </div>
        </div>
        <div class="pub-item reveal reveal-delay-1">
          <div class="pub-year">2023</div>
          <div>
            <div class="pub-title">Sparse Concept Bottlenecks for Interpretable Neural Networks</div>
            <div class="pub-venue">ICML 2023 · International Conference on Machine Learning</div>
            <div class="pub-authors"><strong>A. Morgan</strong>, S. Chen</div>
          </div>
        </div>
        <div class="pub-item reveal reveal-delay-2">
          <div class="pub-year">2023</div>
          <div>
            <div class="pub-title">Towards Faithful Explanations for Text Classification under Noisy Labels</div>
            <div class="pub-venue">ACL 2023 · Annual Meeting of the Association for Computational Linguistics</div>
            <div class="pub-authors">R. Patel, <strong>A. Morgan</strong>, K. Yamada</div>
          </div>
        </div>
        <div class="pub-item reveal reveal-delay-3">
          <div class="pub-year">2022</div>
          <div>
            <div class="pub-title">Data Augmentation for Low-Resource Neural Machine Translation Using Masked Language Modeling</div>
            <div class="pub-venue">EMNLP 2022 · Empirical Methods in NLP</div>
            <div class="pub-authors"><strong>A. Morgan</strong>, T. Kim, S. Chen</div>
          </div>
        </div>
      </div>
    </div>
  </section>
 
  <!-- ── CONTACT ── -->
  <section id="contact">
    <div class="container">
      <div class="contact-inner">
        <div>
          <div class="section-label reveal">Get In Touch</div>
          <h2 class="contact-headline reveal reveal-delay-1">Let's Build<br/><em>Something<br/>Together</em></h2>
          <p class="contact-sub reveal reveal-delay-2">Whether you have a research collaboration in mind, an engineering challenge, or just want to chat — my inbox is always open.</p>
          <div class="contact-links reveal reveal-delay-3">
            <a href="mailto:alex@morgan.dev" class="contact-link-item">
              <span class="contact-link-icon">✉</span>
              alex@morgan.dev
            </a>
            <a href="https://github.com" target="_blank" class="contact-link-item">
              <span class="contact-link-icon">◈</span>
              github.com/alexmorgan
            </a>
            <a href="https://linkedin.com" target="_blank" class="contact-link-item">
              <span class="contact-link-icon">◆</span>
              linkedin.com/in/alexmorgan
            </a>
            <a href="#" class="contact-link-item">
              <span class="contact-link-icon">◉</span>
              Google Scholar Profile
            </a>
          </div>
        </div>
        <div class="reveal reveal-delay-1">
          <form class="contact-form" onsubmit="handleSubmit(event)">
            <div class="form-group">
              <label class="form-label" for="name">Name</label>
              <input class="form-input" type="text" id="name" placeholder="Your name" required />
            </div>
            <div class="form-group">
              <label class="form-label" for="email">Email</label>
              <input class="form-input" type="email" id="email" placeholder="your@email.com" required />
            </div>
            <div class="form-group">
              <label class="form-label" for="subject">Subject</label>
              <input class="form-input" type="text" id="subject" placeholder="What's this about?" />
            </div>
            <div class="form-group">
              <label class="form-label" for="message">Message</label>
              <textarea class="form-textarea" id="message" placeholder="Tell me more..." required></textarea>
            </div>
            <button type="submit" class="btn btn-primary form-btn"><span>Send Message →</span></button>
          </form>
        </div>
      </div>
    </div>
  </section>
 
  <!-- ── FOOTER ── -->
  <footer>
    <p class="footer-copy">© 2025 Alex Morgan. All rights reserved.</p>
    <p class="footer-made">Designed & built with care. <a href="https://github.com" target="_blank">View source →</a></p>
  </footer>
 
  <script>
    // ── Cursor ──
    const dot = document.getElementById('cursorDot');
    const ring = document.getElementById('cursorRing');
    let mouseX = 0, mouseY = 0, ringX = 0, ringY = 0;
    document.addEventListener('mousemove', e => { mouseX = e.clientX; mouseY = e.clientY; });
    const hoverEls = document.querySelectorAll('a, button, .skill-chip, .project-card, .pub-item');
    hoverEls.forEach(el => {
      el.addEventListener('mouseenter', () => ring.classList.add('hover'));
      el.addEventListener('mouseleave', () => ring.classList.remove('hover'));
    });
    function animateCursor() {
      dot.style.left = mouseX + 'px'; dot.style.top = mouseY + 'px';
      ringX += (mouseX - ringX) * 0.12; ringY += (mouseY - ringY) * 0.12;
      ring.style.left = ringX + 'px'; ring.style.top = ringY + 'px';
      requestAnimationFrame(animateCursor);
    }
    animateCursor();
 
    // ── Navbar scroll ──
    const navbar = document.getElementById('navbar');
    window.addEventListener('scroll', () => {
      navbar.classList.toggle('scrolled', window.scrollY > 60);
    });
 
    // ── Mobile menu ──
    const hamburger = document.getElementById('hamburger');
    const mobileMenu = document.getElementById('mobileMenu');
    hamburger.addEventListener('click', () => {
      hamburger.classList.toggle('open');
      mobileMenu.classList.toggle('open');
      document.body.style.overflow = mobileMenu.classList.contains('open') ? 'hidden' : '';
    });
    document.querySelectorAll('.mobile-nav-link').forEach(link => {
      link.addEventListener('click', () => {
        hamburger.classList.remove('open');
        mobileMenu.classList.remove('open');
        document.body.style.overflow = '';
      });
    });
 
    // ── Scroll reveal ──
    const revealEls = document.querySelectorAll('.reveal');
    const io = new IntersectionObserver(entries => {
      entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); } });
    }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });
    revealEls.forEach(el => io.observe(el));
 
    // ── Contact form ──
    function handleSubmit(e) {
      e.preventDefault();
      const btn = e.target.querySelector('button span');
      btn.textContent = 'Sent! ✓';
      setTimeout(() => { btn.textContent = 'Send Message →'; e.target.reset(); }, 3000);
    }
  </script>
</body>
</html>
 
