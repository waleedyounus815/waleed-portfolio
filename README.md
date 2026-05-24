<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Waleed — Frontend & Flutter Dev</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Fraunces:ital,wght@0,700;1,400;1,700&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #0d0d0d;
      --surface: #161616;
      --card: #1c1c1c;
      --border: #2a2a2a;
      --accent: #e8ff47;
      --accent2: #47c8ff;
      --text: #f0f0f0;
      --muted: #666;
      --muted2: #444;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Inter', sans-serif;
      -webkit-font-smoothing: antialiased;
      overflow-x: hidden;
    }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      padding: 1.1rem 3rem;
      display: flex; justify-content: space-between; align-items: center;
      background: rgba(13,13,13,0.92);
      backdrop-filter: blur(16px);
      border-bottom: 1px solid var(--border);
    }
    .nav-logo {
      font-family: 'Fraunces', serif;
      font-style: italic;
      font-size: 1.4rem;
      color: var(--accent);
      letter-spacing: -0.01em;
    }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.8rem;
      font-weight: 500;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--accent); }

    /* HERO */
    .hero {
      min-height: 100vh;
      padding: 9rem 3rem 5rem;
      display: grid;
      grid-template-columns: 1fr 380px;
      gap: 3rem;
      align-items: center;
      max-width: 1200px;
      margin: 0 auto;
    }

    .hero-tag {
      display: inline-flex; align-items: center; gap: 0.5rem;
      padding: 0.35rem 0.85rem;
      background: rgba(232,255,71,0.08);
      border: 1px solid rgba(232,255,71,0.2);
      border-radius: 100px;
      font-size: 0.72rem;
      font-weight: 600;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 2rem;
    }
    .hero-tag::before {
      content: '';
      width: 6px; height: 6px;
      background: var(--accent);
      border-radius: 50%;
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.4; transform: scale(0.8); }
    }

    h1 {
      font-family: 'Fraunces', serif;
      font-size: clamp(3rem, 5.5vw, 5rem);
      font-weight: 700;
      line-height: 1.0;
      letter-spacing: -0.03em;
      color: var(--text);
      margin-bottom: 1.5rem;
    }
    h1 span { color: var(--accent); font-style: italic; }

    .hero-desc {
      font-size: 0.95rem;
      color: var(--muted);
      line-height: 1.8;
      max-width: 480px;
      margin-bottom: 2.5rem;
      font-weight: 300;
    }
    .hero-desc strong { color: var(--text); font-weight: 500; }

    .hero-cta { display: flex; gap: 0.875rem; }
    .btn {
      padding: 0.75rem 1.6rem;
      font-family: 'Inter', sans-serif;
      font-size: 0.8rem;
      font-weight: 600;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      text-decoration: none;
      border-radius: 6px;
      transition: all 0.2s;
      display: inline-block;
    }
    .btn-solid { background: var(--accent); color: #000; border: 1px solid var(--accent); }
    .btn-solid:hover { background: #d4eb00; transform: translateY(-2px); }
    .btn-ghost { background: transparent; color: var(--text); border: 1px solid var(--border); }
    .btn-ghost:hover { border-color: var(--muted); transform: translateY(-2px); }

    /* Hero right panel */
    .hero-panel {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px;
      overflow: hidden;
    }
    .panel-item {
      padding: 1.4rem 1.75rem;
      border-bottom: 1px solid var(--border);
      transition: background 0.2s;
    }
    .panel-item:last-child { border-bottom: none; }
    .panel-item:hover { background: #222; }
    .panel-num {
      font-family: 'Fraunces', serif;
      font-size: 2rem;
      font-weight: 700;
      color: var(--accent);
      line-height: 1;
      margin-bottom: 0.2rem;
    }
    .panel-label { font-size: 0.75rem; color: var(--muted); font-weight: 400; letter-spacing: 0.04em; }

    /* SECTIONS */
    .section {
      padding: 5rem 3rem;
      max-width: 1200px;
      margin: 0 auto;
      border-top: 1px solid var(--border);
    }

    .sec-header {
      display: flex; justify-content: space-between; align-items: baseline;
      margin-bottom: 2.5rem;
    }
    h2 {
      font-family: 'Fraunces', serif;
      font-size: clamp(1.8rem, 3vw, 2.4rem);
      font-weight: 700;
      letter-spacing: -0.02em;
      color: var(--text);
    }
    .sec-num { font-size: 0.7rem; color: var(--muted2); letter-spacing: 0.12em; text-transform: uppercase; }

    /* SKILLS */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 1px;
      background: var(--border);
      border: 1px solid var(--border);
      border-radius: 10px;
      overflow: hidden;
    }
    .skill-card {
      background: var(--card);
      padding: 1.5rem;
      transition: background 0.2s;
    }
    .skill-card:hover { background: #222; }
    .skill-top { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 0.8rem; }
    .skill-name { font-size: 0.9rem; font-weight: 600; color: var(--text); }
    .skill-sub { font-size: 0.72rem; color: var(--muted); margin-top: 0.2rem; }
    .skill-pct { font-family: 'Fraunces', serif; font-size: 1.3rem; font-weight: 700; color: var(--accent); }
    .skill-bar { height: 2px; background: var(--border); border-radius: 1px; overflow: hidden; }
    .skill-fill {
      height: 100%;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      border-radius: 1px;
      transform: scaleX(0); transform-origin: left;
      transition: transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
    }
    .skill-card.vis .skill-fill { transform: scaleX(1); }

    /* PROJECTS */
    .projects-grid { display: flex; flex-direction: column; gap: 1px; background: var(--border); border: 1px solid var(--border); border-radius: 10px; overflow: hidden; }
    .project-card {
      background: var(--card);
      padding: 1.75rem 2rem;
      display: grid;
      grid-template-columns: auto 1fr auto;
      gap: 1.5rem;
      align-items: start;
      transition: background 0.2s;
    }
    .project-card:hover { background: #1f1f1f; }
    .p-num { font-family: 'Fraunces', serif; font-style: italic; font-size: 0.8rem; color: var(--muted2); padding-top: 0.15rem; }
    .p-title { font-size: 0.95rem; font-weight: 600; color: var(--text); margin-bottom: 0.4rem; }
    .p-desc { font-size: 0.82rem; color: var(--muted); line-height: 1.65; }
    .p-tags { display: flex; gap: 0.4rem; flex-wrap: wrap; }
    .tag {
      padding: 0.22rem 0.65rem;
      background: rgba(232,255,71,0.07);
      border: 1px solid rgba(232,255,71,0.15);
      border-radius: 4px;
      font-size: 0.65rem;
      font-weight: 500;
      color: var(--accent);
      letter-spacing: 0.04em;
      white-space: nowrap;
    }

    /* CONTACT */
    .contact-wrap { display: grid; grid-template-columns: 1fr 1fr; gap: 3rem; align-items: start; }
    .contact-heading {
      font-family: 'Fraunces', serif;
      font-size: 1.5rem;
      font-style: italic;
      color: var(--text);
      line-height: 1.4;
      margin-bottom: 1rem;
    }
    .contact-body { font-size: 0.88rem; color: var(--muted); line-height: 1.8; font-weight: 300; }

    .contact-list { display: flex; flex-direction: column; gap: 1px; background: var(--border); border: 1px solid var(--border); border-radius: 10px; overflow: hidden; }
    .contact-row {
      background: var(--card);
      padding: 1.1rem 1.4rem;
      display: flex; justify-content: space-between; align-items: center;
      text-decoration: none;
      transition: background 0.2s;
    }
    .contact-row:hover { background: #222; }
    .c-label { font-size: 0.68rem; text-transform: uppercase; letter-spacing: 0.1em; color: var(--muted2); font-weight: 500; margin-bottom: 0.2rem; }
    .c-val { font-size: 0.85rem; color: var(--text); font-weight: 500; }
    .c-arrow { color: var(--accent); font-size: 1rem; }

    /* FOOTER */
    footer {
      border-top: 1px solid var(--border);
      padding: 1.5rem 3rem;
      display: flex; justify-content: space-between; align-items: center;
      font-size: 0.72rem; color: var(--muted2);
      max-width: 1200px; margin: 0 auto;
    }
    footer span:last-child { color: var(--accent); }

    /* REVEAL */
    .reveal { opacity: 0; transform: translateY(18px); transition: opacity 0.5s ease, transform 0.5s ease; }
    .reveal.vis { opacity: 1; transform: none; }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      nav { padding: 1rem 1.25rem; }
      .nav-links { display: none; }
      .hero { grid-template-columns: 1fr; padding: 7rem 1.25rem 3rem; }
      .section { padding: 3.5rem 1.25rem; }
      .skills-grid { grid-template-columns: 1fr 1fr; }
      .contact-wrap { grid-template-columns: 1fr; }
      footer { flex-direction: column; gap: 0.4rem; text-align: center; padding: 1.25rem; }
      .project-card { grid-template-columns: auto 1fr; }
      .p-tags { display: none; }
    }
  </style>
</head>
<body>

  <nav>
    <div class="nav-logo">Waleed</div>
    <ul class="nav-links">
      <li><a href="#skills">Skills</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <div class="hero">
    <div>
      <div class="hero-tag">Available for work</div>
      <h1>Frontend &<br><span>Flutter</span><br>Developer</h1>
      <p class="hero-desc">
        Hi, I'm <strong>Waleed</strong> — I build clean, fast web interfaces
        and cross-platform Flutter applications, with live deployments on the
        <strong>Google Play Store</strong>. Sharp eye for detail, smooth delivery.
      </p>
      <div class="hero-cta">
        <a href="#projects" class="btn btn-solid">View Projects</a>
        <a href="#contact" class="btn btn-ghost">Contact Me</a>
      </div>
    </div>

    <div class="hero-panel">
      <div class="panel-item">
        <div class="panel-num">2+</div>
        <div class="panel-label">Years Experience</div>
      </div>
      <div class="panel-item">
        <div class="panel-num">4</div>
        <div class="panel-label">Projects Completed</div>
      </div>
      <div class="panel-item">
        <div class="panel-num">Flutter</div>
        <div class="panel-label">Primary Stack</div>
      </div>
      <div class="panel-item">
        <div class="panel-num" style="font-size:1.1rem;padding-top:0.3rem;">Open to Work</div>
        <div class="panel-label">Freelance & Full-time</div>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section" id="skills">
    <div class="sec-header reveal">
      <h2>Skills</h2>
      <span class="sec-num">01 / 03</span>
    </div>
    <div class="skills-grid">
      <div class="skill-card reveal">
        <div class="skill-top">
          <div><div class="skill-name">Flutter</div><div class="skill-sub">Cross-platform apps</div></div>
          <div class="skill-pct">90%</div>
        </div>
        <div class="skill-bar"><div class="skill-fill" style="width:90%"></div></div>
      </div>
      <div class="skill-card reveal">
        <div class="skill-top">
          <div><div class="skill-name">Dart</div><div class="skill-sub">State & logic</div></div>
          <div class="skill-pct">85%</div>
        </div>
        <div class="skill-bar"><div class="skill-fill" style="width:85%"></div></div>
      </div>

    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section" id="projects">
    <div class="sec-header reveal">
      <h2>Projects</h2>
      <span class="sec-num">02 / 03</span>
    </div>
    <div class="projects-grid">
      <div class="project-card reveal">
        <div class="p-num">01</div>
        <div>
          <div class="p-title">E-Commerce App</div>
          <div class="p-desc">Full Flutter mobile app — product listings, cart, Firebase auth, smooth transitions. Live on Android & iOS.</div>
        </div>
        <div class="p-tags">
          <span class="tag">Flutter</span>
          <span class="tag">Firebase</span>
          <span class="tag">Dart</span>
        </div>
      </div>
      <div class="project-card reveal">
        <div class="p-num">02</div>
        <div>
          <div class="p-title">Portfolio Website</div>
          <div class="p-desc">Personal portfolio with scroll animations, dark theme, and fully responsive layout. Pure HTML, CSS & JS.</div>
        </div>
        <div class="p-tags">
          <span class="tag">HTML</span>
          <span class="tag">CSS</span>
          <span class="tag">JavaScript</span>
        </div>
      </div>
      <div class="project-card reveal">
        <div class="p-num">03</div>
        <div>
          <div class="p-title">Task Manager App</div>
          <div class="p-desc">Flutter app with Hive local storage, priority tags, reminders, and dark mode. Minimal clean UI.</div>
        </div>
        <div class="p-tags">
          <span class="tag">Flutter</span>
          <span class="tag">Hive DB</span>
          <span class="tag">Provider</span>
        </div>
      </div>
    </div>
  </div>

  <!-- CONTACT -->
  <div class="section" id="contact">
    <div class="sec-header reveal">
      <h2>Contact</h2>
      <span class="sec-num">03 / 03</span>
    </div>
    <div class="contact-wrap">
      <div class="reveal">
        <p class="contact-heading">"Let's build something worth using."</p>
        <p class="contact-body">Open to freelance projects, full-time roles, and collaborations. Flutter app or a sleek website — reach out and I'll reply within 24 hours.</p>
      </div>
      <div class="contact-list reveal">
        <a href="mailto:waleedyounus815@gmail.com" class="contact-row">
          <div>
            <div class="c-label">Email</div>
            <div class="c-val">waleedyounus815@gmail.com</div>
          </div>
          <span class="c-arrow">→</span>
        </a>
        <a href="https://github.com/waleedyounus815" target="_blank" class="contact-row">
          <div>
            <div class="c-label">GitHub</div>
            <div class="c-val">github.com/waleedyounus815</div>
          </div>
          <span class="c-arrow">→</span>
        </a>
        <a href="https://linkedin.com/in/waleed" target="_blank" class="contact-row">
          <div>
            <div class="c-label">LinkedIn</div>
            <div class="c-val">linkedin.com/in/waleed</div>
          </div>
          <span class="c-arrow">→</span>
        </a>
      </div>
    </div>
  </div>

  <footer>
    <span>© 2025 Waleed Younus</span>
    <span>Frontend & Flutter Developer</span>
  </footer>

  <script>
    const io = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('vis');
        }
      });
    }, { threshold: 0.1 });
    document.querySelectorAll('.reveal, .skill-card').forEach(el => io.observe(el));
  </script>

</body>
</html>
