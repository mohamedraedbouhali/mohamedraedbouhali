<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mohamed Raed Bouhali — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
:root {
  --cyan: #00D9FF;
  --cyan2: #00FFCC;
  --bg: #070B12;
  --bg2: #0D1320;
  --bg3: #111827;
  --glass: rgba(0,217,255,0.04);
  --glass-border: rgba(0,217,255,0.12);
  --text: #E8F4F8;
  --muted: #7A9BAD;
  --red: #FF4B6E;
  --gold: #FFD166;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  font-family: 'JetBrains Mono', monospace;
  background: var(--bg);
  color: var(--text);
  overflow-x: hidden;
  cursor: none;
}

/* CURSOR */
.cursor {
  width: 12px; height: 12px;
  border-radius: 50%;
  background: var(--cyan);
  position: fixed;
  pointer-events: none;
  z-index: 9999;
  mix-blend-mode: screen;
  transition: transform 0.1s ease;
}
.cursor-ring {
  width: 36px; height: 36px;
  border-radius: 50%;
  border: 1px solid rgba(0,217,255,0.5);
  position: fixed;
  pointer-events: none;
  z-index: 9998;
  transition: all 0.18s ease;
}

/* CANVAS */
#matrix-canvas {
  position: fixed; top:0; left:0; width:100%; height:100%;
  z-index: 0; opacity: 0.07; pointer-events: none;
}

/* NAV */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 18px 48px;
  backdrop-filter: blur(20px);
  background: rgba(7,11,18,0.8);
  border-bottom: 1px solid var(--glass-border);
  transition: padding 0.3s;
}
.nav-logo {
  font-family: 'Syne', sans-serif;
  font-weight: 800;
  font-size: 1.1rem;
  color: var(--cyan);
  letter-spacing: 0.05em;
  text-decoration: none;
}
.nav-links { display: flex; gap: 32px; list-style: none; }
.nav-links a {
  color: var(--muted);
  text-decoration: none;
  font-size: 0.72rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  transition: color 0.2s;
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute; left: 0; bottom: -3px;
  width: 0; height: 1px;
  background: var(--cyan);
  transition: width 0.3s;
}
.nav-links a:hover { color: var(--cyan); }
.nav-links a:hover::after { width: 100%; }

/* MAIN */
main { position: relative; z-index: 1; }

/* SECTION BASE */
section { padding: 100px 48px; max-width: 1200px; margin: 0 auto; }

/* HERO */
#hero {
  min-height: 100vh;
  display: flex; align-items: center;
  padding: 0 48px;
  max-width: 1200px; margin: 0 auto;
  position: relative;
}
.hero-tag {
  font-size: 0.7rem;
  letter-spacing: 0.25em;
  color: var(--cyan);
  text-transform: uppercase;
  margin-bottom: 18px;
  opacity: 0;
  animation: fadeUp 0.8s 0.3s forwards;
}
.hero-tag span {
  display: inline-block;
  padding: 4px 12px;
  border: 1px solid var(--glass-border);
  border-radius: 2px;
  background: var(--glass);
}
h1.hero-name {
  font-family: 'Syne', sans-serif;
  font-size: clamp(2.8rem, 6vw, 5.5rem);
  font-weight: 800;
  line-height: 1.0;
  letter-spacing: -0.02em;
  margin-bottom: 12px;
  opacity: 0;
  animation: fadeUp 0.8s 0.5s forwards;
}
h1.hero-name .accent { color: var(--cyan); }
.hero-subtitle {
  font-size: clamp(0.85rem, 1.5vw, 1.05rem);
  color: var(--muted);
  margin-bottom: 32px;
  opacity: 0;
  animation: fadeUp 0.8s 0.7s forwards;
}
.hero-typing {
  font-size: 1.1rem;
  color: var(--cyan2);
  margin-bottom: 48px;
  min-height: 1.6em;
  opacity: 0;
  animation: fadeUp 0.8s 0.9s forwards;
}
.cursor-blink {
  display: inline-block;
  width: 2px; height: 1.1em;
  background: var(--cyan);
  vertical-align: middle;
  animation: blink 0.9s infinite;
  margin-left: 2px;
}
.hero-cta {
  display: flex; gap: 16px; flex-wrap: wrap;
  opacity: 0;
  animation: fadeUp 0.8s 1.1s forwards;
}
.btn {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 12px 28px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.78rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  text-decoration: none;
  border-radius: 2px;
  transition: all 0.25s;
  position: relative;
  overflow: hidden;
}
.btn-primary {
  background: var(--cyan);
  color: var(--bg);
  font-weight: 600;
  border: 1px solid var(--cyan);
}
.btn-primary:hover {
  background: transparent;
  color: var(--cyan);
  box-shadow: 0 0 24px rgba(0,217,255,0.3);
}
.btn-outline {
  background: transparent;
  color: var(--muted);
  border: 1px solid var(--glass-border);
}
.btn-outline:hover {
  border-color: var(--cyan);
  color: var(--cyan);
}

