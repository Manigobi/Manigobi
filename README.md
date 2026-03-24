<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Gobinathan B — Java Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Sans:wght@300;400;500&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
:root {
  --cream:   #faf8f3;
  --cream2:  #f3f0e8;
  --cream3:  #e8e3d5;
  --ink:     #1a1714;
  --ink2:    #3d3830;
  --ink3:    #7a7469;
  --red:     #c0392b;
  --gold:    #b8860b;
  --green:   #2d6a4f;
  --blue:    #1a3a5c;
  --serif:   'Playfair Display', Georgia, serif;
  --sans:    'DM Sans', sans-serif;
  --mono:    'DM Mono', monospace;
}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--cream);
  color: var(--ink);
  font-family: var(--sans);
  font-weight: 300;
  overflow-x: hidden;
  cursor: none;
}

/* ── Custom cursor ── */
#cursor {
  position: fixed;
  width: 10px; height: 10px;
  background: var(--red);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%,-50%);
  transition: width .2s, height .2s, background .2s;
  mix-blend-mode: multiply;
}
#cursor.hover {
  width: 40px; height: 40px;
  background: var(--ink);
  opacity: 0.15;
}

/* ── Noise texture overlay ── */
body::after {
  content: '';
  position: fixed; inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
  opacity: 0.03;
  pointer-events: none;
  z-index: 100;
}

/* ── Marquee strip ── */
.marquee-strip {
  background: var(--ink);
  color: var(--cream);
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 2px;
  text-transform: uppercase;
  padding: 10px 0;
  overflow: hidden;
  white-space: nowrap;
  position: relative;
}
.marquee-inner {
  display: inline-block;
  animation: marquee 25s linear infinite;
}
.marquee-inner span { margin: 0 32px; color: var(--cream3); }
.marquee-inner .dot { color: var(--red); margin: 0 8px; }
@keyframes marquee { from { transform: translateX(0); } to { transform: translateX(-50%); } }

/* ── Main layout ── */
.layout {
  display: grid;
  grid-template-columns: 300px 1fr;
  min-height: 100vh;
}

/* ── Sidebar ── */
.sidebar {
  background: var(--ink);
  color: var(--cream);
  padding: 48px 36px;
  position: sticky;
  top: 0;
  height: 100vh;
  display: flex;
  flex-direction: column;
  gap: 0;
  overflow: hidden;
}

.sidebar-bg {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse 200px 200px at 20% 80%, rgba(192,57,43,0.15), transparent),
    radial-gradient(ellipse 150px 150px at 80% 20%, rgba(184,134,11,0.1), transparent);
  pointer-events: none;
}

.logo-mark {
  font-family: var(--serif);
  font-size: 64px;
  font-weight: 900;
  line-height: 1;
  letter-spacing: -3px;
  color: var(--cream);
  margin-bottom: 6px;
  animation: fadeIn 0.8s ease forwards;
  position: relative;
}

.logo-mark::after {
  content: '.';
  color: var(--red);
}

.sidebar-name {
  font-family: var(--sans);
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 4px;
  text-transform: uppercase;
  color: var(--ink3);
  margin-bottom: 40px;
  animation: fadeIn 0.8s ease 0.1s both;
}

.sidebar-divider {
  width: 40px; height: 1px;
  background: var(--red);
  margin-bottom: 32px;
  animation: expandWidth 0.8s ease 0.3s both;
}
@keyframes expandWidth { from { width: 0; } to { width: 40px; } }

.sidebar-bio {
  font-size: 13px;
  line-height: 1.8;
  color: #a09890;
  margin-bottom: 36px;
  animation: fadeIn 0.8s ease 0.4s both;
}

.sidebar-label {
  font-size: 9px;
  font-weight: 500;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--red);
  margin-bottom: 12px;
}

.tag-cloud {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 36px;
  animation: fadeIn 0.8s ease 0.5s both;
}

.tag {
  font-family: var(--mono);
  font-size: 10px;
  padding: 4px 10px;
  border: 1px solid rgba(255,255,255,0.12);
  border-radius: 2px;
  color: #c0b8b0;
  letter-spacing: 0.5px;
  transition: border-color 0.2s, color 0.2s;
  cursor: none;
}
.tag:hover { border-color: var(--red); color: var(--cream); }

.sidebar-nav {
  display: flex;
  flex-direction: column;
  gap: 4px;
  margin-bottom: auto;
  animation: fadeIn 0.8s ease 0.6s both;
}

