<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Harmony Lab – PPC, Paid Media &amp; Web Design</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet" />
  <style>
    /* ── TOKENS ──────────────────────────────────────────────── */
    :root {
      --bg:          #070b12;
      --bg2:         #0c1020;
      --accent:      #18d4ff;
      --accent2:     #9147ff;
      --text:        #e2e8f0;
      --muted:       #94a3b8;
      --border:      rgba(255,255,255,.08);
      --card:        rgba(255,255,255,.04);
    }
    *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
    html { scroll-behavior:smooth; }
    body {
      font-family:'Inter',sans-serif;
      background:var(--bg);
      color:var(--text);
      overflow-x:hidden;
    }

    /* ── NAV ─────────────────────────────────────────────────── */
    #navbar {
      position:fixed; top:0; left:0; right:0; z-index:1000;
      padding:.9rem 2rem;
      background:rgba(8,12,20,.85);
      backdrop-filter:blur(18px);
      border-bottom:1px solid var(--border);
      display:flex; align-items:center; justify-content:space-between;
    }
    .nav-logo {
      font-family:'Space Grotesk',sans-serif;
      font-weight:700; font-size:1.15rem;
      color:var(--accent); letter-spacing:-.02em;
    }
    .nav-links { display:flex; gap:1.75rem; list-style:none; }
    .nav-links a {
      color:var(--muted); text-decoration:none;
      font-size:.88rem; font-weight:500;
      transition:color .3s;
    }
    .nav-links a:hover, .nav-links a.active { color:var(--accent); }
    /* hamburger */
    #nav-toggle {
      display:none; flex-direction:column; gap:5px;
      background:none; border:none; cursor:pointer; padding:4px;
    }
    #nav-toggle span {
      display:block; width:24px; height:2px;
      background:var(--text); border-radius:2px;
      transition:all .3s;
    }
    @media(max-width:640px){
      .nav-links {
        display:none; flex-direction:column; gap:1rem;
        position:absolute; top:100%; left:0; right:0;
        background:rgba(8,12,20,.97); padding:1.5rem 2rem;
        border-bottom:1px solid var(--border);
      }
      .nav-links.open { display:flex; }
      #nav-toggle { display:flex; }
    }

    /* ── HERO ────────────────────────────────────────────────── */
    #hero {
      position:relative; min-height:100vh;
      display:flex; align-items:center; justify-content:center;
      overflow:hidden;
    }
    #hero-canvas {
      position:absolute; inset:0; width:100%; height:100%;
    }
    .hero-content {
      position:relative; z-index:2;
      text-align:center; padding:2rem;
      max-width:860px;
    }
    .hero-badge {
      display:inline-flex; align-items:center; gap:.5rem;
      background:rgba(0,198,255,.1);
      border:1px solid rgba(0,198,255,.3);
      color:var(--accent); font-size:.75rem; font-weight:700;
      letter-spacing:.12em; text-transform:uppercase;
      padding:.4rem 1rem; border-radius:100px; margin-bottom:1.75rem;
    }
    .hero-badge-dot {
      width:8px; height:8px; background:var(--accent);
      border-radius:50%; animation:pulse-dot 2s infinite;
    }
    @keyframes pulse-dot {
      0%,100%{ opacity:1; transform:scale(1); }
      50%    { opacity:.4; transform:scale(1.6); }
    }
    .hero-name {
      font-family:'Space Grotesk',sans-serif;
      font-size:clamp(2.8rem,9vw,6rem);
      font-weight:700; letter-spacing:-.04em; line-height:1;
      margin-bottom:.9rem;
      background:linear-gradient(130deg,#fff 30%,var(--accent) 100%);
      -webkit-background-clip:text; -webkit-text-fill-color:transparent;
      background-clip:text;
    }
    .hero-subtitle {
      font-size:clamp(1rem,2.5vw,1.3rem);
      color:var(--muted); min-height:2.2em; margin-bottom:.6rem;
    }
    .hero-byline {
      font-size:.92rem; color:rgba(148,163,184,.65);
      margin-bottom:2.2rem; letter-spacing:.02em;
    }
    .hero-byline strong { color:rgba(148,163,184,.9); font-weight:500; }
    .cursor {
      display:inline-block; width:2px; height:1.1em;
      background:var(--accent); vertical-align:middle; margin-left:2px;
      animation:blink .75s step-end infinite;
    }
    @keyframes blink{ 50%{ opacity:0; } }
    .hero-cta { display:flex; gap:1rem; justify-content:center; flex-wrap:wrap; }
    .btn {
      padding:.85rem 2rem; border-radius:9px;
      font-weight:600; font-size:.95rem;
      text-decoration:none; transition:all .3s;
      cursor:pointer; border:none; font-family:'Inter',sans-serif;
      display:inline-block;
    }
    .btn-primary {
      background:linear-gradient(135deg,var(--accent),var(--accent2));
      color:#fff; box-shadow:0 0 30px rgba(0,198,255,.3);
    }
    .btn-primary:hover { transform:translateY(-3px); box-shadow:0 0 50px rgba(0,198,255,.5); }
    .btn-outline {
      background:transparent; color:var(--text);
      border:1px solid var(--border);
    }
    .btn-outline:hover {
      background:var(--card); border-color:var(--accent);
      color:var(--accent); transform:translateY(-3px);
    }

    /* ── SECTION COMMON ──────────────────────────────────────── */
    .section-wrap { padding:6rem 2rem; max-width:1080px; margin:0 auto; }
    .section-bg { background:var(--bg2); }
    .section-label {
      font-size:.72rem; font-weight:700; letter-spacing:.16em;
      text-transform:uppercase; color:var(--accent); margin-bottom:.6rem;
    }
    .section-title {
      font-family:'Space Grotesk',sans-serif;
      font-size:clamp(1.9rem,5vw,2.9rem);
      font-weight:700; letter-spacing:-.025em; margin-bottom:.75rem;
    }
    .section-line {
      width:56px; height:3px;
      background:linear-gradient(90deg,var(--accent),var(--accent2));
      border-radius:2px; margin-bottom:3rem;
    }

    /* ── ABOUT ───────────────────────────────────────────────── */
    .about-grid {
      display:grid; grid-template-columns:1fr 1fr;
      gap:4rem; align-items:start;
    }
    @media(max-width:768px){ .about-grid{ grid-template-columns:1fr; gap:2.5rem; } }
    .about-text p {
      color:var(--muted); line-height:1.8;
      font-size:1.02rem; margin-bottom:1rem;
    }
    .about-text p strong { color:var(--text); }
    .about-tags { display:flex; flex-wrap:wrap; gap:.5rem; margin-top:1.5rem; }
    .tag {
      background:rgba(0,198,255,.08); border:1px solid rgba(0,198,255,.2);
      color:var(--accent); font-size:.78rem; font-weight:500;
      padding:.3rem .8rem; border-radius:100px;
    }
    .stats-grid {
      display:grid; grid-template-columns:1fr 1fr; gap:1.25rem;
    }
    .stat-card {
      background:var(--card); border:1px solid var(--border);
      border-radius:14px; padding:1.75rem 1.5rem; text-align:center;
      transition:all .3s; position:relative; overflow:hidden;
    }
    .stat-card::before {
      content:''; position:absolute; top:0; left:0; right:0; height:2px;
      background:linear-gradient(90deg,var(--accent),var(--accent2));
      transform:scaleX(0); transition:transform .3s;
    }
    .stat-card:hover::before { transform:scaleX(1); }
    .stat-card:hover { transform:translateY(-5px); border-color:rgba(0,198,255,.3); }
    .stat-number {
      font-family:'Space Grotesk',sans-serif; font-size:2.5rem; font-weight:700;
      background:linear-gradient(135deg,var(--accent),var(--accent2));
      -webkit-background-clip:text; -webkit-text-fill-color:transparent;
      background-clip:text;
    }
    .stat-label { color:var(--muted); font-size:.82rem; margin-top:.25rem; }

    /* ── SERVICES ────────────────────────────────────────────── */
    .services-grid {
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(290px,1fr));
      gap:1.4rem;
    }
    .service-card {
      background:var(--card); border:1px solid var(--border);
      border-radius:16px; padding:2rem; transition:all .3s;
      cursor:default; position:relative; overflow:hidden;
    }
    .service-card::after {
      content:''; position:absolute; inset:0;
      background:linear-gradient(135deg,rgba(0,198,255,.06),rgba(124,58,237,.06));
      opacity:0; transition:opacity .3s;
    }
    .service-card:hover { transform:translateY(-7px); border-color:rgba(0,198,255,.35); }
    .service-card:hover::after { opacity:1; }
    .svc-icon {
      width:50px; height:50px;
      background:linear-gradient(135deg,rgba(0,198,255,.15),rgba(124,58,237,.15));
      border-radius:12px; display:flex; align-items:center;
      justify-content:center; font-size:1.4rem; margin-bottom:1.2rem;
    }
    .svc-title {
      font-family:'Space Grotesk',sans-serif;
      font-size:1.05rem; font-weight:600; margin-bottom:.5rem;
    }
    .svc-desc { color:var(--muted); font-size:.88rem; line-height:1.7; }

    /* ── SKILLS ──────────────────────────────────────────────── */
    .skills-grid {
      display:flex; flex-wrap:wrap; gap:1rem 1.5rem;
    }
    .skill-tag {
      font-size:.95rem; font-weight:500; color:var(--text);
      padding-bottom:5px;
      background-image:linear-gradient(90deg,var(--accent),var(--accent2));
      background-repeat:no-repeat;
      background-size:100% 2px;
      background-position:bottom left;
    }

    /* ── EXPERIENCE TIMELINE ─────────────────────────────────── */
    .timeline { position:relative; padding-left:1.5rem; }
    .timeline::before {
      content:''; position:absolute; left:0; top:.3rem; bottom:0;
      width:2px;
      background:linear-gradient(180deg,var(--accent),var(--accent2),transparent);
    }
    .tl-item {
      position:relative; margin-bottom:3rem; padding-left:2rem;
      opacity:0; transform:translateX(-24px); transition:all .65s;
    }
    .tl-item.visible { opacity:1; transform:translateX(0); }
    .tl-dot {
      position:absolute; left:-2.18rem; top:.3rem;
      width:14px; height:14px; background:var(--accent);
      border-radius:50%; box-shadow:0 0 16px rgba(0,198,255,.65);
    }
    .tl-period {
      font-size:.75rem; font-weight:700; letter-spacing:.07em;
      text-transform:uppercase; color:var(--accent); margin-bottom:.35rem;
    }
    .tl-role {
      font-family:'Space Grotesk',sans-serif;
      font-size:1.25rem; font-weight:600; margin-bottom:.15rem;
    }
    .tl-company { color:var(--muted); font-size:.9rem; margin-bottom:.9rem; }
    .tl-list { list-style:none; display:flex; flex-direction:column; gap:.45rem; }
    .tl-list li {
      color:var(--muted); font-size:.88rem; line-height:1.65;
      padding-left:1.1rem; position:relative;
    }
    .tl-list li::before { content:'▸'; position:absolute; left:0; color:var(--accent); }

    .reveal-btn {
      background:rgba(0,198,255,.1); border:1px solid rgba(0,198,255,.3);
      color:var(--accent); font-size:.83rem; font-weight:600;
      padding:.3rem .85rem; border-radius:100px; cursor:pointer;
      font-family:'Inter',sans-serif; transition:all .25s;
    }
    .reveal-btn:hover { background:rgba(0,198,255,.2); border-color:var(--accent); }
    #phone-number { color:var(--muted); text-decoration:none; font-size:.88rem; transition:color .3s; }
    #phone-number:hover { color:var(--accent); }

    /* ── CONTACT ─────────────────────────────────────────────── */
    .contact-grid {
      display:grid; grid-template-columns:1fr 1.5fr;
      gap:4rem; align-items:start;
    }
    @media(max-width:768px){ .contact-grid{ grid-template-columns:1fr; gap:2.5rem; } }
    .contact-info h3 {
      font-family:'Space Grotesk',sans-serif;
      font-size:1.45rem; font-weight:600; margin-bottom:.9rem;
    }
    .contact-info p { color:var(--muted); line-height:1.8; margin-bottom:2rem; font-size:.97rem; }
    .contact-links { display:flex; flex-direction:column; gap:.75rem; }
    .contact-link {
      display:flex; align-items:center; gap:.75rem;
      color:var(--muted); text-decoration:none;
      font-size:.88rem; transition:color .3s;
    }
    .contact-link:hover { color:var(--accent); }
    .cl-icon {
      width:36px; height:36px; background:var(--card);
      border:1px solid var(--border); border-radius:9px;
      display:flex; align-items:center; justify-content:center;
      font-size:.95rem; flex-shrink:0;
    }
    .contact-form-box {
      background:var(--card); border:1px solid var(--border);
      border-radius:20px; padding:2.5rem;
    }
    .form-group { margin-bottom:1.2rem; }
    .form-label {
      display:block; font-size:.82rem; font-weight:500;
      color:var(--muted); margin-bottom:.45rem;
    }
    .form-input {
      width:100%; background:rgba(255,255,255,.05);
      border:1px solid var(--border); color:var(--text);
      font-family:'Inter',sans-serif; font-size:.93rem;
      padding:.75rem 1rem; border-radius:10px; outline:none;
      transition:border-color .3s, box-shadow .3s;
    }
    .form-input::placeholder { color:rgba(148,163,184,.5); }
    .form-input:focus {
      border-color:var(--accent);
      box-shadow:0 0 0 3px rgba(0,198,255,.12);
    }
    textarea.form-input { resize:vertical; min-height:120px; }
    .form-submit {
      width:100%; padding:.9rem;
      background:linear-gradient(135deg,var(--accent),var(--accent2));
      color:#fff; font-family:'Inter',sans-serif; font-size:.97rem;
      font-weight:600; border:none; border-radius:10px; cursor:pointer;
      transition:all .3s; box-shadow:0 0 28px rgba(0,198,255,.2);
      margin-top:.25rem;
    }
    .form-submit:hover { transform:translateY(-2px); box-shadow:0 0 44px rgba(0,198,255,.4); }
    .form-submit:disabled { opacity:.65; cursor:not-allowed; transform:none; }
    .form-msg {
      text-align:center; padding:.7rem; border-radius:9px;
      font-size:.88rem; font-weight:500; margin-top:1rem; display:none;
    }
    .form-msg.success {
      background:rgba(74,222,128,.1); border:1px solid rgba(74,222,128,.3);
      color:#4ade80; display:block;
    }
    .form-msg.error {
      background:rgba(248,113,113,.1); border:1px solid rgba(248,113,113,.3);
      color:#f87171; display:block;
    }

    /* ── FOOTER ──────────────────────────────────────────────── */
    footer {
      text-align:center; padding:2rem;
      color:var(--muted); font-size:.83rem;
      border-top:1px solid var(--border);
    }

    /* ── SCROLL-TO-TOP ───────────────────────────────────────── */
    #scroll-top {
      position:fixed; bottom:2rem; right:2rem;
      width:44px; height:44px;
      background:linear-gradient(135deg,var(--accent),var(--accent2));
      border:none; border-radius:12px; color:#fff; font-size:1.1rem;
      cursor:pointer; z-index:999;
      opacity:0; transform:translateY(16px); transition:all .3s;
    }
    #scroll-top.visible { opacity:1; transform:translateY(0); }
    #scroll-top:hover { transform:translateY(-3px); }

    /* ── FADE-IN ─────────────────────────────────────────────── */
    .fade-in {
      opacity:0; transform:translateY(32px);
      transition:opacity .75s ease, transform .75s ease;
    }
    .fade-in.visible { opacity:1; transform:translateY(0); }
  </style>
