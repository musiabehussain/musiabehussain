<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Musiabe Hussain — Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg:        #0D1117;
    --surface:   #161B22;
    --card:      #1C2333;
    --border:    #21262D;
    --cyan:      #14B8C8;
    --cyan-dim:  rgba(20,184,200,0.12);
    --cyan-glow: rgba(20,184,200,0.25);
    --green:     #3FB950;
    --green-dim: rgba(63,185,80,0.12);
    --amber:     #F0A30A;
    --text-1:    #E6EDF3;
    --text-2:    #8B949E;
    --text-3:    #484F58;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--bg);
    color: var(--text-1);
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    line-height: 1.65;
    min-height: 100vh;
  }

  /* ── Page scaffold ── */
  .page {
    max-width: 1100px;
    margin: 0 auto;
    padding: 32px 20px 80px;
    display: grid;
    grid-template-columns: 1fr 320px;
    gap: 24px;
    align-items: start;
  }
  .main  { display: flex; flex-direction: column; gap: 20px; }
  .aside { display: flex; flex-direction: column; gap: 20px; }

  /* ── Top banner ── */
  .banner {
    grid-column: 1 / -1;
    position: relative;
    border-radius: 16px;
    overflow: hidden;
    background: linear-gradient(135deg, #0b1622 0%, #112233 50%, #0b1d2a 100%);
    border: 1px solid var(--border);
    padding: 40px 36px 36px;
    display: flex;
    align-items: flex-end;
    gap: 28px;
  }
  .banner::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 120% at 80% 50%, rgba(20,184,200,0.07) 0%, transparent 70%),
      radial-gradient(ellipse 30% 60% at 10% 80%, rgba(20,184,200,0.05) 0%, transparent 60%);
    pointer-events: none;
  }
  .banner-grid-lines {
    position: absolute; inset: 0; pointer-events: none;
    background-image:
      linear-gradient(rgba(20,184,200,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(20,184,200,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
  }
  .avatar-wrap {
    position: relative; flex-shrink: 0;
  }
  .avatar {
    width: 110px; height: 110px;
    border-radius: 50%;
    background: linear-gradient(135deg, #14B8C8 0%, #0e7da8 100%);
    display: flex; align-items: center; justify-content: center;
    font-family: 'Syne', sans-serif;
    font-weight: 800; font-size: 38px;
    color: #0D1117;
    border: 3px solid rgba(20,184,200,0.5);
    box-shadow: 0 0 40px rgba(20,184,200,0.3);
    position: relative; z-index: 1;
  }
  .online-dot {
    position: absolute; bottom: 6px; right: 6px;
    width: 18px; height: 18px; border-radius: 50%;
    background: var(--green);
    border: 2px solid var(--surface);
    box-shadow: 0 0 8px rgba(63,185,80,0.6);
  }
  .banner-info { flex: 1; position: relative; z-index: 1; }
  .banner-name {
    font-family: 'Syne', sans-serif;
    font-weight: 800; font-size: 30px;
    letter-spacing: -0.5px;
    color: var(--text-1);
    line-height: 1.1;
    margin-bottom: 4px;
  }
  .banner-title {
    font-size: 14px; font-weight: 500;
    color: var(--cyan); letter-spacing: 0.04em;
    text-transform: uppercase; margin-bottom: 12px;
  }
  .banner-meta {
    display: flex; flex-wrap: wrap; gap: 16px;
    font-size: 13px; color: var(--text-2);
  }
  .banner-meta span { display: flex; align-items: center; gap: 5px; }
  .banner-meta .ico { font-size: 14px; }
  .rating-stars { color: var(--amber); letter-spacing: -1px; }
  .banner-actions {
    position: relative; z-index: 1;
    display: flex; flex-direction: column; gap: 10px; align-items: flex-end;
  }
  .rate-box {
    background: var(--cyan-dim);
    border: 1px solid rgba(20,184,200,0.3);
    border-radius: 10px;
    padding: 10px 18px;
    text-align: center;
  }
  .rate-box .rate-num {
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: 24px; color: var(--cyan);
  }
  .rate-box .rate-label { font-size: 11px; color: var(--text-2); }
  .avail-badge {
    display: flex; align-items: center; gap-6px;
    font-size: 12px; font-weight: 600;
    color: var(--green);
    background: var(--green-dim);
    border: 1px solid rgba(63,185,80,0.25);
    border-radius: 20px; padding: 6px 14px;
    gap: 6px;
  }
  .avail-dot { width: 7px; height: 7px; border-radius: 50%; background: var(--green); }

  /* ── Upwork-style nav bar ── */
  .upwork-nav {
    grid-column: 1 / -1;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    display: flex; align-items: center;
    padding: 0 8px;
    overflow-x: auto;
  }
  .upwork-nav a {
    color: var(--text-2); text-decoration: none;
    padding: 14px 18px; font-size: 14px; font-weight: 500;
    border-bottom: 2px solid transparent;
    white-space: nowrap; transition: color 0.2s, border-color 0.2s;
  }
  .upwork-nav a:hover, .upwork-nav a.active {
    color: var(--cyan); border-bottom-color: var(--cyan);
  }

  /* ── Cards ── */
  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    transition: border-color 0.2s;
  }
  .card:hover { border-color: rgba(20,184,200,0.25); }
  .card-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: 16px;
    color: var(--text-1); margin-bottom: 16px;
    display: flex; align-items: center; gap: 8px;
  }
  .card-title::before {
    content: ''; display: block;
    width: 3px; height: 18px; border-radius: 2px;
    background: var(--cyan);
  }

  /* ── About ── */
  .about-text {
    color: var(--text-2); font-size: 14.5px;
    line-height: 1.75;
  }
  .about-text strong { color: var(--cyan); font-weight: 600; }

  /* ── Skills ── */
  .skill-grid {
    display: flex; flex-wrap: wrap; gap: 8px;
  }
  .skill-tag {
    background: rgba(20,184,200,0.08);
    border: 1px solid rgba(20,184,200,0.2);
    color: var(--cyan);
    border-radius: 20px;
    padding: 5px 14px;
    font-size: 13px; font-weight: 500;
    transition: background 0.2s, border-color 0.2s;
    cursor: default;
  }
  .skill-tag:hover {
    background: rgba(20,184,200,0.18);
    border-color: rgba(20,184,200,0.45);
  }
  .skill-tag.secondary {
    background: rgba(139,148,158,0.08);
    border-color: rgba(139,148,158,0.2);
    color: var(--text-2);
  }

  /* ── Proficiency bars ── */
  .prof-list { display: flex; flex-direction: column; gap: 14px; }
  .prof-item {}
  .prof-header {
    display: flex; justify-content: space-between;
    font-size: 13.5px; margin-bottom: 7px;
    color: var(--text-1);
  }
  .prof-pct { color: var(--cyan); font-weight: 600; }
  .prof-bar {
    height: 5px; background: var(--border); border-radius: 99px; overflow: hidden;
  }
  .prof-fill {
    height: 100%; border-radius: 99px;
    background: linear-gradient(90deg, #14B8C8, #0e9bb0);
    transform-origin: left;
    animation: growBar 1s ease forwards;
    transform: scaleX(0);
  }
  @keyframes growBar { to { transform: scaleX(1); } }

  /* ── Stat cards (sidebar) ── */
  .stat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  .stat-box {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px 12px;
    text-align: center;
  }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: 22px; color: var(--cyan);
    line-height: 1;
  }
  .stat-label { font-size: 11px; color: var(--text-2); margin-top: 4px; }

  /* ── Portfolio items ── */
  .portfolio-grid { display: flex; flex-direction: column; gap: 14px; }
  .portfolio-item {
    display: flex; gap: 14px;
    padding: 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    transition: border-color 0.2s, transform 0.2s;
    cursor: pointer;
  }
  .portfolio-item:hover {
    border-color: rgba(20,184,200,0.3);
    transform: translateX(4px);
  }
  .port-icon {
    width: 44px; height: 44px; border-radius: 10px; flex-shrink: 0;
    background: var(--cyan-dim);
    border: 1px solid rgba(20,184,200,0.2);
    display: flex; align-items: center; justify-content: center;
    font-size: 20px;
  }
  .port-info { flex: 1; min-width: 0; }
  .port-title {
    font-weight: 600; font-size: 14px; color: var(--text-1);
    white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
  }
  .port-desc { font-size: 12.5px; color: var(--text-2); margin-top: 2px; }
  .port-tags { display: flex; gap: 6px; margin-top: 6px; flex-wrap: wrap; }
  .port-tag {
    font-size: 11px; padding: 2px 8px; border-radius: 4px;
    background: rgba(20,184,200,0.1); color: var(--cyan);
  }

  /* ── Contact CTA (sidebar) ── */
  .btn-primary {
    display: block; width: 100%; text-align: center;
    background: linear-gradient(135deg, #14B8C8 0%, #0e9bb0 100%);
    color: #0D1117; font-weight: 700; font-size: 14.5px;
    padding: 13px; border-radius: 10px;
    text-decoration: none; border: none; cursor: pointer;
    transition: opacity 0.2s, transform 0.15s;
    letter-spacing: 0.02em;
  }
  .btn-primary:hover { opacity: 0.88; transform: translateY(-1px); }
  .btn-secondary {
    display: block; width: 100%; text-align: center;
    background: transparent;
    color: var(--cyan); font-weight: 600; font-size: 14px;
    padding: 11px; border-radius: 10px;
    border: 1px solid rgba(20,184,200,0.35);
    text-decoration: none; cursor: pointer;
    transition: background 0.2s;
    letter-spacing: 0.02em;
  }
  .btn-secondary:hover { background: var(--cyan-dim); }

  /* ── Social links ── */
  .social-links { display: flex; flex-direction: column; gap: 8px; }
  .social-link {
    display: flex; align-items: center; gap: 10px;
    padding: 10px 12px;
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 8px; text-decoration: none;
    color: var(--text-2); font-size: 13.5px;
    transition: color 0.2s, border-color 0.2s;
  }
  .social-link:hover { color: var(--cyan); border-color: rgba(20,184,200,0.3); }
  .social-icon { font-size: 16px; width: 20px; text-align: center; }

  /* ── Philosophy ── */
  .philosophy-box {
    background: var(--cyan-dim);
    border: 1px solid rgba(20,184,200,0.2);
    border-radius: 10px;
    padding: 16px 18px;
    font-style: italic;
    font-size: 14px;
    color: var(--text-1);
    line-height: 1.7;
    position: relative;
  }
  .philosophy-box::before {
    content: '"';
    position: absolute; top: -6px; left: 14px;
    font-size: 52px; color: var(--cyan); opacity: 0.3;
    font-family: 'Syne', sans-serif; line-height: 1;
  }
  .philosophy-attr {
    margin-top: 10px;
    font-style: normal; font-size: 12px; color: var(--cyan);
    font-weight: 600; letter-spacing: 0.05em;
  }

  /* ── Expertise highlights ── */
  .expertise-list { display: flex; flex-direction: column; gap: 10px; }
  .expertise-item {
    display: flex; align-items: flex-start; gap: 12px;
    padding: 12px 14px;
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 8px;
  }
  .exp-bullet {
    width: 32px; height: 32px; flex-shrink: 0;
    border-radius: 8px; background: var(--cyan-dim);
    border: 1px solid rgba(20,184,200,0.2);
    display: flex; align-items: center; justify-content: center;
    font-size: 15px;
  }
  .exp-text { font-size: 13.5px; color: var(--text-2); line-height: 1.5; }
  .exp-text strong { color: var(--text-1); font-weight: 600; }

  /* ── Animations ── */
  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .card, .banner, .upwork-nav {
    animation: fadeSlideUp 0.5s ease both;
  }
  .card:nth-child(1) { animation-delay: 0.05s; }
  .card:nth-child(2) { animation-delay: 0.1s; }
  .card:nth-child(3) { animation-delay: 0.15s; }
  .card:nth-child(4) { animation-delay: 0.2s; }

  /* ── Responsive ── */
  @media (max-width: 720px) {
    .page { grid-template-columns: 1fr; }
    .banner { flex-direction: column; align-items: flex-start; gap: 16px; }
    .banner-actions { flex-direction: row; align-items: center; }
    .stat-grid { grid-template-columns: repeat(4, 1fr); }
  }
</style>
</head>
<body>

<div class="page">

  <!-- ══ BANNER ══ -->
  <div class="banner">
    <div class="banner-grid-lines"></div>
    <div class="avatar-wrap">
      <div class="avatar">MH</div>
      <div class="online-dot"></div>
    </div>
    <div class="banner-info">
      <div class="banner-name">Musiabe Hussain</div>
      <div class="banner-title">Senior Full Stack Developer &amp; Founder</div>
      <div class="banner-meta">
        <span><span class="ico">📍</span> Gilgit-Baltistan, Pakistan</span>
        <span><span class="rating-stars">★★★★★</span> 5.0 (47 reviews)</span>
        <span><span class="ico">🕐</span> Response &lt; 1 hr</span>
        <span><span class="ico">🌐</span> gbfixers.com</span>
      </div>
    </div>
    <div class="banner-actions">
      <div class="rate-box">
        <div class="rate-num">$18</div>
        <div class="rate-label">/ hr</div>
      </div>
      <div class="avail-badge">
        <div class="avail-dot"></div>
        Available Now
      </div>
    </div>
  </div>

  <!-- ══ NAV ══ -->
  <nav class="upwork-nav">
    <a href="#about" class="active">Overview</a>
    <a href="#skills">Skills</a>
    <a href="#portfolio">Portfolio</a>
    <a href="#expertise">Expertise</a>
    <a href="#philosophy">Philosophy</a>
  </nav>

  <!-- ══ MAIN COLUMN ══ -->
  <div class="main">

    <div class="card" id="about">
      <div class="card-title">About Me</div>
      <p class="about-text">
        I'm a <strong>Senior Full Stack Developer</strong> with <strong>5+ years of production experience</strong>,
        specializing in React, TypeScript, and Node.js. I'm the founder of
        <strong>GBfixers.com</strong> — Gilgit-Baltistan's premier tech solutions platform,
        built to bridge the digital divide in the GB region.
        <br/><br/>
        I don't just write code — I architect solutions. My approach is rooted in
        <strong>Clean Architecture</strong>, <strong>SOLID principles</strong>, and a relentless
        focus on performance, accessibility, and user experience. Whether you need a scalable
        React app, a robust REST API, or a complete product from zero to production, I deliver
        with precision and speed.
        <br/><br/>
        Self-starter. Fast learner. Business-first mindset. No hand-holding needed.
      </p>
    </div>

    <!-- Skills -->
    <div class="card" id="skills">
      <div class="card-title">Skills &amp; Technologies</div>

      <p style="font-size:12px; color:var(--text-3); text-transform:uppercase; letter-spacing:.08em; margin-bottom:10px; font-weight:600;">Frontend</p>
      <div class="skill-grid" style="margin-bottom:18px;">
        <span class="skill-tag">React</span>
        <span class="skill-tag">TypeScript</span>
        <span class="skill-tag">Next.js</span>
        <span class="skill-tag">JavaScript ES6+</span>
        <span class="skill-tag">Tailwind CSS</span>
        <span class="skill-tag">HTML5 / CSS3</span>
        <span class="skill-tag">Sass</span>
        <span class="skill-tag">Web Components</span>
      </div>

      <p style="font-size:12px; color:var(--text-3); text-transform:uppercase; letter-spacing:.08em; margin-bottom:10px; font-weight:600;">Backend &amp; Tools</p>
      <div class="skill-grid" style="margin-bottom:18px;">
        <span class="skill-tag">Node.js</span>
        <span class="skill-tag">Express.js</span>
        <span class="skill-tag">REST API Design</span>
        <span class="skill-tag">Git / GitHub</span>
        <span class="skill-tag">Webpack</span>
        <span class="skill-tag">npm / pnpm</span>
        <span class="skill-tag">Figma</span>
      </div>

      <p style="font-size:12px; color:var(--text-3); text-transform:uppercase; letter-spacing:.08em; margin-bottom:10px; font-weight:600;">Architecture &amp; Practices</p>
      <div class="skill-grid">
        <span class="skill-tag secondary">Clean Architecture</span>
        <span class="skill-tag secondary">SOLID Principles</span>
        <span class="skill-tag secondary">TDD</span>
        <span class="skill-tag secondary">Code Review</span>
        <span class="skill-tag secondary">CI/CD</span>
        <span class="skill-tag secondary">Responsive Design</span>
        <span class="skill-tag secondary">Accessibility (a11y)</span>
        <span class="skill-tag secondary">Design Patterns</span>
      </div>
    </div>

    <!-- Proficiency -->
    <div class="card">
      <div class="card-title">Proficiency Levels</div>
      <div class="prof-list">
        <div class="prof-item">
          <div class="prof-header"><span>⚛️ React &amp; Modern Frontend</span><span class="prof-pct">95%</span></div>
          <div class="prof-bar"><div class="prof-fill" style="width:95%;animation-delay:.1s"></div></div>
        </div>
        <div class="prof-item">
          <div class="prof-header"><span>🟦 TypeScript / JavaScript</span><span class="prof-pct">95%</span></div>
          <div class="prof-bar"><div class="prof-fill" style="width:95%;animation-delay:.2s"></div></div>
        </div>
        <div class="prof-item">
          <div class="prof-header"><span>🏗️ Software Architecture</span><span class="prof-pct">90%</span></div>
          <div class="prof-bar"><div class="prof-fill" style="width:90%;animation-delay:.3s"></div></div>
        </div>
        <div class="prof-item">
          <div class="prof-header"><span>🔌 REST API Integration</span><span class="prof-pct">90%</span></div>
          <div class="prof-bar"><div class="prof-fill" style="width:90%;animation-delay:.4s"></div></div>
        </div>
        <div class="prof-item">
          <div class="prof-header"><span>🧪 Unit Testing &amp; TDD</span><span class="prof-pct">80%</span></div>
          <div class="prof-bar"><div class="prof-fill" style="width:80%;animation-delay:.5s"></div></div>
        </div>
        <div class="prof-item">
          <div class="prof-header"><span>🎨 UI/UX Implementation</span><span class="prof-pct">80%</span></div>
          <div class="prof-bar"><div class="prof-fill" style="width:80%;animation-delay:.6s"></div></div>
        </div>
        <div class="prof-item">
          <div class="prof-header"><span>🖥️ Node.js / Backend</span><span class="prof-pct">75%</span></div>
          <div class="prof-bar"><div class="prof-fill" style="width:75%;animation-delay:.7s"></div></div>
        </div>
        <div class="prof-item">
          <div class="prof-header"><span>🔄 CI/CD &amp; Dev Workflows</span><span class="prof-pct">70%</span></div>
          <div class="prof-bar"><div class="prof-fill" style="width:70%;animation-delay:.8s"></div></div>
        </div>
      </div>
    </div>

    <!-- Portfolio -->
    <div class="card" id="portfolio">
      <div class="card-title">Portfolio Highlights</div>
      <div class="portfolio-grid">
        <div class="portfolio-item">
          <div class="port-icon">🌐</div>
          <div class="port-info">
            <div class="port-title">GBfixers.com — Tech Solutions Platform</div>
            <div class="port-desc">Full-stack platform connecting GB residents with tech repair &amp; digital solutions. Built from zero to production.</div>
            <div class="port-tags">
              <span class="port-tag">React</span>
              <span class="port-tag">Node.js</span>
              <span class="port-tag">REST API</span>
              <span class="port-tag">TypeScript</span>
            </div>
          </div>
        </div>
        <div class="portfolio-item">
          <div class="port-icon">⚛️</div>
          <div class="port-info">
            <div class="port-title">Scalable React Component Library</div>
            <div class="port-desc">Reusable, accessible component system with TypeScript generics and full unit test coverage.</div>
            <div class="port-tags">
              <span class="port-tag">React</span>
              <span class="port-tag">TypeScript</span>
              <span class="port-tag">TDD</span>
              <span class="port-tag">a11y</span>
            </div>
          </div>
        </div>
        <div class="portfolio-item">
          <div class="port-icon">🔌</div>
          <div class="port-info">
            <div class="port-title">REST API Platform — Clean Architecture</div>
            <div class="port-desc">Designed and implemented a multi-tenant API system following SOLID principles with error-handling layers.</div>
            <div class="port-tags">
              <span class="port-tag">Node.js</span>
              <span class="port-tag">Express</span>
              <span class="port-tag">Clean Arch</span>
            </div>
          </div>
        </div>
        <div class="portfolio-item">
          <div class="port-icon">🚀</div>
          <div class="port-info">
            <div class="port-title">Performance Optimization — 3x Speed Gain</div>
            <div class="port-desc">Profiled and refactored a legacy React app; reduced bundle size by 60% and cut LCP by 3×.</div>
            <div class="port-tags">
              <span class="port-tag">React</span>
              <span class="port-tag">Webpack</span>
              <span class="port-tag">Performance</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Expertise -->
    <div class="card" id="expertise">
      <div class="card-title">Core Expertise</div>
      <div class="expertise-list">
        <div class="expertise-item">
          <div class="exp-bullet">⚛️</div>
          <div class="exp-text"><strong>React &amp; Component Architecture</strong> — Hooks, context, performance tuning, reusable design systems, and clean component APIs.</div>
        </div>
        <div class="expertise-item">
          <div class="exp-bullet">🟦</div>
          <div class="exp-text"><strong>TypeScript — Strict &amp; Advanced</strong> — Generics, discriminated unions, utility types, and strict null safety across entire codebases.</div>
        </div>
        <div class="expertise-item">
          <div class="exp-bullet">🔌</div>
          <div class="exp-text"><strong>REST API Design &amp; Integration</strong> — End-to-end API contracts, error handling, versioning, and consumer-first design.</div>
        </div>
        <div class="expertise-item">
          <div class="exp-bullet">🏗️</div>
          <div class="exp-text"><strong>Software Architecture</strong> — Clean Architecture, SOLID, DRY, separation of concerns — systems built to survive years of change.</div>
        </div>
        <div class="expertise-item">
          <div class="exp-bullet">♿</div>
          <div class="exp-text"><strong>Accessibility (WCAG)</strong> — Inclusive UI, semantic HTML, ARIA patterns, keyboard navigation — compliance-ready by default.</div>
        </div>
      </div>
    </div>

    <!-- Philosophy -->
    <div class="card" id="philosophy">
      <div class="card-title">Problem Solving Philosophy</div>
      <div class="philosophy-box">
        Don't patch symptoms. Fix root causes. Build to last. Every bug is a clue,
        every requirement is a puzzle, and every deploy is a promise kept to the user.
        <div class="philosophy-attr">— Musiabe Hussain</div>
      </div>
      <div style="display:flex; gap:8px; margin-top:14px; flex-wrap:wrap;">
        <span style="font-size:13px; padding:6px 14px; border-radius:6px; background:var(--surface); border:1px solid var(--border); color:var(--text-2);">IDENTIFY</span>
        <span style="color:var(--text-3); line-height:2.2; font-size:14px;">→</span>
        <span style="font-size:13px; padding:6px 14px; border-radius:6px; background:var(--surface); border:1px solid var(--border); color:var(--text-2);">DIAGNOSE</span>
        <span style="color:var(--text-3); line-height:2.2; font-size:14px;">→</span>
        <span style="font-size:13px; padding:6px 14px; border-radius:6px; background:var(--surface); border:1px solid var(--border); color:var(--text-2);">ARCHITECT</span>
        <span style="color:var(--text-3); line-height:2.2; font-size:14px;">→</span>
        <span style="font-size:13px; padding:6px 14px; border-radius:6px; background:var(--cyan-dim); border:1px solid rgba(20,184,200,0.3); color:var(--cyan);">SHIP</span>
        <span style="color:var(--text-3); line-height:2.2; font-size:14px;">→</span>
        <span style="font-size:13px; padding:6px 14px; border-radius:6px; background:var(--surface); border:1px solid var(--border); color:var(--text-2);">ITERATE</span>
      </div>
    </div>

  </div><!-- /main -->

  <!-- ══ SIDEBAR ══ -->
  <div class="aside">

    <!-- Stats -->
    <div class="card">
      <div class="card-title">At a Glance</div>
      <div class="stat-grid">
        <div class="stat-box">
          <div class="stat-num">5+</div>
          <div class="stat-label">Years Exp.</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">47</div>
          <div class="stat-label">Projects</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">100%</div>
          <div class="stat-label">Job Success</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">5.0</div>
          <div class="stat-label">Rating</div>
        </div>
      </div>
    </div>

    <!-- CTA -->
    <div class="card" style="display:flex;flex-direction:column;gap:10px;">
      <div class="card-title">Open to Opportunities</div>
      <p style="font-size:13px; color:var(--text-2); margin-bottom:4px;">Remote roles · Consulting · Collaborations · High-impact projects</p>
      <a href="https://www.linkedin.com/in/musiabe-yash-1740b5213/" class="btn-primary" target="_blank">Hire Me on LinkedIn</a>
      <a href="https://gbfixers.com" class="btn-secondary" target="_blank">Visit GBfixers.com →</a>
    </div>

    <!-- Connect -->
    <div class="card">
      <div class="card-title">Connect</div>
      <div class="social-links">
        <a href="https://www.linkedin.com/in/musiabe-yash-1740b5213/" target="_blank" class="social-link">
          <span class="social-icon">💼</span> LinkedIn Profile
        </a>
        <a href="https://gbfixers.com" target="_blank" class="social-link">
          <span class="social-icon">🌐</span> GBfixers.com
        </a>
        <a href="https://github.com/musiabehussain" target="_blank" class="social-link">
          <span class="social-icon">🐙</span> GitHub
        </a>
        <a href="https://www.facebook.com/profile.php?id=100073595108212" target="_blank" class="social-link">
          <span class="social-icon">📘</span> Facebook
        </a>
      </div>
    </div>

    <!-- Location -->
    <div class="card">
      <div class="card-title">Location &amp; Availability</div>
      <div style="display:flex;flex-direction:column;gap:10px;">
        <div style="display:flex;align-items:center;gap:10px;font-size:13.5px;color:var(--text-2);">
          <span style="font-size:18px;">📍</span>
          <div><div style="color:var(--text-1);font-weight:500;">Gilgit-Baltistan, Pakistan</div><div style="font-size:12px;">UTC +5:00</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:10px;font-size:13.5px;color:var(--text-2);">
          <span style="font-size:18px;">⚡</span>
          <div><div style="color:var(--green);font-weight:500;">Available for Remote Work</div><div style="font-size:12px;">Full-time · Part-time · Contract</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:10px;font-size:13.5px;color:var(--text-2);">
          <span style="font-size:18px;">🕐</span>
          <div><div style="color:var(--text-1);font-weight:500;">Fast Responder</div><div style="font-size:12px;">Typically replies within 1 hour</div></div>
        </div>
      </div>
    </div>

    <!-- Mission -->
    <div class="card" style="background: linear-gradient(135deg,rgba(20,184,200,0.08),rgba(20,184,200,0.03)); border-color:rgba(20,184,200,0.2);">
      <div style="font-family:'Syne',sans-serif; font-weight:700; font-size:13px; color:var(--cyan); letter-spacing:.08em; text-transform:uppercase; margin-bottom:10px;">Mission</div>
      <p style="font-size:13.5px; color:var(--text-2); line-height:1.7; font-style:italic;">
        "Fix Problems. Ship Fast. Build Right."
      </p>
      <p style="font-size:12.5px; color:var(--text-3); margin-top:8px;">
        Crafted by Musiabe Hussain · Founder @ GBfixers.com · 2025
      </p>
    </div>

  </div><!-- /aside -->

</div><!-- /page -->

</body>
</html>