.hero-scroll {
  position: absolute; bottom: 40px; left: 50%;
  transform: translateX(-50%);
  display: flex; flex-direction: column; align-items: center; gap: 8px;
  opacity: 0;
  animation: fadeUp 0.8s 1.4s forwards;
  color: var(--muted);
  font-size: 0.65rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
}
.scroll-line {
  width: 1px; height: 50px;
  background: linear-gradient(to bottom, var(--cyan), transparent);
  animation: scrollPulse 2s infinite;
}

/* SECTION TITLE */
.section-title {
  font-family: 'Syne', sans-serif;
  font-weight: 800;
  font-size: clamp(2rem, 4vw, 3rem);
  margin-bottom: 8px;
  letter-spacing: -0.02em;
}
.section-title .accent { color: var(--cyan); }
.section-line {
  width: 48px; height: 3px;
  background: linear-gradient(to right, var(--cyan), transparent);
  margin-bottom: 48px;
}
.section-label {
  font-size: 0.68rem;
  letter-spacing: 0.2em;
  color: var(--cyan);
  text-transform: uppercase;
  margin-bottom: 10px;
}

/* ABOUT */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
  align-items: start;
}
.about-text p {
  color: var(--muted);
  line-height: 1.8;
  font-size: 0.88rem;
  margin-bottom: 20px;
}
.about-text p strong { color: var(--text); }
.stat-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-top: 32px;
}
.stat-card {
  padding: 20px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 4px;
  transition: all 0.3s;
}
.stat-card:hover {
  border-color: var(--cyan);
  background: rgba(0,217,255,0.06);
  transform: translateY(-3px);
}
.stat-num {
  font-family: 'Syne', sans-serif;
  font-size: 2rem;
  font-weight: 800;
  color: var(--cyan);
  line-height: 1;
}
.stat-label {
  font-size: 0.7rem;
  color: var(--muted);
  margin-top: 4px;
  letter-spacing: 0.05em;
}
.lang-pills {
  display: flex; flex-wrap: wrap; gap: 8px;
  margin-top: 20px;
}
.lang-pill {
  padding: 6px 14px;
  font-size: 0.7rem;
  border-radius: 100px;
  border: 1px solid var(--glass-border);
  color: var(--muted);
  letter-spacing: 0.05em;
  transition: all 0.2s;
}
.lang-pill:hover {
  border-color: var(--cyan);
  color: var(--cyan);
  background: rgba(0,217,255,0.05);
}
.lang-pill .flag { margin-right: 6px; }

/* SKILLS */
.skills-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
}
.skill-group {
  padding: 28px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 6px;
  transition: all 0.3s;
  position: relative;
  overflow: hidden;
}
.skill-group::before {
  content: '';
  position: absolute; top: 0; left: 0;
  width: 3px; height: 0;
  background: linear-gradient(to bottom, var(--cyan), var(--cyan2));
  transition: height 0.4s;
}
.skill-group:hover::before { height: 100%; }
.skill-group:hover {
  border-color: rgba(0,217,255,0.25);
  transform: translateY(-4px);
  box-shadow: 0 16px 40px rgba(0,217,255,0.08);
}
.skill-group-title {
  font-size: 0.68rem;
  letter-spacing: 0.2em;
  color: var(--cyan);
  text-transform: uppercase;
  margin-bottom: 20px;
  display: flex; align-items: center; gap: 8px;
}
.skill-tags {
  display: flex; flex-wrap: wrap; gap: 8px;
}
.skill-tag {
  padding: 5px 10px;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 3px;
  font-size: 0.68rem;
  color: var(--text);
  letter-spacing: 0.03em;
  transition: all 0.2s;
}
.skill-tag:hover {
  background: rgba(0,217,255,0.1);
  border-color: var(--cyan);
  color: var(--cyan);
}

