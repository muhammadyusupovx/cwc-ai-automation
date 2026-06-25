<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CWC AI — Automate Your Business</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=Inter:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --black: #0A0A0F;
      --surface: #111118;
      --card: #16161F;
      --border: rgba(255,255,255,0.07);
      --white: #F0EFF8;
      --muted: #7B7A8E;
      --accent: #7C5CFC;
      --accent2: #C084FC;
      --glow: rgba(124,92,252,0.18);
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--black);
      color: var(--white);
      font-family: 'Inter', sans-serif;
      font-weight: 300;
      line-height: 1.6;
      overflow-x: hidden;
    }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 20px 48px;
      background: rgba(10,10,15,0.85);
      backdrop-filter: blur(16px);
      border-bottom: 1px solid var(--border);
    }
    .logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800; font-size: 1.3rem;
      letter-spacing: -0.02em;
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    }
    .nav-links { display: flex; gap: 32px; list-style: none; }
    .nav-links a {
      color: var(--muted); text-decoration: none; font-size: 0.9rem;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--white); }
    .nav-cta {
      background: var(--accent); color: #fff;
      border: none; padding: 10px 22px; border-radius: 8px;
      font-family: 'Inter', sans-serif; font-size: 0.88rem; font-weight: 500;
      cursor: pointer; transition: opacity 0.2s;
    }
    .nav-cta:hover { opacity: 0.85; }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      text-align: center;
      padding: 120px 24px 80px;
      position: relative;
      overflow: hidden;
    }
    .hero::before {
      content: '';
      position: absolute; top: -200px; left: 50%; transform: translateX(-50%);
      width: 800px; height: 800px;
      background: radial-gradient(circle, rgba(124,92,252,0.12) 0%, transparent 70%);
      pointer-events: none;
    }
    .hero-badge {
      display: inline-flex; align-items: center; gap: 8px;
      background: rgba(124,92,252,0.12);
      border: 1px solid rgba(124,92,252,0.3);
      padding: 6px 16px; border-radius: 100px;
      font-size: 0.8rem; color: var(--accent2);
      margin-bottom: 32px; letter-spacing: 0.04em;
    }
    .hero-badge span { width: 6px; height: 6px; border-radius: 50%; background: var(--accent2); animation: pulse 2s infinite; }
    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }

    h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2.8rem, 7vw, 5.5rem);
      font-weight: 800;
      line-height: 1.05;
      letter-spacing: -0.03em;
      max-width: 820px;
      margin-bottom: 24px;
    }
    h1 em {
      font-style: normal;
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    }
    .hero-sub {
      font-size: 1.1rem; color: var(--muted);
      max-width: 520px; margin: 0 auto 48px;
      line-height: 1.7;
    }
    .hero-actions { display: flex; gap: 16px; flex-wrap: wrap; justify-content: center; }
    .btn-primary {
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      color: #fff; border: none;
      padding: 14px 32px; border-radius: 10px;
      font-family: 'Inter', sans-serif; font-size: 0.95rem; font-weight: 500;
      cursor: pointer; transition: transform 0.2s, box-shadow 0.2s;
      box-shadow: 0 0 32px rgba(124,92,252,0.3);
    }
    .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 0 48px rgba(124,92,252,0.45); }
    .btn-ghost {
      background: transparent; color: var(--white);
      border: 1px solid var(--border);
      padding: 14px 32px; border-radius: 10px;
      font-family: 'Inter', sans-serif; font-size: 0.95rem; font-weight: 400;
      cursor: pointer; transition: border-color 0.2s, background 0.2s;
    }
    .btn-ghost:hover { border-color: var(--accent); background: rgba(124,92,252,0.06); }

    /* STATS BAR */
    .stats-bar {
      display: flex; justify-content: center; gap: 64px;
      flex-wrap: wrap;
      padding: 40px 24px;
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      margin: 0 48px;
    }
    .stat-item { text-align: center; }
    .stat-num {
      font-family: 'Syne', sans-serif;
      font-size: 2rem; font-weight: 800;
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    }
    .stat-label { font-size: 0.82rem; color: var(--muted); margin-top: 4px; }

    /* SECTION */
    section { padding: 100px 24px; max-width: 1100px; margin: 0 auto; }
    .section-eye {
      font-size: 0.75rem; letter-spacing: 0.12em;
      color: var(--accent); text-transform: uppercase;
      margin-bottom: 14px; font-weight: 500;
    }
    h2 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 800; letter-spacing: -0.02em;
      line-height: 1.1; margin-bottom: 16px;
    }
    .section-sub { color: var(--muted); max-width: 480px; margin-bottom: 56px; font-size: 1rem; }

    /* SERVICES GRID */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
    }
    .service-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 32px;
      transition: border-color 0.3s, transform 0.3s;
      position: relative; overflow: hidden;
    }
    .service-card::before {
      content: '';
      position: absolute; top: 0; left: 0; right: 0; height: 2px;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      opacity: 0; transition: opacity 0.3s;
    }
    .service-card:hover { border-color: rgba(124,92,252,0.3); transform: translateY(-4px); }
    .service-card:hover::before { opacity: 1; }
    .service-icon {
      width: 48px; height: 48px; border-radius: 12px;
      background: rgba(124,92,252,0.12);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.4rem; margin-bottom: 20px;
    }
    .service-title {
      font-family: 'Syne', sans-serif;
      font-size: 1.15rem; font-weight: 700;
      margin-bottom: 10px;
    }
    .service-desc { color: var(--muted); font-size: 0.9rem; line-height: 1.65; }

    /* HOW IT WORKS */
    .how-wrap { display: flex; flex-direction: column; gap: 0; }
    .how-step {
      display: grid; grid-template-columns: 56px 1fr;
      gap: 24px; padding: 32px 0;
      border-bottom: 1px solid var(--border);
    }
    .how-step:last-child { border-bottom: none; }
    .step-num {
      font-family: 'Syne', sans-serif;
      font-size: 0.75rem; font-weight: 800;
      color: var(--accent); letter-spacing: 0.08em;
      padding-top: 4px;
    }
    .step-title {
      font-family: 'Syne', sans-serif;
      font-size: 1.2rem; font-weight: 700; margin-bottom: 8px;
    }
    .step-desc { color: var(--muted); font-size: 0.92rem; }

    /* TESTIMONIAL */
    .testi-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
    }
    .testi-card {
      background: var(--card); border: 1px solid var(--border);
      border-radius: 16px; padding: 28px;
    }
    .testi-text { font-size: 0.95rem; line-height: 1.7; margin-bottom: 20px; }
    .testi-author { display: flex; align-items: center; gap: 12px; }
    .testi-avatar {
      width: 40px; height: 40px; border-radius: 50%;
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      display: flex; align-items: center; justify-content: center;
      font-weight: 700; font-size: 0.9rem;
    }
    .testi-name { font-weight: 500; font-size: 0.9rem; }
    .testi-role { font-size: 0.78rem; color: var(--muted); }

    /* CTA */
    .cta-section {
      text-align: center; padding: 100px 24px;
      background: var(--surface);
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
    }
    .cta-section h2 { max-width: 600px; margin: 0 auto 16px; }
    .cta-section p { color: var(--muted); margin-bottom: 40px; }

    /* FOOTER */
    footer {
      text-align: center; padding: 40px 24px;
      color: var(--muted); font-size: 0.82rem;
      border-top: 1px solid var(--border);
    }
    footer strong { color: var(--white); }

    @media (max-width: 768px) {
      nav { padding: 16px 20px; }
      .nav-links { display: none; }
      .stats-bar { margin: 0; gap: 32px; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo">CWC AI</div>
  <ul class="nav-links">
    <li><a href="#services">Services</a></li>
    <li><a href="#how">Process</a></li>
    <li><a href="#results">Results</a></li>
  </ul>
  <button class="nav-cta" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Get a Demo</button>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-badge"><span></span> AI-Powered Business Automation</div>
  <h1>Your business,<br/><em>run by AI.</em></h1>
  <p class="hero-sub">We build custom AI systems that eliminate repetitive work, respond to customers 24/7, and help your business grow — without hiring more staff.</p>
  <div class="hero-actions">
    <button class="btn-primary" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">See It in Action</button>
    <button class="btn-ghost" onclick="document.getElementById('services').scrollIntoView({behavior:'smooth'})">What We Build</button>
  </div>
</div>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-item">
    <div class="stat-num">3×</div>
    <div class="stat-label">Faster customer response</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">60%</div>
    <div class="stat-label">Reduction in manual tasks</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">24/7</div>
    <div class="stat-label">AI works while you sleep</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">14 days</div>
    <div class="stat-label">Average delivery time</div>
  </div>
</div>

<!-- SERVICES -->
<section id="services">
  <div class="section-eye">What we build</div>
  <h2>AI tools built for<br/>real businesses</h2>
  <p class="section-sub">From customer support bots to full workflow automation — we build what your business actually needs.</p>
  <div class="services-grid">
    <div class="service-card">
      <div class="service-icon">🤖</div>
      <div class="service-title">AI Customer Chatbot</div>
      <div class="service-desc">A smart assistant that answers customer questions, books appointments, and handles support — automatically, around the clock.</div>
    </div>
    <div class="service-card">
      <div class="service-icon">⚡</div>
      <div class="service-title">Workflow Automation</div>
      <div class="service-desc">Connect your tools and eliminate repetitive tasks. Orders, emails, reports — all handled without human input.</div>
    </div>
    <div class="service-card">
      <div class="service-icon">📊</div>
      <div class="service-title">AI Sales Assistant</div>
      <div class="service-desc">Follow up with leads, qualify prospects, and book calls automatically. Your sales pipeline, on autopilot.</div>
    </div>
    <div class="service-card">
      <div class="service-icon">✍️</div>
      <div class="service-title">Content Generation</div>
      <div class="service-desc">Social posts, product descriptions, emails — generated in your brand voice, ready to publish.</div>
    </div>
    <div class="service-card">
      <div class="service-icon">📦</div>
      <div class="service-title">Inventory & Logistics AI</div>
      <div class="service-desc">Predict stock needs, automate reorders, and track shipments — all connected to one intelligent dashboard.</div>
    </div>
    <div class="service-card">
      <div class="service-icon">🔗</div>
      <div class="service-title">Custom AI Integration</div>
      <div class="service-desc">Already have software? We plug AI into what you use — no full rebuild needed. Fast, flexible, and built to scale.</div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section id="how" style="background: var(--surface); max-width:100%; padding: 100px 24px;">
  <div style="max-width:1100px; margin:0 auto;">
    <div class="section-eye">Our process</div>
    <h2>From idea to live<br/>in 14 days</h2>
    <p class="section-sub">No lengthy contracts. No confusing tech jargon. Just results.</p>
    <div class="how-wrap">
      <div class="how-step">
        <div class="step-num">01</div>
        <div>
          <div class="step-title">Discovery call</div>
          <div class="step-desc">We learn your business, your biggest bottlenecks, and what an AI solution would actually save you.</div>
        </div>
      </div>
      <div class="how-step">
        <div class="step-num">02</div>
        <div>
          <div class="step-title">Custom proposal</div>
          <div class="step-desc">You get a clear plan: what we build, how long it takes, and exactly what it costs. No surprises.</div>
        </div>
      </div>
      <div class="how-step">
        <div class="step-num">03</div>
        <div>
          <div class="step-title">We build it</div>
          <div class="step-desc">Our team builds and tests your AI system. You see progress at every stage.</div>
        </div>
      </div>
      <div class="how-step">
        <div class="step-num">04</div>
        <div>
          <div class="step-title">You go live</div>
          <div class="step-desc">We deploy, train your team, and stay available for support. Your AI is working from day one.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- RESULTS -->
<section id="results">
  <div class="section-eye">Client results</div>
  <h2>What clients say</h2>
  <p class="section-sub">Real businesses, real outcomes.</p>
  <div class="testi-grid">
    <div class="testi-card">
      <div class="testi-text">"CWC built us an AI chatbot in under two weeks. Our support tickets dropped by 70% and customers get answers instantly — even at 2am."</div>
      <div class="testi-author">
        <div class="testi-avatar">JM</div>
        <div>
          <div class="testi-name">James Mitchell</div>
          <div class="testi-role">CEO, ShopNova</div>
        </div>
      </div>
    </div>
    <div class="testi-card">
      <div class="testi-text">"The workflow automation they set up saves our team 20 hours a week. We reinvested that time into growth. Best decision we made this year."</div>
      <div class="testi-author">
        <div class="testi-avatar">SR</div>
        <div>
          <div class="testi-name">Sofia Reyes</div>
          <div class="testi-role">Operations Lead, Fieldly</div>
        </div>
      </div>
    </div>
    <div class="testi-card">
      <div class="testi-text">"I was skeptical AI could understand our niche. CWC proved me wrong. The sales assistant they built books 3–4 calls a day on its own."</div>
      <div class="testi-author">
        <div class="testi-avatar">AK</div>
        <div>
          <div class="testi-name">Alex Kim</div>
          <div class="testi-role">Founder, GrowthStack</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<div class="cta-section" id="contact">
  <div class="section-eye">Get started</div>
  <h2>Ready to automate<br/>your business?</h2>
  <p>Tell us what you need. We'll show you exactly what AI can do for you — free, no commitment.</p>
  <button class="btn-primary" style="font-size:1rem; padding:16px 40px;"
    onclick="window.open('mailto:hello@cwcai.com','_blank')">
    Book a Free Demo →
  </button>
</div>

<!-- FOOTER -->
<footer>
  <strong>CWC AI</strong> — Central World Club &nbsp;·&nbsp; hello@cwcai.com &nbsp;·&nbsp; © 2026 CWC. All rights reserved.
</footer>

</body>
</html>