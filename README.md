<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Mehdi Nickzamir — Profile</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Mono:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #f5f4f2;
      --surface: #efefed;
      --border: #e0deda;
      --text: #1a1917;
      --muted: #7a7672;
      --orange: #d4622a;
      --orange-light: #f07540;
      --orange-pale: #fce9de;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Syne', sans-serif;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* Grain overlay */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 100;
      opacity: 0.5;
    }

    .page {
      max-width: 860px;
      margin: 0 auto;
      padding: 60px 32px 80px;
    }

    /* ── HEADER ── */
    .header {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      gap: 32px;
      margin-bottom: 56px;
      animation: fadeUp .6s ease both;
    }

    .header-left { flex: 1; }

    .badge {
      display: inline-block;
      background: var(--orange-pale);
      color: var(--orange);
      font-family: 'DM Mono', monospace;
      font-size: 11px;
      letter-spacing: .08em;
      text-transform: uppercase;
      padding: 5px 12px;
      border-radius: 999px;
      margin-bottom: 18px;
      border: 1px solid #f0c8a8;
    }

    h1 {
      font-size: clamp(2.4rem, 5vw, 3.6rem);
      font-weight: 800;
      line-height: 1.05;
      letter-spacing: -.03em;
      margin-bottom: 16px;
    }

    h1 .wave {
      display: inline-block;
      animation: wave 2.2s ease-in-out infinite;
      transform-origin: 70% 70%;
    }

    .tagline {
      font-size: 1.05rem;
      color: var(--muted);
      line-height: 1.6;
      max-width: 400px;
      font-weight: 400;
    }

    /* Avatar blob */
    .avatar-wrap {
      flex-shrink: 0;
      width: 130px;
      height: 130px;
      position: relative;
    }

    .avatar-blob {
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, var(--orange) 0%, var(--orange-light) 100%);
      border-radius: 60% 40% 55% 45% / 45% 55% 40% 60%;
      animation: blobMorph 6s ease-in-out infinite;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3.2rem;
    }

    /* ── MARQUEE STRIP ── */
    .marquee-wrap {
      overflow: hidden;
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      padding: 12px 0;
      margin-bottom: 48px;
      background: var(--surface);
      animation: fadeUp .6s .1s ease both;
    }

    .marquee-track {
      display: flex;
      gap: 0;
      animation: marquee 18s linear infinite;
      white-space: nowrap;
      width: max-content;
    }

    .marquee-item {
      font-family: 'DM Mono', monospace;
      font-size: 12px;
      color: var(--muted);
      letter-spacing: .06em;
      padding: 0 28px;
      text-transform: uppercase;
    }

    .marquee-item span {
      color: var(--orange);
      margin-right: 8px;
    }

    /* ── ABOUT SECTION ── */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
      margin-bottom: 48px;
      animation: fadeUp .6s .2s ease both;
    }

    .about-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 24px;
      transition: transform .2s ease, box-shadow .2s ease;
    }

    .about-card:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 32px rgba(0,0,0,.07);
    }

    .about-card.wide { grid-column: span 2; }

    .card-label {
      font-family: 'DM Mono', monospace;
      font-size: 10px;
      letter-spacing: .1em;
      text-transform: uppercase;
      color: var(--orange);
      margin-bottom: 10px;
    }

    .card-title {
      font-size: 1.3rem;
      font-weight: 700;
      margin-bottom: 8px;
    }

    .card-text {
      font-size: .9rem;
      color: var(--muted);
      line-height: 1.65;
      font-weight: 400;
    }

    /* ── TYPING ANIMATION ── */
    .typing-wrap {
      display: flex;
      align-items: center;
      gap: 10px;
      font-family: 'DM Mono', monospace;
      font-size: .85rem;
      color: var(--muted);
    }

    .typing-text::after {
      content: '|';
      animation: blink .7s step-end infinite;
      color: var(--orange);
    }

    /* ── SKILLS ── */
    .skills-section {
      margin-bottom: 48px;
      animation: fadeUp .6s .3s ease both;
    }

    .section-heading {
      font-size: .75rem;
      font-family: 'DM Mono', monospace;
      letter-spacing: .12em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .section-heading::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    .skills-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }

    .skill-pill {
      background: white;
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 8px 16px;
      font-size: .85rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      gap: 7px;
      transition: all .18s ease;
      cursor: default;
    }

    .skill-pill:hover {
      border-color: var(--orange);
      background: var(--orange-pale);
      color: var(--orange);
      transform: translateY(-2px);
    }

    .skill-pill .dot {
      width: 6px; height: 6px;
      border-radius: 50%;
      background: var(--orange);
      flex-shrink: 0;
    }

    /* ── STATS ROW ── */
    .stats-row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin-bottom: 48px;
      animation: fadeUp .6s .35s ease both;
    }

    .stat-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 20px 24px;
      text-align: center;
    }

    .stat-num {
      font-size: 2rem;
      font-weight: 800;
      color: var(--orange);
      letter-spacing: -.04em;
      line-height: 1;
      margin-bottom: 4px;
    }

    .stat-label {
      font-family: 'DM Mono', monospace;
      font-size: .75rem;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: .07em;
    }

    /* ── CONNECT SECTION ── */
    .connect-section {
      animation: fadeUp .6s .4s ease both;
    }

    .connect-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }

    .connect-card {
      display: flex;
      align-items: center;
      gap: 14px;
      background: white;
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 16px 20px;
      text-decoration: none;
      color: var(--text);
      transition: all .2s ease;
      position: relative;
      overflow: hidden;
    }

    .connect-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: var(--orange-pale);
      transform: scaleX(0);
      transform-origin: left;
      transition: transform .25s ease;
      z-index: 0;
    }

    .connect-card:hover::before { transform: scaleX(1); }
    .connect-card:hover { border-color: var(--orange); }
    .connect-card:hover .connect-arrow { transform: translate(3px, -3px); color: var(--orange); }

    .connect-card > * { position: relative; z-index: 1; }

    .connect-icon {
      width: 40px; height: 40px;
      background: var(--surface);
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.2rem;
      flex-shrink: 0;
      border: 1px solid var(--border);
    }

    .connect-info { flex: 1; }

    .connect-name {
      font-weight: 700;
      font-size: .9rem;
      margin-bottom: 2px;
    }

    .connect-handle {
      font-family: 'DM Mono', monospace;
      font-size: .75rem;
      color: var(--muted);
    }

    .connect-arrow {
      font-size: .85rem;
      color: var(--muted);
      transition: all .2s ease;
    }

    /* ── FOOTER ── */
    .footer {
      margin-top: 56px;
      padding-top: 24px;
      border-top: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-family: 'DM Mono', monospace;
      font-size: .75rem;
      color: var(--muted);
      animation: fadeUp .6s .5s ease both;
    }

    .footer-dot {
      width: 8px; height: 8px;
      border-radius: 50%;
      background: var(--orange);
      animation: pulse 2s ease-in-out infinite;
    }

    /* ── ANIMATED LINES (decorative) ── */
    .deco-lines {
      position: fixed;
      top: 0; right: 0;
      width: 300px; height: 300px;
      pointer-events: none;
      opacity: .35;
      z-index: 0;
    }

    /* ── KEYFRAMES ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes wave {
      0%, 60%, 100% { transform: rotate(0deg); }
      10%, 30% { transform: rotate(18deg); }
      20% { transform: rotate(-8deg); }
    }

    @keyframes blobMorph {
      0%, 100% { border-radius: 60% 40% 55% 45% / 45% 55% 40% 60%; }
      33%  { border-radius: 40% 60% 45% 55% / 55% 45% 60% 40%; }
      66%  { border-radius: 55% 45% 40% 60% / 40% 60% 55% 45%; }
    }

    @keyframes marquee {
      from { transform: translateX(0); }
      to   { transform: translateX(-50%); }
    }

    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0; }
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 1; }
      50% { transform: scale(1.4); opacity: .6; }
    }

    @media (max-width: 600px) {
      .about-grid { grid-template-columns: 1fr; }
      .about-card.wide { grid-column: span 1; }
      .connect-grid { grid-template-columns: 1fr; }
      .stats-row { grid-template-columns: 1fr 1fr; }
      .header { flex-direction: column-reverse; align-items: flex-start; }
    }
  </style>
</head>
<body>

<!-- Decorative SVG -->
<svg class="deco-lines" viewBox="0 0 300 300" fill="none" xmlns="http://www.w3.org/2000/svg">
  <circle cx="250" cy="50" r="120" stroke="#d4622a" stroke-width=".8" opacity=".5"/>
  <circle cx="250" cy="50" r="80" stroke="#d4622a" stroke-width=".6" opacity=".4"/>
  <circle cx="250" cy="50" r="40" stroke="#d4622a" stroke-width=".5" opacity=".3"/>
</svg>

<div class="page">

  <!-- HEADER -->
  <header class="header">
    <div class="header-left">
      <div class="badge">// Open to PhD Opportunities</div>
      <h1>Hi, I'm Mehdi <span class="wave">👋</span></h1>
      <p class="tagline">Data Scientist & Deep Learning enthusiast. Currently diving deep into NLP at Politecnico di Torino.</p>
    </div>
    <div class="avatar-wrap">
      <div class="avatar-blob">🧠</div>
    </div>
  </header>

  <!-- MARQUEE -->
  <div class="marquee-wrap">
    <div class="marquee-track" id="marqueeTrack"></div>
  </div>

  <!-- ABOUT GRID -->
  <div class="about-grid">
    <div class="about-card">
      <div class="card-label">// current focus</div>
      <div class="card-title">Natural Language Processing</div>
      <p class="card-text">Fine-tuning transformers, building RAG pipelines, and exploring how language models reason.</p>
    </div>
    <div class="about-card">
      <div class="card-label">// location</div>
      <div class="card-title">Turin, Italy 🇮🇹</div>
      <p class="card-text">MSc Data Science at Politecnico di Torino — where espresso and gradient descent flow freely.</p>
    </div>
    <div class="about-card wide">
      <div class="card-label">// philosophy</div>
      <div class="card-title">Build. Break. Learn. Repeat.</div>
      <div class="typing-wrap" style="margin-top:8px">
        <span style="color:var(--orange);font-size:.8rem;">❯</span>
        <span class="typing-text" id="typingEl"></span>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div class="stats-row">
    <div class="stat-card">
      <div class="stat-num">26</div>
      <div class="stat-label">Years old</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">∞</div>
      <div class="stat-label">Curiosity level</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">PhD?</div>
      <div class="stat-label">Next chapter</div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="skills-section">
    <div class="section-heading">Skills & Tools</div>
    <div class="skills-grid" id="skillsGrid"></div>
  </div>

  <!-- CONNECT -->
  <div class="connect-section">
    <div class="section-heading">Let's Connect</div>
    <div class="connect-grid" id="connectGrid"></div>
  </div>

  <!-- FOOTER -->
  <footer class="footer">
    <span>Mehdi Nickzamir © 2025</span>
    <div style="display:flex;align-items:center;gap:8px;">
      <div class="footer-dot"></div>
      <span>Available for collaboration</span>
    </div>
  </footer>

</div>

<script>
  // ── Marquee content ──
  const marqueeItems = [
    'PyTorch', 'Transformers', 'NLP', 'Deep Learning',
    'Python', 'LLMs', 'RAG', 'Scikit-learn',
    'Data Science', 'Neural Nets', 'HuggingFace', 'Pandas',
  ];
  const track = document.getElementById('marqueeTrack');
  // duplicate for seamless loop
  [...marqueeItems, ...marqueeItems].forEach(item => {
    const el = document.createElement('span');
    el.className = 'marquee-item';
    el.innerHTML = `<span>◆</span>${item}`;
    track.appendChild(el);
  });

  // ── Skills ──
  const skills = [
    'Python', 'PyTorch', 'HuggingFace 🤗', 'Transformers',
    'NLP', 'LLMs', 'RAG', 'Scikit-learn',
    'Pandas', 'NumPy', 'SQL', 'Git',
  ];
  const grid = document.getElementById('skillsGrid');
  skills.forEach((s, i) => {
    const el = document.createElement('div');
    el.className = 'skill-pill';
    el.innerHTML = `<span class="dot"></span>${s}`;
    el.style.animationDelay = `${i * 0.05}s`;
    grid.appendChild(el);
  });

  // ── Connect cards ──
  const links = [
    { icon: '✉️', name: 'Email', handle: 'Mehdi.nickzamir99@gmail.com', href: 'mailto:Mehdi.nickzamir99@gmail.com' },
    { icon: '💼', name: 'LinkedIn', handle: 'mehdi-nickzamir', href: 'https://www.linkedin.com/in/mehdi-nickzamir/' },
    { icon: '📝', name: 'Medium', handle: '@MehdiNick', href: 'https://medium.com/@MehdiNick' },
    { icon: '🎥', name: 'YouTube', handle: 'MehdiExplores', href: 'https://www.youtube.com/@MehdiExplores' },
  ];
  const cGrid = document.getElementById('connectGrid');
  links.forEach(l => {
    const a = document.createElement('a');
    a.className = 'connect-card';
    a.href = l.href;
    a.target = '_blank';
    a.rel = 'noopener';
    a.innerHTML = `
      <div class="connect-icon">${l.icon}</div>
      <div class="connect-info">
        <div class="connect-name">${l.name}</div>
        <div class="connect-handle">${l.handle}</div>
      </div>
      <span class="connect-arrow">↗</span>
    `;
    cGrid.appendChild(a);
  });

  // ── Typing animation ──
  const phrases = [
    'Even if it breaks, you learn why.',
    'Every field adds its own spice.',
    'Currently exploring NLP & LLMs.',
    'Open to PhD adventures worldwide.',
  ];
  const el = document.getElementById('typingEl');
  let pi = 0, ci = 0, deleting = false;
  function type() {
    const phrase = phrases[pi];
    if (!deleting) {
      el.textContent = phrase.slice(0, ++ci);
      if (ci === phrase.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      el.textContent = phrase.slice(0, --ci);
      if (ci === 0) { deleting = false; pi = (pi + 1) % phrases.length; }
    }
    setTimeout(type, deleting ? 40 : 70);
  }
  type();
</script>
</body>
</html>