/* EXPERIENCE */
.timeline {
  position: relative;
  padding-left: 32px;
}
.timeline::before {
  content: '';
  position: absolute; left: 0; top: 0; bottom: 0;
  width: 1px;
  background: linear-gradient(to bottom, var(--cyan), transparent);
}
.timeline-item {
  position: relative;
  margin-bottom: 48px;
  opacity: 0;
  transform: translateX(-20px);
  transition: all 0.6s;
}
.timeline-item.visible {
  opacity: 1;
  transform: translateX(0);
}
.timeline-dot {
  position: absolute;
  left: -39px; top: 6px;
  width: 14px; height: 14px;
  border-radius: 50%;
  border: 2px solid var(--cyan);
  background: var(--bg);
  transition: all 0.3s;
}
.timeline-item:hover .timeline-dot {
  background: var(--cyan);
  box-shadow: 0 0 12px var(--cyan);
}
.timeline-meta {
  font-size: 0.68rem;
  color: var(--cyan);
  letter-spacing: 0.1em;
  margin-bottom: 8px;
}
.timeline-company {
  font-family: 'Syne', sans-serif;
  font-size: 1.2rem;
  font-weight: 700;
  margin-bottom: 4px;
}
.timeline-role {
  font-size: 0.78rem;
  color: var(--muted);
  margin-bottom: 16px;
}
.timeline-body {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 6px;
  padding: 20px;
}
.timeline-body ul {
  list-style: none;
  display: flex; flex-direction: column; gap: 8px;
}
.timeline-body li {
  font-size: 0.78rem;
  color: var(--muted);
  display: flex; align-items: flex-start; gap: 10px;
  line-height: 1.6;
}
.timeline-body li::before {
  content: '→';
  color: var(--cyan);
  font-size: 0.7rem;
  margin-top: 2px;
  flex-shrink: 0;
}

/* CERTS */
.certs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 20px;
}
.cert-card {
  padding: 24px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 6px;
  position: relative;
  overflow: hidden;
  transition: all 0.3s;
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.5s;
}
.cert-card.visible {
  opacity: 1;
  transform: translateY(0);
}
.cert-card:hover {
  border-color: rgba(0,217,255,0.3);
  box-shadow: 0 12px 32px rgba(0,217,255,0.07);
  transform: translateY(-4px);
}
.cert-card::after {
  content: '';
  position: absolute; top: 0; right: 0;
  width: 60px; height: 60px;
  background: radial-gradient(circle, rgba(0,217,255,0.08), transparent);
  border-radius: 50%;
}
.cert-status {
  font-size: 0.65rem;
  padding: 3px 10px;
  border-radius: 100px;
  display: inline-block;
  margin-bottom: 12px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
.cert-status.done {
  background: rgba(0,255,180,0.1);
  color: #00FFB4;
  border: 1px solid rgba(0,255,180,0.2);
}
.cert-status.progress {
  background: rgba(255,193,7,0.1);
  color: var(--gold);
  border: 1px solid rgba(255,193,7,0.2);
}
.cert-name {
  font-family: 'Syne', sans-serif;
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 6px;
}
.cert-issuer {
  font-size: 0.7rem;
  color: var(--muted);
}
.cert-date {
  font-size: 0.68rem;
  color: var(--cyan);
  margin-top: 12px;
  letter-spacing: 0.05em;
}

/* PROJECTS */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 24px;
}
.project-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 8px;
  overflow: hidden;
  transition: all 0.35s;
  opacity: 0; transform: translateY(24px);
}
.project-card.visible { opacity: 1; transform: translateY(0); }
.project-card:hover {
  border-color: rgba(0,217,255,0.3);
  box-shadow: 0 20px 50px rgba(0,0,0,0.4), 0 0 0 1px rgba(0,217,255,0.1);
  transform: translateY(-6px);
}
.project-header {
  padding: 24px 24px 0;
  display: flex; align-items: flex-start; justify-content: space-between;
}
.project-icon {
  font-size: 1.8rem;
  line-height: 1;
}
.project-link {
  width: 32px; height: 32px;
  display: flex; align-items: center; justify-content: center;
  border: 1px solid var(--glass-border);
  border-radius: 50%;
  color: var(--muted);
  text-decoration: none;
  font-size: 0.8rem;
  transition: all 0.2s;
}
.project-link:hover {
  background: var(--cyan);
  color: var(--bg);
  border-color: var(--cyan);
}
.project-body { padding: 16px 24px 24px; }
.project-name {
  font-family: 'Syne', sans-serif;
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 8px;
}
.project-desc {
  font-size: 0.76rem;
  color: var(--muted);
  line-height: 1.7;
  margin-bottom: 16px;
}
.project-tags {
  display: flex; flex-wrap: wrap; gap: 6px;
}
.project-tag {
  padding: 3px 10px;
  border-radius: 100px;
  font-size: 0.62rem;
  letter-spacing: 0.08em;
  border: 1px solid rgba(0,217,255,0.2);
  color: var(--cyan);
  background: rgba(0,217,255,0.05);
}

