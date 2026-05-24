# waleed-portfolio
[index (2).html](https://github.com/user-attachments/files/28194461/index.2.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Waleed — Frontend & Flutter Dev</title>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&family=Playfair+Display:ital,wght@0,700;1,400&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #f5f2ee;
      --ink: #1a1814;
      --muted: #7a7570;
      --line: #dedad5;
      --accent: #c9602a;
      --accent-light: #f0e6de;
      --white: #fdfcfb;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--ink);
      font-family: 'Outfit', sans-serif;
      font-weight: 400;
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      padding: 1.25rem 4rem;
      display: flex; justify-content: space-between; align-items: center;
      background: var(--bg);
      border-bottom: 1px solid var(--line);
    }
    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-style: italic;
      font-size: 1.3rem;
      color: var(--ink);
      letter-spacing: 0.01em;
    }
    .nav-links { display: flex; gap: 2.5rem; list-style: none; }
    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.82rem;
      font-weight: 500;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--accent); }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      padding: 10rem 4rem 5rem;
      display: grid;
      grid-template-columns: 1.1fr 0.9fr;
      gap: 4rem;
      align-items: center;
      border-bottom: 1px solid var(--line);
    }

    .hero-eyebrow {
      display: flex; align-items: center; gap: 0.75rem;
      margin-bottom: 2rem;
      font-size: 0.78rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--muted);
    }
    .hero-eyebrow::before {
      content: '';
      display: inline-block;
      width: 32px; height: 1px;
      background: var(--accent);
    }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(3.2rem, 5.5vw, 5.2rem);
      font-weight: 700;
      line-height: 1.05;
      letter-spacing: -0.02em;
      color: var(--ink);
      margin-bottom: 1.75rem;
    }
    h1 em {
      font-style: italic;
      color: var(--accent);
    }

    .hero-desc {
      font-size: 1rem;
      color: var(--muted);
      line-height: 1.75;
      max-width: 460px;
      margin-bottom: 2.5rem;
    }

    .hero-cta { display: flex; gap: 1rem; align-items: center; }

    .btn {
      padding: 0.78rem 1.8rem;
      font-family: 'Outfit', sans-serif;
      font-size: 0.82rem;
      font-weight: 600;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      text-decoration: none;
      border-radius: 2px;
      transition: all 0.2s ease;
      display: inline-block;
    }
    .btn-solid {
      background: var(--ink);
      color: var(--white);
      border: 1px solid var(--ink);
    }
    .btn-solid:hover { background: var(--accent); border-color: var(--accent); }
    .btn-ghost {
      background: transparent;
      color: var(--ink);
      border: 1px solid var(--line);
    }
    .btn-ghost:hover { border-color: var(--ink); }

    /* Hero right — stat cards */
    .hero-right {
      display: flex;
      flex-direction: column;
      gap: 1px;
      background: var(--line);
      border: 1px solid var(--line);
    }
    .stat-card {
      background: var(--white);
      padding: 1.75rem 2rem;
      transition: background 0.2s;
    }
    .stat-card:hover { background: var(--accent-light); }
    .stat-num {
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem;
      font-weight: 700;
      color: var(--ink);
      line-height: 1;
      margin-bottom: 0.3rem;
    }
    .stat-label { font-size: 0.8rem; color: var(--muted); font-weight: 500; letter-spacing: 0.04em; }

    /* ── SECTIONS ── */
    .section {
      padding: 6rem 4rem;
      border-bottom: 1px solid var(--line);
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      margin-bottom: 3.5rem;
      padding-bottom: 1.5rem;
      border-bottom: 1px solid var(--line);
    }
    .section-num {
      font-size: 0.72rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--muted);
    }
    h2 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.8rem, 3vw, 2.6rem);
      font-weight: 700;
      letter-spacing: -0.02em;
      color: var(--ink);
    }

    /* ── SKILLS ── */
    .skills-list {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1px;
      background: var(--line);
      border: 1px solid var(--line);
    }
    .skill-row {
      background: var(--white);
      padding: 1.5rem 1.75rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: background 0.2s;
    }
    .skill-row:hover { background: var(--accent-light); }
    .skill-name-text {
      font-size: 0.9rem;
      font-weight: 600;
      color: var(--ink);
    }
    .skill-sub { font-size: 0.75rem; color: var(--muted); margin-top: 0.15rem; }
    .skill-pct {
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem;
      font-weight: 700;
      color: var(--accent);
    }

    /* ── PROJECTS ── */
    .projects-list { display: flex; flex-direction: column; gap: 1px; background: var(--line); border: 1px solid var(--line); }
    .project-row {
      background: var(--white);
      padding: 2rem 2.5rem;
      display: grid;
      grid-template-columns: 2rem 1fr auto;
      gap: 2rem;
      align-items: start;
      transition: background 0.2s;
      cursor: default;
    }
    .project-row:hover { background: var(--accent-light); }
    .project-index {
      font-family: 'Playfair Display', serif;
      font-style: italic;
      font-size: 0.85rem;
      color: var(--muted);
      padding-top: 0.2rem;
    }
    .project-title-text {
      font-size: 1rem;
      font-weight: 600;
      color: var(--ink);
      margin-bottom: 0.4rem;
    }
    .project-desc-text { font-size: 0.85rem; color: var(--muted); line-height: 1.6; }
    .project-tags-wrap { display: flex; gap: 0.4rem; flex-wrap: wrap; padding-top: 0.2rem; }
    .tag {
      padding: 0.2rem 0.65rem;
      background: var(--bg);
      border: 1px solid var(--line);
      border-radius: 2px;
      font-size: 0.68rem;
      font-weight: 500;
      letter-spacing: 0.04em;
      color: var(--muted);
      white-space: nowrap;
    }

    /* ── CONTACT ── */
    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: start;
    }
    .contact-tagline {
      font-family: 'Playfair Display', serif;
      font-size: 1.6rem;
      font-style: italic;
      color: var(--ink);
      line-height: 1.4;
      margin-bottom: 1.25rem;
    }
    .contact-body { font-size: 0.9rem; color: var(--muted); line-height: 1.75; }

    .contact-items { display: flex; flex-direction: column; gap: 1px; background: var(--line); border: 1px solid var(--line); }
    .contact-item {
      background: var(--white);
      padding: 1.2rem 1.5rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      text-decoration: none;
      transition: background 0.2s;
    }
    .contact-item:hover { background: var(--accent-light); }
    .contact-item-label { font-size: 0.72rem; text-transform: uppercase; letter-spacing: 0.1em; color: var(--muted); font-weight: 500; }
    .contact-item-value { font-size: 0.88rem; color: var(--ink); font-weight: 500; }
    .contact-arrow { color: var(--accent); font-size: 1rem; }

    /* ── FOOTER ── */
    footer {
      padding: 1.5rem 4rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.75rem;
      color: var(--muted);
    }

    /* ── REVEAL ── */
    .reveal {
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 0.55s ease, transform 0.55s ease;
    }
    .reveal.visible { opacity: 1; transform: none; }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      .hero { grid-template-columns: 1fr; padding: 7rem 1.5rem 3rem; gap: 3rem; }
      .section { padding: 4rem 1.5rem; }
      .skills-list { grid-template-columns: 1fr; }
      .contact-grid { grid-template-columns: 1fr; gap: 2.5rem; }
      footer { padding: 1.25rem 1.5rem; flex-direction: column; gap: 0.4rem; text-align: center; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
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
    <div class="hero-content">
      <div class="hero-eyebrow">Frontend &amp; Flutter Developer</div>
      <h1>Building interfaces<br>that <em>feel right.</em></h1>
      <p class="hero-desc">
        Hi, I'm <strong>Waleed</strong> — I craft clean, responsive web experiences
        and cross-platform Flutter apps with a sharp eye for detail.
      </p>
      <div class="hero-cta">
        <a href="#projects" class="btn btn-solid">View Projects</a>
        <a href="#contact" class="btn btn-ghost">Get in Touch</a>
      </div>
    </div>

    <div class="hero-right">
      <div class="stat-card">
        <div class="stat-num">2+</div>
        <div class="stat-label">Years of Experience</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">10+</div>
        <div class="stat-label">Projects Completed</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">Flutter</div>
        <div class="stat-label">Primary Specialization</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">Open</div>
        <div class="stat-label">Available for Work</div>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section" id="skills">
    <div class="section-header reveal">
      <h2>Skills</h2>
      <span class="section-num">01 / 03</span>
    </div>
    <div class="skills-list">
      <div class="skill-row reveal">
        <div>
          <div class="skill-name-text">Flutter</div>
          <div class="skill-sub">Cross-platform mobile apps</div>
        </div>
        <div class="skill-pct">90%</div>
      </div>
      <div class="skill-row reveal">
        <div>
          <div class="skill-name-text">Dart</div>
          <div class="skill-sub">State management, logic</div>
        </div>
        <div class="skill-pct">85%</div>
      </div>
      <div class="skill-row reveal">
        <div>
          <div class="skill-name-text">HTML / CSS</div>
          <div class="skill-sub">Responsive & semantic</div>
        </div>
        <div class="skill-pct">90%</div>
      </div>
      <div class="skill-row reveal">
        <div>
          <div class="skill-name-text">JavaScript</div>
          <div class="skill-sub">ES6+, DOM, APIs</div>
        </div>
        <div class="skill-pct">80%</div>
      </div>
      <div class="skill-row reveal">
        <div>
          <div class="skill-name-text">React</div>
          <div class="skill-sub">Components & hooks</div>
        </div>
        <div class="skill-pct">75%</div>
      </div>
      <div class="skill-row reveal">
        <div>
          <div class="skill-name-text">UI / UX</div>
          <div class="skill-sub">Figma, prototyping</div>
        </div>
        <div class="skill-pct">70%</div>
      </div>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section" id="projects">
    <div class="section-header reveal">
      <h2>Projects</h2>
      <span class="section-num">02 / 03</span>
    </div>
    <div class="projects-list">
      <div class="project-row reveal">
        <div class="project-index">01</div>
        <div>
          <div class="project-title-text">E-Commerce App</div>
          <div class="project-desc-text">Full Flutter mobile app with product listings, cart, Firebase auth, and smooth page transitions. Deployed on Android & iOS.</div>
        </div>
        <div class="project-tags-wrap">
          <span class="tag">Flutter</span>
          <span class="tag">Firebase</span>
          <span class="tag">Dart</span>
        </div>
      </div>
      <div class="project-row reveal">
        <div class="project-index">02</div>
        <div>
          <div class="project-title-text">Portfolio Website</div>
          <div class="project-desc-text">Personal portfolio with clean typography, scroll animations, and fully responsive layout. Built with pure HTML, CSS, and JS.</div>
        </div>
        <div class="project-tags-wrap">
          <span class="tag">HTML</span>
          <span class="tag">CSS</span>
          <span class="tag">JS</span>
        </div>
      </div>
      <div class="project-row reveal">
        <div class="project-index">03</div>
        <div>
          <div class="project-title-text">Task Manager App</div>
          <div class="project-desc-text">Flutter app with local Hive DB storage, priority tags, dark mode, and reminder notifications. Clean minimal UI.</div>
        </div>
        <div class="project-tags-wrap">
          <span class="tag">Flutter</span>
          <span class="tag">Hive</span>
          <span class="tag">Provider</span>
        </div>
      </div>
    </div>
  </div>

  <!-- CONTACT -->
  <div class="section" id="contact">
    <div class="section-header reveal">
      <h2>Contact</h2>
      <span class="section-num">03 / 03</span>
    </div>
    <div class="contact-grid">
      <div class="reveal">
        <p class="contact-tagline">"Let's build something worth using."</p>
        <p class="contact-body">
          Open to freelance projects, full-time roles, and collaborations.
          Whether it's a Flutter app or a polished website — reach out and I'll
          reply within 24 hours.
        </p>
      </div>
      <div class="contact-items reveal">
        <a href="mailto:waleedyounus815@gmail.com" class="contact-item">
          <div>
            <div class="contact-item-label">Email</div>
            <div class="contact-item-value">waleedyounus815@gmail.com</div>
          </div>
          <span class="contact-arrow">→</span>
        </a>
        <a href="https://github.com/waleedyounus815" target="_blank" class="contact-item">
          <div>
            <div class="contact-item-label">GitHub</div>
            <div class="contact-item-value">github.com/waleedyounus815</div>
          </div>
          <span class="contact-arrow">→</span>
        </a>
        <a href="https://linkedin.com/in/waleed" target="_blank" class="contact-item">
          <div>
            <div class="contact-item-label">LinkedIn</div>
            <div class="contact-item-value">linkedin.com/in/waleed</div>
          </div>
          <span class="contact-arrow">→</span>
        </a>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <footer>
    <span>© 2025 Waleed</span>
    <span>Frontend &amp; Flutter Developer</span>
  </footer>

  <script>
    const observer = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) e.target.classList.add('visible');
      });
    }, { threshold: 0.12 });
    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
  </script>

</body>
</html>