</head>
<body>

<!-- ══ NAV ══════════════════════════════════════════════════════ -->
<nav id="navbar">
  <div class="nav-logo">Harmony Lab</div>
  <button id="nav-toggle" aria-label="Toggle navigation">
    <span></span><span></span><span></span>
  </button>
  <ul class="nav-links" id="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- ══ HERO ══════════════════════════════════════════════════════ -->
<section id="hero">
  <canvas id="hero-canvas"></canvas>
  <div class="hero-content">
    <div class="hero-badge">
      <span class="hero-badge-dot"></span>
      Available for new projects
    </div>
    <h1 class="hero-name">Harmony Lab</h1>
    <p class="hero-subtitle" id="hero-subtitle"></p>
    <p class="hero-byline">led by <strong>Dr. Ákos Hornung</strong></p>
    <div class="hero-cta">
      <a href="#contact" class="btn btn-primary">Let's Work Together</a>
      <a href="#about"   class="btn btn-outline">Learn More</a>
    </div>
  </div>
</section>

<!-- ══ ABOUT ══════════════════════════════════════════════════════ -->
<div id="about-wrap">
  <div class="section-wrap fade-in" id="about">
    <div class="section-label">About Us</div>
    <h2 class="section-title">Performance marketing meets sharp design</h2>
    <div class="section-line"></div>
    <div class="about-grid">
      <div class="about-text">
        <p><strong>Harmony Lab</strong> is a boutique digital agency based in Pécs, Hungary, specialising in paid media management and web design. We combine data-driven campaign strategy with conversion-focused design to deliver measurable growth for our clients.</p>
        <p>Our expertise spans <strong>PPC &amp; Paid Media</strong> — managing high-performance campaigns across Google Ads, Meta Ads, TikTok, and Microsoft Advertising — and <strong>Website &amp; Landing Page design</strong> built to convert the traffic we drive.</p>
        <p>With <strong>8 years of Project Management experience</strong> in multinational R&amp;D, we bring the same rigour to every client engagement — structured planning, budget discipline, and clear communication. Managing a campaign portfolio is no different from managing a project pipeline: both demand clear targets, fast iteration, and accountability for results.</p>
        <p>We design and build websites from layout and UX to interactive JavaScript elements. A well-designed landing page is part of the campaign: it's where ad spend either converts or dies.</p>
        <div class="about-tags">
          <span class="tag">Google Ads</span>
          <span class="tag">Meta Ads</span>
          <span class="tag">TikTok Ads</span>
          <span class="tag">Microsoft Ads</span>
          <span class="tag">GA4</span>
          <span class="tag">Google Tag Manager</span>
          <span class="tag">A/B Testing</span>
          <span class="tag">Mailchimp</span>
          <span class="tag">HTML &amp; CSS</span>
          <span class="tag">JavaScript</span>
          <span class="tag">UI/UX Design</span>
          <span class="tag">Python</span>
          <span class="tag">Data Analysis</span>
        </div>
      </div>
      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-number" data-target="3" data-suffix="+">0</div>
          <div class="stat-label">Years PPC Experience</div>
        </div>
        <div class="stat-card">
          <div class="stat-number" data-target="8" data-suffix="+">0</div>
          <div class="stat-label">Years Project Management</div>
        </div>
        <div class="stat-card">
          <div class="stat-number" data-target="4">0</div>
          <div class="stat-label">Ad Platforms</div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ══ SERVICES ════════════════════════════════════════════════════ -->