/* CONTACT */
.contact-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: center;
}
.contact-text p {
  color: var(--muted);
  font-size: 0.88rem;
  line-height: 1.8;
  margin-bottom: 16px;
}
.contact-links {
  display: flex; flex-direction: column; gap: 14px;
  margin-top: 32px;
}
.contact-link {
  display: flex; align-items: center; gap: 16px;
  padding: 16px 20px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 6px;
  text-decoration: none;
  color: var(--text);
  font-size: 0.8rem;
  transition: all 0.25s;
}
.contact-link:hover {
  border-color: var(--cyan);
  color: var(--cyan);
  background: rgba(0,217,255,0.05);
  transform: translateX(6px);
}
.contact-link-icon {
  width: 36px; height: 36px;
  display: flex; align-items: center; justify-content: center;
  border-radius: 50%;
  background: rgba(0,217,255,0.1);
  font-size: 0.95rem;
  flex-shrink: 0;
}
.contact-link-text { flex: 1; }
.contact-link-label { font-size: 0.62rem; color: var(--muted); letter-spacing: 0.1em; }
.contact-link-value { font-size: 0.82rem; margin-top: 2px; }

/* LEADERSHIP */
.leadership-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 16px;
}
.leadership-card {
  padding: 20px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 6px;
  transition: all 0.3s;
  opacity: 0; transform: translateY(16px);
}
.leadership-card.visible { opacity: 1; transform: translateY(0); }
.leadership-card:hover {
  border-color: rgba(0,217,255,0.25);
  transform: translateY(-3px);
}
.l-icon { font-size: 1.3rem; margin-bottom: 10px; }
.l-role {
  font-family: 'Syne', sans-serif;
  font-size: 0.88rem;
  font-weight: 700;
  margin-bottom: 4px;
}
.l-org { font-size: 0.72rem; color: var(--cyan); margin-bottom: 4px; }
.l-period { font-size: 0.68rem; color: var(--muted); }

/* FOOTER */
footer {
  text-align: center;
  padding: 40px;
  border-top: 1px solid var(--glass-border);
  color: var(--muted);
  font-size: 0.72rem;
  letter-spacing: 0.08em;
  position: relative; z-index: 1;
}

/* ANIMATIONS */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to { opacity: 1; transform: translateY(0); }
}
@keyframes blink {
  0%, 100% { opacity: 1; } 50% { opacity: 0; }
}
@keyframes scrollPulse {
  0%, 100% { opacity: 1; transform: scaleY(1); }
  50% { opacity: 0.4; transform: scaleY(0.7); }
}

/* GLITCH EFFECT */
.glitch {
  position: relative;
}
.glitch::before, .glitch::after {
  content: attr(data-text);
  position: absolute; top: 0; left: 0;
  width: 100%; height: 100%;
  clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
}
.glitch::before {
  left: 2px;
  color: var(--red);
  animation: glitch1 4s infinite;
}
.glitch::after {
  left: -2px;
  color: var(--cyan);
  animation: glitch2 4s infinite;
  clip-path: polygon(0 60%, 100% 60%, 100% 100%, 0 100%);
}
@keyframes glitch1 {
  0%,94%,100% { opacity: 0; transform: none; }
  95% { opacity: 0.8; transform: translateX(-3px) skewX(-2deg); }
  97% { opacity: 0; transform: translateX(3px); }
}
@keyframes glitch2 {
  0%,91%,100% { opacity: 0; transform: none; }
  92% { opacity: 0.8; transform: translateX(3px) skewX(2deg); }
  94% { opacity: 0; transform: translateX(-3px); }
}

/* RESPONSIVE */
@media (max-width: 768px) {
  nav { padding: 16px 24px; }
  .nav-links { display: none; }
  section, #hero { padding: 80px 24px; }
  .about-grid, .contact-wrapper { grid-template-columns: 1fr; }
}

/* GLOW PULSE on hover for key elements */
.glow-on-hover:hover {
  box-shadow: 0 0 20px rgba(0,217,255,0.2);
}
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursor-ring"></div>