.nav-item {
  display: flex;
  align-items: center;
  gap: 12px;
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 1px;
  color: #a09890;
  text-decoration: none;
  padding: 8px 0;
  border-bottom: 1px solid rgba(255,255,255,0.05);
  transition: color 0.2s;
  cursor: none;
}
.nav-item:hover { color: var(--cream); }
.nav-item .n { color: var(--red); width: 24px; flex-shrink: 0; }

.sidebar-social {
  display: flex;
  gap: 12px;
  margin-top: 36px;
  animation: fadeIn 0.8s ease 0.7s both;
}

.s-btn {
  width: 36px; height: 36px;
  border: 1px solid rgba(255,255,255,0.12);
  border-radius: 2px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  text-decoration: none;
  color: #a09890;
  transition: border-color 0.2s, color 0.2s, background 0.2s;
  cursor: none;
}
.s-btn:hover { border-color: var(--red); color: var(--cream); background: rgba(192,57,43,0.15); }

.avail-badge {
  display: flex;
  align-items: center;
  gap: 8px;
  font-family: var(--mono);
  font-size: 10px;
  color: #6ab187;
  letter-spacing: 1px;
  margin-top: 16px;
}
.avail-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: #6ab187;
  animation: breathe 2s ease-in-out infinite;
}
@keyframes breathe { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.4;transform:scale(0.7)} }

/* ── Main content ── */
.main {
  padding: 0;
  overflow-y: auto;
}

/* ── Hero section ── */
.hero {
  padding: 64px 64px 48px;
  border-bottom: 1px solid var(--cream3);
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: 'JAVA';
  position: absolute;
  right: -20px; top: 20px;
  font-family: var(--serif);
  font-size: 160px;
  font-weight: 900;
  color: var(--cream2);
  letter-spacing: -8px;
  line-height: 1;
  pointer-events: none;
  user-select: none;
}

.hero-label {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 4px;
  text-transform: uppercase;
  color: var(--red);
  margin-bottom: 20px;
  animation: fadeIn 0.6s ease 0.2s both;
}

.hero-title {
  font-family: var(--serif);
  font-size: clamp(42px, 5vw, 72px);
  font-weight: 900;
  line-height: 1.0;
  letter-spacing: -2px;
  color: var(--ink);
  margin-bottom: 8px;
  animation: slideRight 0.8s ease 0.3s both;
}

.hero-title em {
  font-style: italic;
  color: var(--red);
}

.hero-subtitle {
  font-family: var(--serif);
  font-size: 22px;
  font-style: italic;
  color: var(--ink3);
  font-weight: 400;
  margin-bottom: 28px;
  animation: slideRight 0.8s ease 0.4s both;
}

.hero-desc {
  max-width: 540px;
  font-size: 15px;
  line-height: 1.8;
  color: var(--ink2);
  animation: fadeIn 0.8s ease 0.5s both;
}

@keyframes slideRight { from { opacity:0; transform: translateX(-30px); } to { opacity:1; transform:translateX(0); } }
@keyframes fadeIn { from { opacity:0; } to { opacity:1; } }

.hero-stats {
  display: flex;
  gap: 48px;
  margin-top: 40px;
  padding-top: 32px;
  border-top: 1px solid var(--cream3);
  animation: fadeIn 0.8s ease 0.6s both;
}

.h-stat { }
.h-stat-num {
  font-family: var(--serif);
  font-size: 42px;
  font-weight: 700;
  color: var(--ink);
  line-height: 1;
}
.h-stat-lbl {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--ink3);
  margin-top: 4px;
}

/* ── Content sections ── */
.content-section {
  padding: 56px 64px;
  border-bottom: 1px solid var(--cream3);
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.content-section.visible { opacity:1; transform:translateY(0); }

.section-header {
  display: flex;
  align-items: baseline;
  gap: 16px;
  margin-bottom: 40px;
}

.section-num {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--red);
  letter-spacing: 1px;
}

.section-heading {
  font-family: var(--serif);
  font-size: 30px;
  font-weight: 700;
  color: var(--ink);
  letter-spacing: -0.5px;
}

.section-line {
  flex: 1;
  height: 1px;
  background: var(--cream3);
  margin-left: 16px;
}

/* ── About / Code ── */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px;
  align-items: start;
}

.about-text {
  font-size: 15px;
  line-height: 1.9;
  color: var(--ink2);
}