<div class="section-bg">
  <div class="section-wrap fade-in" id="services">
    <div class="section-label">What We Do</div>
    <h2 class="section-title">Paid Media &amp; Web Design</h2>
    <div class="section-line"></div>
    <div class="services-grid">

      <div class="service-card">
        <div class="svc-icon">🎯</div>
        <h3 class="svc-title">Google Ads</h3>
        <p class="svc-desc">Search, Display, and YouTube campaigns built for performance. Keyword research, smart bidding strategies, and continuous optimisation to drive qualified traffic and measurable conversions.</p>
      </div>

      <div class="service-card">
        <div class="svc-icon">📱</div>
        <h3 class="svc-title">Meta Ads</h3>
        <p class="svc-desc">Facebook &amp; Instagram campaigns from prospecting to retargeting. Audience building, creative testing, and ROAS optimisation across the full funnel.</p>
      </div>

      <div class="service-card">
        <div class="svc-icon">⚡</div>
        <h3 class="svc-title">TikTok &amp; Microsoft Ads</h3>
        <p class="svc-desc">Expanding reach beyond core platforms. TikTok for mobile-first audiences and Microsoft Advertising (Bing) for B2B targeting or cost-efficient incremental reach.</p>
      </div>

      <div class="service-card">
        <div class="svc-icon">📊</div>
        <h3 class="svc-title">Analytics &amp; Tracking</h3>
        <p class="svc-desc">Full conversion tracking setup via Meta Pixel, Google Tag Manager, and GA4. Reliable, clean data is the foundation of every optimisation decision I make.</p>
      </div>

      <div class="service-card">
        <div class="svc-icon">🧪</div>
        <h3 class="svc-title">A/B Testing &amp; CRO</h3>
        <p class="svc-desc">Systematic testing of creatives, audiences, landing pages, and bid strategies to consistently improve ROAS and reduce CPA over the campaign lifecycle.</p>
      </div>

      <div class="service-card">
        <div class="svc-icon">✉️</div>
        <h3 class="svc-title">Email Marketing</h3>
        <p class="svc-desc">Mailchimp campaign creation, automated drip flows, and algorithmic mailing systems to nurture leads and re-engage customers throughout the funnel.</p>
      </div>

      <div class="service-card">
        <div class="svc-icon">🖥️</div>
        <h3 class="svc-title">Website Design &amp; Development</h3>
        <p class="svc-desc">Clean, conversion-focused websites and landing pages built with HTML, CSS, and JavaScript. Responsive layouts, fast load times, and UX best practices — designed to turn visitors into leads.</p>
      </div>

      <div class="service-card">
        <div class="svc-icon">⚙️</div>
        <h3 class="svc-title">Interactive &amp; Dynamic UI</h3>
        <p class="svc-desc">Custom JavaScript interactions, animated elements, and dynamic components that bring pages to life. Every visual detail is purposeful — engaging users without sacrificing performance or clarity.</p>
      </div>

      <div class="service-card">
        <div class="svc-icon">🔗</div>
        <h3 class="svc-title">Landing Page Optimisation</h3>
        <p class="svc-desc">Ad campaigns and landing pages designed together for maximum conversion. Clear messaging hierarchy, trust signals, strong CTAs, and technical tracking setup — closing the loop from click to conversion.</p>
      </div>

    </div>
  </div>