<canvas id="matrix-canvas"></canvas>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">MRBI</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#certifications">Certs</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<div id="hero" style="position:relative;z-index:1;">
  <div>
    <div class="hero-tag"><span>// Available for opportunities</span></div>
    <h1 class="hero-name glitch" data-text="Mohamed Raed">
      Mohamed <span class="accent">Raed</span><br/>Bouhali
    </h1>
    <p class="hero-subtitle">Data Science & AI Engineer &nbsp;·&nbsp; Full-Stack Developer &nbsp;·&nbsp; DevOps</p>
    <div class="hero-typing">
      <span id="typing-text"></span><span class="cursor-blink"></span>
    </div>
    <div class="hero-cta">
      <a href="https://portfeliomrbi.vercel.app/" target="_blank" class="btn btn-primary">
        <span>🌐</span> Portfolio
      </a>
      <a href="https://github.com/mohamedraedbouhali" target="_blank" class="btn btn-outline">
        <span>⌥</span> GitHub
      </a>
      <a href="https://www.linkedin.com/in/bouhali-mohamed-raed/" target="_blank" class="btn btn-outline">
        <span>→</span> LinkedIn
      </a>
      <a href="mailto:raedbouhali@gmail.com" class="btn btn-outline">
        <span>✉</span> Contact
      </a>
    </div>
  </div>
  <div class="hero-scroll">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="section-label">// 01 &nbsp; Who I Am</div>
  <h2 class="section-title">About <span class="accent">Me</span></h2>
  <div class="section-line"></div>
  <div class="about-grid">
    <div class="about-text">
      <p>I'm <strong>Mohamed Raed Bouhali</strong>, a Data Science & AI Engineering student at <strong>TEK-UP University</strong>, Tunis — passionate about building intelligent, scalable systems that sit at the intersection of AI, full-stack development, and DevOps.</p>
      <p>From training transformer-based chatbots to deploying containerized microservices and building end-to-end web platforms, I thrive on <strong>solving complex problems</strong> with clean, impactful technology.</p>
      <p>I'm a <strong>RHCSA</strong>, <strong>PCAP™</strong>, and <strong>EX188</strong> certified engineer, currently pursuing AWS and Power BI certifications. I lead as Treasurer of the IEEE TEK-UP Student Branch and am active in Securinets and IEEE Education Society.</p>
      <div class="lang-pills">
        <div class="lang-pill"><span class="flag">🇸🇦</span> Arabic — Native</div>
        <div class="lang-pill"><span class="flag">🇬🇧</span> English — B2</div>
        <div class="lang-pill"><span class="flag">🇫🇷</span> French — B2</div>
        <div class="lang-pill"><span class="flag">🇩🇪</span> German — B1</div>
      </div>
    </div>
    <div>
      <div class="stat-grid">
        <div class="stat-card">
          <div class="stat-num">3+</div>
          <div class="stat-label">Internships completed</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">5+</div>
          <div class="stat-label">Featured projects</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">3</div>
          <div class="stat-label">Active certifications</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">10+</div>
          <div class="stat-label">Years of leadership</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-label">// 02 &nbsp; What I Work With</div>
  <h2 class="section-title">Tech <span class="accent">Stack</span></h2>
  <div class="section-line"></div>
  <div class="skills-container">
    <div class="skill-group">
      <div class="skill-group-title">⌨️ &nbsp; Languages</div>
      <div class="skill-tags">
        <span class="skill-tag">Python</span><span class="skill-tag">Java</span>
        <span class="skill-tag">JavaScript</span><span class="skill-tag">PHP</span>
        <span class="skill-tag">C</span><span class="skill-tag">SQL</span>
        <span class="skill-tag">HTML5</span><span class="skill-tag">CSS3</span>
      </div>
    </div>
    <div class="skill-group">
      <div class="skill-group-title">🤖 &nbsp; AI & Data Science</div>
      <div class="skill-tags">
        <span class="skill-tag">TensorFlow</span><span class="skill-tag">PyTorch</span>
        <span class="skill-tag">Scikit-Learn</span><span class="skill-tag">NLP</span>
        <span class="skill-tag">Power BI</span><span class="skill-tag">Data Mining</span>
        <span class="skill-tag">Transformers</span>
      </div>
    </div>
    <div class="skill-group">
      <div class="skill-group-title">🌐 &nbsp; Frameworks & Databases</div>
      <div class="skill-tags">
        <span class="skill-tag">React.js</span><span class="skill-tag">Django REST</span>
        <span class="skill-tag">Symfony</span><span class="skill-tag">.NET</span>
        <span class="skill-tag">MySQL</span><span class="skill-tag">PostgreSQL</span>
      </div>
    </div>
    <div class="skill-group">
      <div class="skill-group-title">☁️ &nbsp; DevOps & Cloud</div>
      <div class="skill-tags">
        <span class="skill-tag">Docker</span><span class="skill-tag">Kubernetes</span>
        <span class="skill-tag">Linux</span><span class="skill-tag">Red Hat</span>
        <span class="skill-tag">AWS</span><span class="skill-tag">Azure</span>
        <span class="skill-tag">CI/CD</span><span class="skill-tag">Git</span>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-label">// 03 &nbsp; Where I've Worked</div>
  <h2 class="section-title">Work <span class="accent">Experience</span></h2>
  <div class="section-line"></div>
  <div class="timeline">
    <div class="timeline-item">
      <div class="timeline-dot"></div>
      <div class="timeline-meta">Aug 2025 – Sep 2025 &nbsp;·&nbsp; Tunis, Tunisia</div>
      <div class="timeline-company">VMD</div>
      <div class="timeline-role">DevOps Intern</div>
      <div class="timeline-body">
        <ul>
          <li>Accelerated deployment pipelines — reduced release cycle time for features, bug fixes, and updates</li>
          <li>Automated testing integration to catch bugs early and ensure stable, production-ready builds</li>
          <li>Streamlined developer collaboration workflows enabling more frequent, low-friction code integration</li>
          <li>Ensured build consistency through CI/CD best practices and repeatable deployments</li>
        </ul>
      </div>
    </div>
    <div class="timeline-item">
      <div class="timeline-dot"></div>
      <div class="timeline-meta">Jul 2025 – Aug 2025 &nbsp;·&nbsp; Ariana, Tunisia</div>
      <div class="timeline-company">Progress Engineering</div>
      <div class="timeline-role">Full-Stack Intern</div>
      <div class="timeline-body">
        <ul>
          <li>Built backend and frontend modules for managing and tracking business opportunities end-to-end</li>
          <li>Implemented authentication, user management, and advanced data filtering functionalities</li>
          <li>Defined technical architecture based on functional analysis and stakeholder requirements</li>
          <li>Conducted functional testing, resolved anomalies, and produced full technical documentation</li>
        </ul>
      </div>
    </div>
    <div class="timeline-item">
      <div class="timeline-dot"></div>
      <div class="timeline-meta">Jul 2024 – Aug 2024 &nbsp;·&nbsp; Ben Arous, Tunisia</div>
      <div class="timeline-company">ALL Circuits</div>
      <div class="timeline-role">Electronics Intern</div>
      <div class="timeline-body">
        <ul>
          <li>Participated in manual and automated PCB assembly (CMS and through-hole components)</li>
          <li>Executed verification and quality control tests on produced electronic boards</li>
          <li>Studied industrial standards and certifications (ISO, IPC) related to electronics manufacturing</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<!-- CERTS -->