.about-text p + p { margin-top: 16px; }

.code-panel {
  background: var(--ink);
  border-radius: 4px;
  padding: 28px;
  font-family: var(--mono);
  font-size: 12px;
  line-height: 1.9;
  color: #a09890;
  position: relative;
  overflow: hidden;
}

.code-panel::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--red), var(--gold), var(--green));
}

.cp-bar {
  display: flex;
  gap: 6px;
  margin-bottom: 20px;
}
.cp-dot { width: 8px; height: 8px; border-radius: 50%; }
.cp-dot:nth-child(1) { background: #ff5f56; }
.cp-dot:nth-child(2) { background: #ffbd2e; }
.cp-dot:nth-child(3) { background: #27c93f; }

.ck { color: #c792ea; }
.cs { color: #c3e88d; }
.cc { color: #546e7a; font-style: italic; }
.cf { color: #82aaff; }
.cn { color: #f78c6c; }

/* ── Stack ── */
.stack-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: var(--cream3);
  border: 1px solid var(--cream3);
  border-radius: 4px;
  overflow: hidden;
}

.stack-cell {
  background: var(--cream);
  padding: 24px 20px;
  display: flex;
  align-items: center;
  gap: 14px;
  transition: background 0.2s;
  cursor: none;
}
.stack-cell:hover { background: var(--cream2); }

.stack-icon {
  width: 40px; height: 40px;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  flex-shrink: 0;
}

.stack-name {
  font-family: var(--mono);
  font-size: 12px;
  font-weight: 500;
  color: var(--ink);
  letter-spacing: 0.5px;
  margin-bottom: 2px;
}
.stack-cat {
  font-size: 10px;
  color: var(--ink3);
  letter-spacing: 0.5px;
}

/* ── Project ── */
.project-editorial {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 40px;
  align-items: start;
}

.proj-number {
  font-family: var(--serif);
  font-size: 120px;
  font-weight: 900;
  color: var(--cream3);
  line-height: 1;
  letter-spacing: -6px;
  text-align: center;
  margin-top: -10px;
}

.proj-content {}

.proj-tag {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--red);
  margin-bottom: 12px;
}

.proj-title {
  font-family: var(--serif);
  font-size: 32px;
  font-weight: 700;
  color: var(--ink);
  letter-spacing: -1px;
  margin-bottom: 14px;
  line-height: 1.1;
}

.proj-desc {
  font-size: 14px;
  line-height: 1.8;
  color: var(--ink2);
  margin-bottom: 24px;
}

.proj-features {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  margin-bottom: 28px;
}

.feat {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  color: var(--ink2);
}

.feat::before {
  content: '';
  width: 4px; height: 4px;
  border-radius: 50%;
  background: var(--red);
  flex-shrink: 0;
}

.proj-pills {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 28px;
}

.pill {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 1px;
  padding: 5px 12px;
  border: 1px solid var(--cream3);
  border-radius: 2px;
  color: var(--ink2);
  background: var(--cream2);
}

.proj-link {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--ink);
  text-decoration: none;
  border-bottom: 2px solid var(--red);
  padding-bottom: 3px;
  transition: gap 0.2s, color 0.2s;
  cursor: none;
}
.proj-link:hover { gap: 16px; color: var(--red); }

/* ── Skills / Bars ── */
.skill-editorial {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.skill-row-e {
  display: grid;
  grid-template-columns: 200px 1fr 50px;
  align-items: center;
  gap: 24px;
  padding: 18px 0;
  border-bottom: 1px solid var(--cream3);
}

.skill-row-e:last-child { border-bottom: none; }

.sn {
  font-family: var(--sans);
  font-size: 13px;
  font-weight: 400;
  color: var(--ink2);
}

.bar-bg {
  height: 2px;
  background: var(--cream3);
  border-radius: 99px;
  overflow: visible;
  position: relative;
}

.bar-fg {
  height: 2px;
  background: var(--ink);
  border-radius: 99px;
  width: 0;
  transition: width 1.4s cubic-bezier(0.16,1,0.3,1);
  position: relative;
}

.bar-fg::after {
  content: '';
  position: absolute;
  right: -3px; top: -3px;
  width: 8px; height: 8px;
  border-radius: 50%;
  background: var(--red);
  opacity: 0;
  transition: opacity 0.3s 1.2s;
}

.bar-fg.animated::after { opacity: 1; }

.sp {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--ink3);
  text-align: right;
}

/* ── Roadmap ── */
.roadmap-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.road-card {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 16px 20px;
  border: 1px solid var(--cream3);
  border-radius: 4px;
  background: var(--cream);
  transition: border-color 0.2s, box-shadow 0.2s;
  cursor: none;
}

.road-card:hover {
  border-color: var(--ink3);
  box-shadow: 4px 4px 0 var(--cream3);
}

.road-status {
  width: 8px; height: 8px;
  border-radius: 50%;
  flex-shrink: 0;
}

.road-status.done   { background: var(--green); }
.road-status.active { background: var(--gold); animation: breathe 1.5s ease-in-out infinite; }
.road-status.todo   { background: var(--cream3); border: 1px solid var(--cream3 ); }

.road-label {
  font-size: 13px;
  color: var(--ink2);
}

/* ── Quote ── */
.quote-editorial {
  padding: 56px 64px;
  background: var(--ink);
  color: var(--cream);
  text-align: center;
  position: relative;
  overflow: hidden;
}

.quote-editorial::before {
  content: '\201C';
  position: absolute;
  font-family: var(--serif);
  font-size: 400px;
  font-weight: 900;
  color: rgba(255,255,255,0.03);
  top: -100px; left: 50%;
  transform: translateX(-50%);
  line-height: 1;
  pointer-events: none;
}

.q-text {
  font-family: var(--serif);
  font-size: clamp(22px, 3vw, 36px);
  font-style: italic;
  font-weight: 400;
  line-height: 1.5;
  max-width: 600px;
  margin: 0 auto 20px;
  color: var(--cream);
}

.q-attr {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: #a09890;
}

/* ── Footer ── */
.footer {
  padding: 40px 64px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-top: 1px solid var(--cream3);
}

.footer-left {
  font-family: var(--serif);
  font-size: 18px;
  font-style: italic;
  color: var(--ink3);
}

.footer-right {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 2px;
  color: var(--ink3);
  text-transform: uppercase;
}

/* ── Responsive ── */
@media (max-width: 900px) {
  .layout { grid-template-columns: 1fr; }
  .sidebar { position: relative; height: auto; }
  .main { }
  .about-grid, .project-editorial { grid-template-columns: 1fr; }
  .hero::before { display: none; }
  .hero, .content-section { padding: 40px 32px; }
  .stack-grid { grid-template-columns: 1fr 1fr; }
  .roadmap-grid { grid-template-columns: 1fr; }
  .footer { flex-direction: column; gap: 12px; padding: 32px; }
  .hero-stats { gap: 28px; }
}
</style>
</head>
<body>

<div id="cursor"></div>

<!-- Marquee -->
<div class="marquee-strip">
  <div class="marquee-inner">
    <span>Java Developer</span><span class="dot">◆</span>
    <span>Spring Boot</span><span class="dot">◆</span>
    <span>Backend Engineer</span><span class="dot">◆</span>
    <span>RESTful APIs</span><span class="dot">◆</span>
    <span>MySQL</span><span class="dot">◆</span>
    <span>SQL Server</span><span class="dot">◆</span>
    <span>PostgreSQL</span><span class="dot">◆</span>
    <span>E-Commerce</span><span class="dot">◆</span>
    <span>Clean Code</span><span class="dot">◆</span>
    <span>Open to Work</span><span class="dot">◆</span>
    <!-- repeat for seamless loop -->
    <span>Java Developer</span><span class="dot">◆</span>
    <span>Spring Boot</span><span class="dot">◆</span>
    <span>Backend Engineer</span><span class="dot">◆</span>
    <span>RESTful APIs</span><span class="dot">◆</span>
    <span>MySQL</span><span class="dot">◆</span>
    <span>SQL Server</span><span class="dot">◆</span>
    <span>PostgreSQL</span><span class="dot">◆</span>
    <span>E-Commerce</span><span class="dot">◆</span>
    <span>Clean Code</span><span class="dot">◆</span>
    <span>Open to Work</span><span class="dot">◆</span>
  </div>
</div>

<div class="layout">

  <!-- Sidebar -->
  <aside class="sidebar">
    <div class="sidebar-bg"></div>
    <div class="logo-mark">GB</div>
    <div class="sidebar-name">Gobinathan B</div>
    <div class="sidebar-divider"></div>
    <p class="sidebar-bio">Java Developer building scalable backend systems. Passionate about clean architecture and efficient code.</p>

    <div class="sidebar-label">Core Stack</div>
    <div class="tag-cloud">
      <span class="tag">Java</span>
      <span class="tag">Spring</span>
      <span class="tag">Hibernate</span>
      <span class="tag">MySQL</span>
      <span class="tag">SQL Server</span>
      <span class="tag">Maven</span>
      <span class="tag">Git</span>
      <span class="tag">REST</span>
    </div>

    <div class="sidebar-label">Navigate</div>
    <nav class="sidebar-nav">
      <a href="#about" class="nav-item"><span class="n">01</span> About</a>
      <a href="#stack" class="nav-item"><span class="n">02</span> Tech Stack</a>
      <a href="#project" class="nav-item"><span class="n">03</span> Projects</a>
      <a href="#skills" class="nav-item"><span class="n">04</span> Proficiency</a>
      <a href="#roadmap" class="nav-item"><span class="n">05</span> Roadmap</a>
    </nav>

    <div class="sidebar-social">
      <a href="https://github.com/Manigobi" class="s-btn" target="_blank" title="GitHub">🐙</a>
      <a href="https://linkedin.com/in/gobinathan-b" class="s-btn" target="_blank" title="LinkedIn">💼</a>
      <a href="mailto:gobinathan@gmail.com" class="s-btn" title="Email">📧</a>
      <a href="https://leetcode.com/gobinathan" class="s-btn" target="_blank" title="LeetCode">⚡</a>
    </div>

    <div class="avail-badge">
      <div class="avail-dot"></div>
      Available for opportunities
    </div>
  </aside>

  <!-- Main -->
  <main class="main">

    <!-- Hero -->
    <section class="hero">
      <div class="hero-label">Portfolio · 2025 · India</div>
      <h1 class="hero-title">Backend<br><em>Engineer</em></h1>
      <p class="hero-subtitle">crafting robust Java systems</p>
      <p class="hero-desc">I build reliable, scalable backend applications using Java and Spring. Focused on clean architecture, efficient databases, and RESTful API design that stands the test of production.</p>
      <div class="hero-stats">
        <div class="h-stat">
          <div class="h-stat-num" id="ctr1">0</div>
          <div class="h-stat-lbl">Repositories</div>
        </div>
        <div class="h-stat">
          <div class="h-stat-num" id="ctr2">0</div>
          <div class="h-stat-lbl">Contributions</div>
        </div>
        <div class="h-stat">
          <div class="h-stat-num" id="ctr3">0</div>
          <div class="h-stat-lbl">Projects Shipped</div>
        </div>
      </div>
    </section>

    <!-- About -->
    <section class="content-section" id="about">
      <div class="section-header">
        <span class="section-num">01</span>
        <h2 class="section-heading">About</h2>
        <div class="section-line"></div>
      </div>
      <div class="about-grid">
        <div class="about-text">
          <p>I'm <strong>Gobinathan B</strong>, a Java Developer from India with a deep focus on backend engineering. I thrive in building systems that are maintainable, testable, and production-ready.</p>
          <p>My approach blends strong OOP fundamentals with modern Spring ecosystem tools — whether it's designing RESTful APIs, structuring data models, or wiring up persistence layers with Hibernate.</p>
          <p>Beyond the code, I believe in clear documentation, Git discipline, and always thinking about the next engineer who will read what I write.</p>
        </div>
        <div class="code-panel">
          <div class="cp-bar">
            <div class="cp-dot"></div><div class="cp-dot"></div><div class="cp-dot"></div>
          </div>
<span class="ck">public class</span> <span style="color:#ffcb6b">GobinathanB</span> {<br><br>
&nbsp;&nbsp;<span class="cc">// Identity</span><br>
&nbsp;&nbsp;<span class="ck">String</span> role = <span class="cs">"Java Developer"</span>;<br>
&nbsp;&nbsp;<span class="ck">String</span> location = <span class="cs">"India 🇮🇳"</span>;<br><br>
&nbsp;&nbsp;<span class="cc">// Philosophy</span><br>
&nbsp;&nbsp;<span class="ck">String</span>[] values = {<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs">"Clean Architecture"</span>,<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs">"Test-Driven Thinking"</span>,<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs">"Continuous Learning"</span><br>
&nbsp;&nbsp;};<br><br>
&nbsp;&nbsp;<span class="ck">boolean</span> openToWork = <span class="cn">true</span>;<br>
}
        </div>
      </div>
    </section>

    <!-- Stack -->
    <section class="content-section" id="stack">
      <div class="section-header">
        <span class="section-num">02</span>
        <h2 class="section-heading">Tech Stack</h2>
        <div class="section-line"></div>
      </div>
      <div class="stack-grid">
        <div class="stack-cell">
          <div class="stack-icon" style="background:#fff3e0">☕</div>
          <div><div class="stack-name">Java</div><div class="stack-cat">Language</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#e8f5e9">🌱</div>
          <div><div class="stack-name">Spring Boot</div><div class="stack-cat">Framework</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#e3f2fd">🔧</div>
          <div><div class="stack-name">Spring MVC</div><div class="stack-cat">Framework</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#fce4ec">🗃️</div>
          <div><div class="stack-name">Hibernate</div><div class="stack-cat">ORM</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#e0f7fa">🐬</div>
          <div><div class="stack-name">MySQL</div><div class="stack-cat">Database</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#ede7f6">🐘</div>
          <div><div class="stack-name">PostgreSQL</div><div class="stack-cat">Database</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#e8eaf6">🗄️</div>
          <div><div class="stack-name">SQL Server</div><div class="stack-cat">Database</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#fff8e1">📦</div>
          <div><div class="stack-name">Maven</div><div class="stack-cat">Build Tool</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#fbe9e7">🔀</div>
          <div><div class="stack-name">Git & GitHub</div><div class="stack-cat">Version Control</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#f3e5f5">📮</div>
          <div><div class="stack-name">Postman</div><div class="stack-cat">API Testing</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#e8f5e9">🌐</div>
          <div><div class="stack-name">HTML / CSS / JS</div><div class="stack-cat">Frontend</div></div>
        </div>
        <div class="stack-cell">
          <div class="stack-icon" style="background:#f1f8e9">🐧</div>
          <div><div class="stack-name">Linux</div><div class="stack-cat">OS</div></div>
        </div>
      </div>
    </section>

    <!-- Project -->
    <section class="content-section" id="project">
      <div class="section-header">
        <span class="section-num">03</span>
        <h2 class="section-heading">Featured Project</h2>
        <div class="section-line"></div>
      </div>
      <div class="project-editorial">
        <div class="proj-number">01</div>
        <div class="proj-content">
          <div class="proj-tag">Public · Java · Spring · MySQL</div>
          <h3 class="proj-title">E-Commerce<br>Website</h3>
          <p class="proj-desc">A full-featured online shopping platform built from scratch. Handles product listings, cart management, user authentication, and order processing with a clean admin panel.</p>
          <div class="proj-features">
            <div class="feat">Secure user authentication</div>
            <div class="feat">Product catalog & filtering</div>
            <div class="feat">Shopping cart & orders</div>
            <div class="feat">Checkout flow</div>
            <div class="feat">Responsive UI</div>
            <div class="feat">Admin dashboard</div>
          </div>
          <div class="proj-pills">
            <span class="pill">Java</span>
            <span class="pill">Spring MVC</span>
            <span class="pill">Hibernate</span>
            <span class="pill">MySQL</span>
            <span class="pill">CSS</span>
            <span class="pill">Maven</span>
          </div>
          <a href="https://github.com/Manigobi/e-commerce-website" class="proj-link" target="_blank">View Repository →</a>
        </div>
      </div>
    </section>

    <!-- Skills -->
    <section class="content-section" id="skills">
      <div class="section-header">
        <span class="section-num">04</span>
        <h2 class="section-heading">Proficiency</h2>
        <div class="section-line"></div>
      </div>
      <div class="skill-editorial" id="skillSection">
        <div class="skill-row-e">
          <span class="sn">Java (Core + Advanced)</span>
          <div class="bar-bg"><div class="bar-fg" data-w="80"></div></div>
          <span class="sp">80%</span>
        </div>
        <div class="skill-row-e">
          <span class="sn">Spring Boot / MVC</span>
          <div class="bar-bg"><div class="bar-fg" data-w="70"></div></div>
          <span class="sp">70%</span>
        </div>
        <div class="skill-row-e">
          <span class="sn">RESTful API Design</span>
          <div class="bar-bg"><div class="bar-fg" data-w="70"></div></div>
          <span class="sp">70%</span>
        </div>
        <div class="skill-row-e">
          <span class="sn">SQL Databases</span>
          <div class="bar-bg"><div class="bar-fg" data-w="75"></div></div>
          <span class="sp">75%</span>
        </div>
        <div class="skill-row-e">
          <span class="sn">Frontend (HTML/CSS/JS)</span>
          <div class="bar-bg"><div class="bar-fg" data-w="60"></div></div>
          <span class="sp">60%</span>
        </div>
        <div class="skill-row-e">
          <span class="sn">Git & Version Control</span>
          <div class="bar-bg"><div class="bar-fg" data-w="80"></div></div>
          <span class="sp">80%</span>
        </div>
      </div>
    </section>

    <!-- Roadmap -->
    <section class="content-section" id="roadmap">
      <div class="section-header">
        <span class="section-num">05</span>
        <h2 class="section-heading">Roadmap 2025</h2>
        <div class="section-line"></div>
      </div>
      <div class="roadmap-grid">
        <div class="road-card"><div class="road-status done"></div><span class="road-label">Core Java & OOP Principles</span></div>
        <div class="road-card"><div class="road-status done"></div><span class="road-label">Spring Framework (MVC, Boot)</span></div>
        <div class="road-card"><div class="road-status done"></div><span class="road-label">RESTful API Development</span></div>
        <div class="road-card"><div class="road-status done"></div><span class="road-label">SQL Databases (MySQL, PostgreSQL, SQL Server)</span></div>
        <div class="road-card"><div class="road-status active"></div><span class="road-label">Microservices Architecture</span></div>
        <div class="road-card"><div class="road-status active"></div><span class="road-label">Docker & Containerisation</span></div>
        <div class="road-card"><div class="road-status todo"></div><span class="road-label">Cloud Deployment (AWS / GCP)</span></div>
        <div class="road-card"><div class="road-status todo"></div><span class="road-label">System Design & Scalability</span></div>
      </div>
      <div style="display:flex;gap:24px;margin-top:20px;font-size:12px;color:var(--ink3);">
        <span style="display:flex;align-items:center;gap:8px;"><span style="width:8px;height:8px;border-radius:50%;background:var(--green);display:inline-block"></span>Completed</span>
        <span style="display:flex;align-items:center;gap:8px;"><span style="width:8px;height:8px;border-radius:50%;background:var(--gold);display:inline-block"></span>In Progress</span>
        <span style="display:flex;align-items:center;gap:8px;"><span style="width:8px;height:8px;border-radius:50%;background:var(--cream3);display:inline-block;border:1px solid var(--cream3)"></span>Planned</span>
      </div>
    </section>

    <!-- Quote -->
    <div class="quote-editorial">
      <p class="q-text">"First, solve the problem. Then, write the code."</p>
      <div class="q-attr">— John Johnson</div>
    </div>

    <!-- Footer -->
    <footer class="footer">
      <div class="footer-left">Gobinathan B — India, 2025</div>
      <div class="footer-right">☕ Built with Java & Passion · Open to Work</div>
    </footer>

  </main>
</div>

<script>
/* Custom cursor */
const cur = document.getElementById('cursor');
document.addEventListener('mousemove', e => {
  cur.style.left = e.clientX + 'px';
  cur.style.top  = e.clientY + 'px';
});
document.querySelectorAll('a,button,.stack-cell,.road-card,.tag').forEach(el => {
  el.addEventListener('mouseenter', () => cur.classList.add('hover'));
  el.addEventListener('mouseleave', () => cur.classList.remove('hover'));
});

/* Hero counter */
function count(el, target, dur=1200) {
  let v = 0;
  const step = target / (dur / 16);
  const t = setInterval(() => {
    v += step;
    if (v >= target) { el.textContent = target; clearInterval(t); return; }
    el.textContent = Math.floor(v);
  }, 16);
}
setTimeout(() => {
  count(document.getElementById('ctr1'), 15);
  count(document.getElementById('ctr2'), 25);
  count(document.getElementById('ctr3'), 3);
}, 600);

/* Scroll reveal */
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); obs.unobserve(e.target); } });
}, { threshold: 0.1 });
document.querySelectorAll('.content-section').forEach(s => obs.observe(s));

/* Skill bars */
const barObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.bar-fg').forEach(b => {
        b.style.width = b.dataset.w + '%';
        setTimeout(() => b.classList.add('animated'), 1300);
      });
      barObs.unobserve(e.target);
    }
  });
}, { threshold: 0.4 });
const ss = document.getElementById('skillSection');
if (ss) barObs.observe(ss);
</script>
</body>
</html>