</div>

<!-- ══ SKILLS ══════════════════════════════════════════════════════ -->
<div id="skills-wrap">
  <div class="section-wrap fade-in" id="skills">
    <div class="section-label">Our Expertise</div>
    <h2 class="section-title">Skills &amp; Proficiency</h2>
    <div class="section-line"></div>
    <div class="skills-grid">

      <span class="skill-tag">Meta Ads Manager</span>
      <span class="skill-tag">Google Ads</span>
      <span class="skill-tag">Google Analytics 4</span>
      <span class="skill-tag">Conversion Tracking / GTM</span>
      <span class="skill-tag">A/B Testing &amp; CRO</span>
      <span class="skill-tag">Keyword Research</span>
      <span class="skill-tag">TikTok Ads</span>
      <span class="skill-tag">Microsoft Advertising</span>
      <span class="skill-tag">Email Marketing / Mailchimp</span>
      <span class="skill-tag">Project Management</span>
      <span class="skill-tag">Data Analysis &amp; AI Tools</span>
      <span class="skill-tag">Python &amp; Scripting</span>
      <span class="skill-tag">HTML &amp; CSS</span>
      <span class="skill-tag">JavaScript</span>
      <span class="skill-tag">Responsive / UX Design</span>
      <span class="skill-tag">Landing Page CRO</span>

    </div>
  </div>