<section id="certifications">
  <div class="section-label">// 04 &nbsp; Credentials</div>
  <h2 class="section-title">Certifi<span class="accent">cations</span></h2>
  <div class="section-line"></div>
  <div class="certs-grid">
    <div class="cert-card">
      <div class="cert-status done">✓ Certified</div>
      <div class="cert-name">RHCSA</div>
      <div class="cert-issuer">Red Hat Certified System Administrator</div>
      <div class="cert-date">Jul 2025</div>
    </div>
    <div class="cert-card">
      <div class="cert-status done">✓ Certified</div>
      <div class="cert-name">PCAP™</div>
      <div class="cert-issuer">Certified Associate Python Programmer — Python Institute</div>
      <div class="cert-date">Jan 2026</div>
    </div>
    <div class="cert-card">
      <div class="cert-status done">✓ Certified</div>
      <div class="cert-name">EX188 — RHSCS</div>
      <div class="cert-issuer">Red Hat Specialist in Containers</div>
      <div class="cert-date">Apr 2026</div>
    </div>
    <div class="cert-card">
      <div class="cert-status progress">⟳ In Progress</div>
      <div class="cert-name">AWS Certified</div>
      <div class="cert-issuer">AI Practitioner + Data Engineer — Amazon Web Services</div>
      <div class="cert-date">2026</div>
    </div>
    <div class="cert-card">
      <div class="cert-status progress">⟳ In Progress</div>
      <div class="cert-name">PL-300</div>
      <div class="cert-issuer">Microsoft Power BI Data Analyst + EJDS INE</div>
      <div class="cert-date">2026</div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-label">// 05 &nbsp; What I've Built</div>
  <h2 class="section-title">Featured <span class="accent">Projects</span></h2>
  <div class="section-line"></div>
  <div class="projects-grid">
    <div class="project-card">
      <div class="project-header">
        <div class="project-icon">⛱️</div>
        <a href="mailto:raedbouhali@gmail.com" class="project-link" title="Request Access">↗</a>
      </div>
      <div class="project-body">
        <div class="project-name">TUNISCO</div>
        <p class="project-desc">Full-featured tourism discovery platform showcasing Tunisia's destinations with interactive search, geolocation, user reviews, and curated travel itineraries.</p>
        <div class="project-tags">
          <span class="project-tag">PHP</span>
          <span class="project-tag">Symfony</span>
          <span class="project-tag">MySQL</span>
        </div>
      </div>
    </div>
    <div class="project-card">
      <div class="project-header">
        <div class="project-icon">🧙‍♂️</div>
        <a href="mailto:raedbouhali@gmail.com" class="project-link" title="Request Access">↗</a>
      </div>
      <div class="project-body">
        <div class="project-name">Wizard World</div>
        <p class="project-desc">Full-stack Harry Potter fan platform with e-commerce, wishlist, personalized recommendations, and a Hogwarts-themed UI. Decoupled DRF + React architecture.</p>
        <div class="project-tags">
          <span class="project-tag">Django REST</span>
          <span class="project-tag">React</span>
          <span class="project-tag">PostgreSQL</span>
        </div>
      </div>
    </div>
    <div class="project-card">
      <div class="project-header">
        <div class="project-icon">🤖</div>
        <a href="mailto:raedbouhali@gmail.com" class="project-link" title="Request Access">↗</a>
      </div>
      <div class="project-body">
        <div class="project-name">AI Conversational Chatbot</div>
        <p class="project-desc">Transformer-based seq2seq conversational agent supporting text & voice. Achieved 92% relevance score — significantly outperforming rule-based baselines.</p>
        <div class="project-tags">
          <span class="project-tag">TensorFlow</span>
          <span class="project-tag">PyTorch</span>
          <span class="project-tag">NLP</span>
        </div>
      </div>
    </div>
    <div class="project-card">
      <div class="project-header">
        <div class="project-icon">📊</div>
        <a href="mailto:raedbouhali@gmail.com" class="project-link" title="Request Access">↗</a>
      </div>
      <div class="project-body">
        <div class="project-name">Progress Opportunities</div>
        <p class="project-desc">Business management platform built during internship — full commercial pipeline tracking, KPI dashboard, notifications, role-based access, and PDF/Excel exports.</p>
        <div class="project-tags">
          <span class="project-tag">Symfony</span>
          <span class="project-tag">PHP</span>
          <span class="project-tag">MySQL</span>
        </div>
      </div>
    </div>
    <div class="project-card">
      <div class="project-header">
        <div class="project-icon">💀</div>
        <a href="mailto:raedbouhali@gmail.com" class="project-link" title="Request Access">↗</a>
      </div>
      <div class="project-body">
        <div class="project-name">Hangman Game</div>
        <p class="project-desc">Polished console-based Hangman in Java with full OOP design, categorized word banks, difficulty levels, real-time score tracking, and persistent leaderboard.</p>
        <div class="project-tags">
          <span class="project-tag">Java</span>
          <span class="project-tag">OOP</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- LEADERSHIP -->
<section id="leadership">
  <div class="section-label">// 06 &nbsp; Community</div>
  <h2 class="section-title">Leader<span class="accent">ship</span></h2>
  <div class="section-line"></div>
  <div class="leadership-grid">
    <div class="leadership-card"><div class="l-icon">💰</div><div class="l-role">Treasurer</div><div class="l-org">IEEE TEK-UP Student Branch</div><div class="l-period">2025 – Present</div></div>
    <div class="leadership-card"><div class="l-icon">🔐</div><div class="l-role">Member</div><div class="l-org">Securinets Tekup</div><div class="l-period">2024 – Present</div></div>
    <div class="leadership-card"><div class="l-icon">📚</div><div class="l-role">Member</div><div class="l-org">IEEE Education Society (EdSoc)</div><div class="l-period">2024 – Present</div></div>
    <div class="leadership-card"><div class="l-icon">❤️</div><div class="l-role">Member</div><div class="l-org">Tunisian Red Crescent</div><div class="l-period">2022 – 2024</div></div>
    <div class="leadership-card"><div class="l-icon">🌱</div><div class="l-role">Volunteer</div><div class="l-org">INJAZ Tunisia</div><div class="l-period">2021 – 2022</div></div>
    <div class="leadership-card"><div class="l-icon">🏕️</div><div class="l-role">Leader</div><div class="l-org">Tunisian Scouts</div><div class="l-period">2012 – 2022</div></div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-label">// 07 &nbsp; Get In Touch</div>
  <h2 class="section-title">Let's <span class="accent">Connect</span></h2>
  <div class="section-line"></div>
  <div class="contact-wrapper">
    <div class="contact-text">
      <p>Always open to collaborating on <strong>AI</strong>, <strong>Data Science</strong>, <strong>DevOps</strong>, or startup ventures. Whether it's a project, an opportunity, or just a tech chat — reach out.</p>
      <p>Currently based in <strong>Tunis, Tunisia</strong>.</p>
    </div>
    <div class="contact-links">
      <a href="mailto:raedbouhali@gmail.com" class="contact-link">
        <div class="contact-link-icon">✉</div>
        <div class="contact-link-text">
          <div class="contact-link-label">Email</div>
          <div class="contact-link-value">raedbouhali@gmail.com</div>
        </div>
        <span>→</span>
      </a>
      <a href="https://www.linkedin.com/in/bouhali-mohamed-raed/" target="_blank" class="contact-link">
        <div class="contact-link-icon">in</div>
        <div class="contact-link-text">
          <div class="contact-link-label">LinkedIn</div>
          <div class="contact-link-value">bouhali-mohamed-raed</div>
        </div>
        <span>→</span>
      </a>
      <a href="https://github.com/mohamedraedbouhali" target="_blank" class="contact-link">
        <div class="contact-link-icon">⌥</div>
        <div class="contact-link-text">
          <div class="contact-link-label">GitHub</div>
          <div class="contact-link-value">mohamedraedbouhali</div>
        </div>
        <span>→</span>
      </a>
      <a href="https://portfeliomrbi.vercel.app/" target="_blank" class="contact-link">
        <div class="contact-link-icon">🌐</div>
        <div class="contact-link-text">
          <div class="contact-link-label">Portfolio</div>
          <div class="contact-link-value">portfeliomrbi.vercel.app</div>
        </div>
        <span>→</span>
      </a>
      <a href="tel:+21626711810" class="contact-link">
        <div class="contact-link-icon">📱</div>
        <div class="contact-link-text">
          <div class="contact-link-label">Phone / WhatsApp</div>
          <div class="contact-link-value">+216 26 711 810</div>
        </div>
        <span>→</span>
      </a>
    </div>
  </div>