</div>

<!-- ══ EXPERIENCE ══════════════════════════════════════════════════ -->
<div class="section-bg">
  <div class="section-wrap fade-in" id="experience">
    <div class="section-label">Our Background</div>
    <h2 class="section-title">Experience Behind the Services</h2>
    <div class="section-line"></div>
    <div class="timeline">

      <div class="tl-item">
        <div class="tl-dot"></div>
        <div class="tl-period">Mar 2023 – Present</div>
        <div class="tl-role">Paid Media Management</div>
        <div class="tl-company">Harmony Lab — PPC &amp; Paid Media Services</div>
        <ul class="tl-list">
          <li>Managing and optimising paid campaigns across Meta Ads and Google Ads for maximum ROAS and efficiency.</li>
          <li>Improving client ROAS through A/B testing of creatives, audiences, and bidding strategies.</li>
          <li>Keyword research and full implementation of Google Search, Display, and YouTube campaigns.</li>
          <li>Conversion tracking setup and maintenance using Meta Pixel and Google Tag Manager.</li>
          <li>Performance monitoring via Google Analytics 4 with regular data-driven optimisation reporting.</li>
          <li>Mailchimp email campaigns, automated flows, and algorithmic mailing systems for client retention.</li>
        </ul>
      </div>

      <div class="tl-item">
        <div class="tl-dot"></div>
        <div class="tl-period">Aug 2018 – Present</div>
        <div class="tl-role">Project Management &amp; Analytics</div>
        <div class="tl-company">Harmony Lab — Strategy &amp; Project Services</div>
        <ul class="tl-list">
          <li>End-to-end project planning: timetables, budgets, resource allocation, and milestone tracking for complex client engagements.</li>
          <li>Coordination of interdisciplinary teams and international stakeholder management.</li>
          <li>Integration of evolving client requirements into live projects while maintaining schedule and budget targets.</li>
          <li>High-dimensional data analysis, AI-assisted analytics, and Python scripting applied to campaign and business data.</li>
          <li>Concept and business development support — arriving at solutions that are both technically sound and commercially viable.</li>
        </ul>
      </div>

    </div>
  </div>
</div>

<!-- ══ CONTACT ═════════════════════════════════════════════════════ -->
<div id="contact-wrap">
  <div class="section-wrap fade-in" id="contact">
    <div class="section-label">Get In Touch</div>
    <h2 class="section-title">Let's Work Together</h2>
    <div class="section-line"></div>
    <div class="contact-grid">

      <div class="contact-info">
        <h3>Ready to grow your results online?</h3>
        <p>Whether you need high-performance paid campaigns, a conversion-focused website, or both working together — Harmony Lab can help. Drop us a message and we'll get back to you promptly.</p>
        <div class="contact-links">
          <span class="contact-link">
            <div class="cl-icon">👤</div>
            Dr. Ákos Hornung
          </span>
          <div class="contact-link">
            <div class="cl-icon">📞</div>
            <span id="phone-reveal-wrap">
              <button id="phone-reveal-btn" class="reveal-btn">Show phone number</button>
              <a id="phone-number" href="tel:+36703307153" style="display:none">+36 70 330 7153</a>
            </span>
          </div>
          <span class="contact-link">
            <div class="cl-icon">📍</div>
            Pécs, Hungary
          </span>
        </div>
      </div>

      <div class="contact-form-box">
        <form id="contact-form" action="https://formspree.io/f/mvznvbyr" method="POST">
          <div class="form-group">
            <label class="form-label" for="cf-name">Your Name</label>
            <input class="form-input" type="text" id="cf-name" name="name" placeholder="Jane Smith" required />
          </div>
          <div class="form-group">
            <label class="form-label" for="cf-email">Your Email</label>
            <input class="form-input" type="email" id="cf-email" name="email" placeholder="jane@company.com" required />
          </div>
          <div class="form-group">
            <label class="form-label" for="cf-message">Message</label>
            <textarea class="form-input" id="cf-message" name="message" placeholder="Tell me about your project or campaign goals…" required></textarea>
          </div>
          <button type="submit" class="form-submit" id="submit-btn">Send Message →</button>
          <div class="form-msg" id="form-msg"></div>
        </form>
      </div>

    </div>
  </div>