</section>

<footer>
  <p>© 2026 Mohamed Raed Bouhali &nbsp;·&nbsp; Designed & built with precision &nbsp;·&nbsp; Tunis, Tunisia</p>
</footer>

<script>
/* ---- CURSOR ---- */
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursor-ring');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
function animateCursor() {
  cursor.style.left = mx - 6 + 'px';
  cursor.style.top = my - 6 + 'px';
  rx += (mx - rx) * 0.12;
  ry += (my - ry) * 0.12;
  ring.style.left = rx - 18 + 'px';
  ring.style.top = ry - 18 + 'px';
  requestAnimationFrame(animateCursor);
}
animateCursor();
document.querySelectorAll('a, button').forEach(el => {
  el.addEventListener('mouseenter', () => {
    cursor.style.transform = 'scale(2.5)';
    ring.style.transform = 'scale(1.5)';
  });
  el.addEventListener('mouseleave', () => {
    cursor.style.transform = 'scale(1)';
    ring.style.transform = 'scale(1)';
  });
});

/* ---- MATRIX CANVAS ---- */
const canvas = document.getElementById('matrix-canvas');
const ctx = canvas.getContext('2d');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
window.addEventListener('resize', () => {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
});
const cols = Math.floor(canvas.width / 20);
const drops = Array(cols).fill(1);
function drawMatrix() {
  ctx.fillStyle = 'rgba(7,11,18,0.05)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ctx.fillStyle = '#00D9FF';
  ctx.font = '14px JetBrains Mono, monospace';
  const chars = '01アイウエオカキクケコABCDEF<>/[]{}';
  drops.forEach((y, i) => {
    const char = chars[Math.floor(Math.random() * chars.length)];
    ctx.fillText(char, i * 20, y * 20);
    if (y * 20 > canvas.height && Math.random() > 0.975) drops[i] = 0;
    drops[i]++;
  });
}
setInterval(drawMatrix, 60);

/* ---- TYPING EFFECT ---- */
const lines = [
  'Building intelligent systems',
  'Data Science & AI Engineer',
  'Full-Stack Developer',
  'DevOps Enthusiast',
  'RHCSA · PCAP™ · EX188 Certified',
];
let lineIdx = 0, charIdx = 0, deleting = false;
const typingEl = document.getElementById('typing-text');
function type() {
  const current = lines[lineIdx];
  if (!deleting) {
    typingEl.textContent = current.slice(0, ++charIdx);
    if (charIdx === current.length) { deleting = true; setTimeout(type, 1800); return; }
  } else {
    typingEl.textContent = current.slice(0, --charIdx);
    if (charIdx === 0) { deleting = false; lineIdx = (lineIdx + 1) % lines.length; }
  }
  setTimeout(type, deleting ? 40 : 70);
}
setTimeout(type, 1600);

/* ---- SCROLL ANIMATIONS ---- */
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
      const siblings = e.target.parentElement.querySelectorAll('.timeline-item, .cert-card, .project-card, .leadership-card');
      siblings.forEach((el, i) => {
        if (el === e.target) el.style.transitionDelay = i * 80 + 'ms';
      });
    }
  });
}, { threshold: 0.1 });
document.querySelectorAll('.timeline-item, .cert-card, .project-card, .leadership-card').forEach(el => observer.observe(el));

/* ---- NAV SHRINK ---- */
window.addEventListener('scroll', () => {
  document.querySelector('nav').style.padding = window.scrollY > 60 ? '12px 48px' : '18px 48px';
});

/* ---- STAT COUNTER ---- */
function animateCounters() {
  document.querySelectorAll('.stat-num').forEach(el => {
    const target = parseInt(el.textContent);
    if (isNaN(target)) return;
    const suffix = el.textContent.replace(target, '');
    let current = 0;
    const step = target / 40;
    const timer = setInterval(() => {
      current = Math.min(current + step, target);
      el.textContent = Math.floor(current) + suffix;
      if (current >= target) clearInterval(timer);
    }, 40);
  });
}
const statObserver = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { animateCounters(); statObserver.disconnect(); }});
}, { threshold: 0.5 });
const statsSection = document.querySelector('.stat-grid');
if (statsSection) statObserver.observe(statsSection);
</script>
</body>
</html>