</div>

<!-- ══ FOOTER ══════════════════════════════════════════════════════ -->
<footer>
  <p>© 2025 Harmony Lab · Dr. Ákos Hornung · Pécs, Hungary</p>
</footer>

<!-- ══ SCROLL-TO-TOP ════════════════════════════════════════════════ -->
<button id="scroll-top" title="Back to top">↑</button>

<!-- ══════════════════════════════════════════════════════════════════
     JAVASCRIPT
═══════════════════════════════════════════════════════════════════ -->
<script>
(function(){
  'use strict';

  /* ── PARTICLE CANVAS ─────────────────────────────────────────── */
  const canvas = document.getElementById('hero-canvas');
  const ctx    = canvas.getContext('2d');
  let W, H, particles = [];
  let mx = -999, my = -999;

  function resize(){
    W = canvas.width  = window.innerWidth;
    H = canvas.height = window.innerHeight;
  }
  resize();
  window.addEventListener('resize', () => { resize(); buildParticles(); });
  window.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });

  function buildParticles(){
    particles = [];
    const n = Math.min(Math.floor(W * H / 11000), 120);
    for(let i = 0; i < n; i++){
      particles.push({
        x:  Math.random() * W,
        y:  Math.random() * H,
        vx: (Math.random() - .5) * .45,
        vy: (Math.random() - .5) * .45,
        r:  Math.random() * 1.8 + .4,
        a:  Math.random() * .55 + .2
      });
    }
  }
  buildParticles();

  function drawFrame(){
    /* gradient bg */
    const g = ctx.createRadialGradient(W/2, H/2, 0, W/2, H/2, W * .85);
    g.addColorStop(0, '#0d1625');
    g.addColorStop(1, '#080c14');
    ctx.fillStyle = g;
    ctx.fillRect(0, 0, W, H);

    for(let i = 0; i < particles.length; i++){
      const p = particles[i];
      /* mouse repulsion */
      const dx = p.x - mx, dy = p.y - my;
      const d2 = dx*dx + dy*dy;
      if(d2 < 14400){ /* 120px radius */
        const f = (14400 - d2) / 14400 * .014;
        p.vx += dx * f; p.vy += dy * f;
      }
      p.vx *= .98; p.vy *= .98;
      p.x += p.vx; p.y += p.vy;
      if(p.x < 0) p.x = W; if(p.x > W) p.x = 0;
      if(p.y < 0) p.y = H; if(p.y > H) p.y = 0;

      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI*2);
      ctx.fillStyle = `rgba(0,198,255,${p.a})`;
      ctx.fill();

      /* connections */
      for(let j = i+1; j < particles.length; j++){
        const q = particles[j];
        const dx2 = p.x-q.x, dy2 = p.y-q.y;
        const dist = Math.sqrt(dx2*dx2 + dy2*dy2);
        if(dist < 105){
          ctx.beginPath();
          ctx.moveTo(p.x, p.y); ctx.lineTo(q.x, q.y);
          ctx.strokeStyle = `rgba(0,198,255,${.18*(1-dist/105)})`;
          ctx.lineWidth = .5;
          ctx.stroke();
        }
      }
    }
    requestAnimationFrame(drawFrame);
  }
  drawFrame();


  /* ── TYPING ANIMATION ────────────────────────────────────────── */
  const phrases = [
    'PPC & Paid Media Specialist',
    'Google Ads & Meta Ads Expert',
    'Web Designer & Developer',
    'Performance Campaign Manager',
    'Landing Page Specialist',
    'Data-Driven Growth Partner'
  ];
  let pi = 0, ci = 0, del = false;
  const subtitleEl = document.getElementById('hero-subtitle');
  function type(){
    const cur = phrases[pi];
    const shown = del ? cur.slice(0, ci--) : cur.slice(0, ci++);
    subtitleEl.innerHTML = shown + '<span class="cursor"></span>';
    let speed = del ? 38 : 78;
    if(!del && ci > cur.length)       { del = true;  speed = 1900; }
    else if(del && ci < 0)            { del = false; pi = (pi+1)%phrases.length; ci = 0; speed = 380; }
    setTimeout(type, speed);
  }
  type();


  /* ── INTERSECTION OBSERVER ───────────────────────────────────── */
  let countersAnimated = false;

  const io = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if(!entry.isIntersecting) return;
      const el = entry.target;
      el.classList.add('visible');

      /* counters */
      if(el.id === 'about' && !countersAnimated){
        countersAnimated = true;
        el.querySelectorAll('[data-target]').forEach(animCounter);
      }

      /* timeline items */
      el.querySelectorAll('.tl-item').forEach((item, i) => {
        setTimeout(() => item.classList.add('visible'), i * 220);
      });
    });
  }, { threshold: 0.12 });

  document.querySelectorAll('.fade-in').forEach(el => io.observe(el));


  /* ── COUNTER ANIMATION ───────────────────────────────────────── */
  function animCounter(el){
    const target = parseInt(el.dataset.target, 10);
    const fmt    = el.dataset.format;
    const suffix = el.dataset.suffix || '';
    const dur    = 1600;
    const step   = target / (dur / 16);
    let cur = 0;
    const t = setInterval(() => {
      cur = Math.min(cur + step, target);
      let display;
      if(fmt === 'dollar'){
        display = '$' + Math.floor(cur / 1000) + 'K';
      } else {
        display = Math.floor(cur);
      }
      el.textContent = display + (cur >= target ? suffix : '');
      if(cur >= target) clearInterval(t);
    }, 16);
  }


  /* ── NAV ACTIVE + SCROLL-TOP ─────────────────────────────────── */
  const navAs   = document.querySelectorAll('.nav-links a');
  const scrollBtn = document.getElementById('scroll-top');
  const trackedIds = ['about','services','skills','experience','contact'];

  window.addEventListener('scroll', () => {
    const sy = window.scrollY;
    scrollBtn.classList.toggle('visible', sy > 400);
    let current = '';
    trackedIds.forEach(id => {
      const sec = document.getElementById(id);
      if(sec && sy >= sec.getBoundingClientRect().top + sy - 220) current = id;
    });
    navAs.forEach(a => a.classList.toggle('active', a.getAttribute('href') === '#'+current));
  }, { passive: true });

  scrollBtn.addEventListener('click', () => window.scrollTo({ top: 0, behavior: 'smooth' }));


  /* ── HAMBURGER ───────────────────────────────────────────────── */
  document.getElementById('nav-toggle').addEventListener('click', () => {
    document.getElementById('nav-links').classList.toggle('open');
  });
  document.querySelectorAll('.nav-links a').forEach(a => {
    a.addEventListener('click', () => document.getElementById('nav-links').classList.remove('open'));
  });


  /* ── PHONE REVEAL ────────────────────────────────────────── */
  document.getElementById('phone-reveal-btn').addEventListener('click', function(){
    this.style.display = 'none';
    document.getElementById('phone-number').style.display = 'inline';
  });

  /* ── CONTACT FORM (Formspree AJAX) ───────────────────────────── */
  const form      = document.getElementById('contact-form');
  const submitBtn = document.getElementById('submit-btn');
  const formMsg   = document.getElementById('form-msg');

  form.addEventListener('submit', async e => {
    e.preventDefault();
    submitBtn.disabled    = true;
    submitBtn.textContent = 'Sending…';
    formMsg.className     = 'form-msg';

    try {
      const res = await fetch(form.action, {
        method:  'POST',
        body:    new FormData(form),
        headers: { 'Accept': 'application/json' }
      });
      if(res.ok){
        formMsg.textContent = '✓ Message sent! I\'ll get back to you soon.';
        formMsg.className   = 'form-msg success';
        form.reset();
      } else {
        throw new Error();
      }
    } catch {
      formMsg.textContent = '✗ Something went wrong. Please try again later.';
      formMsg.className   = 'form-msg error';
    }

    submitBtn.disabled    = false;
    submitBtn.textContent = 'Send Message →';
  });

})();
</script>
</body>
</html>
