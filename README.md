# portfolio.
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Deja Meilino — 3D Designer & Artist</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Mono:wght@300;400&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #050505;
    --dark: #0d0d0d;
    --card: #111111;
    --border: rgba(255,255,255,0.07);
    --white: #f5f2ee;
    --muted: rgba(245,242,238,0.45);
    --accent: #c8a97e;
    --accent2: #e8d5b7;
    --red: #c0392b;
  }
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'Syne', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed; width: 8px; height: 8px;
    background: var(--accent); border-radius: 50%;
    pointer-events: none; z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s, width 0.3s, height 0.3s, opacity 0.3s;
  }
  .cursor-ring {
    position: fixed; width: 36px; height: 36px;
    border: 1px solid rgba(200,169,126,0.4); border-radius: 50%;
    pointer-events: none; z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform 0.15s ease, width 0.3s, height 0.3s;
  }
  a:hover ~ .cursor, button:hover ~ .cursor { width: 20px; height: 20px; }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; justify-content: space-between; align-items: center;
    padding: 1.5rem 3rem;
    background: linear-gradient(to bottom, rgba(5,5,5,0.95) 0%, transparent 100%);
    backdrop-filter: blur(0px);
  }
  .nav-logo {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.2rem; font-weight: 300; letter-spacing: 0.15em;
    color: var(--white); text-decoration: none;
  }
  .nav-links { display: flex; gap: 2.5rem; list-style: none; }
  .nav-links a {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem; letter-spacing: 0.12em;
    color: var(--muted); text-decoration: none; text-transform: uppercase;
    transition: color 0.3s;
  }
  .nav-links a:hover { color: var(--accent); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; justify-content: flex-end;
    padding: 0 3rem 5rem;
    position: relative;
    overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 60% 60% at 75% 40%, rgba(192,57,43,0.12) 0%, transparent 60%),
      radial-gradient(ellipse 40% 50% at 20% 70%, rgba(200,169,126,0.06) 0%, transparent 60%),
      var(--black);
  }
  .hero-grid {
    position: absolute; inset: 0; opacity: 0.025;
    background-image:
      linear-gradient(var(--white) 1px, transparent 1px),
      linear-gradient(90deg, var(--white) 1px, transparent 1px);
    background-size: 80px 80px;
  }
  .hero-year {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem; letter-spacing: 0.2em; color: var(--accent);
    text-transform: uppercase; margin-bottom: 2rem;
    position: relative;
    animation: fadeUp 1s ease 0.2s both;
  }
  .hero-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(5rem, 12vw, 11rem);
    font-weight: 300; line-height: 0.9;
    letter-spacing: -0.02em;
    position: relative;
    animation: fadeUp 1s ease 0.4s both;
  }
  .hero-title em {
    font-style: italic; color: var(--accent);
  }
  .hero-subtitle {
    margin-top: 2rem;
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem; letter-spacing: 0.15em;
    color: var(--muted); text-transform: uppercase;
    display: flex; align-items: center; gap: 1.5rem;
    position: relative;
    animation: fadeUp 1s ease 0.6s both;
  }
  .hero-subtitle::before {
    content: ''; display: block; width: 40px; height: 1px;
    background: var(--accent);
  }
  .hero-scroll {
    position: absolute; right: 3rem; bottom: 5rem;
    display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
    animation: fadeUp 1s ease 0.8s both;
  }
  .hero-scroll span {
    font-family: 'DM Mono', monospace; font-size: 0.6rem;
    letter-spacing: 0.15em; color: var(--muted);
    writing-mode: vertical-rl; text-transform: uppercase;
  }
  .scroll-line {
    width: 1px; height: 60px; background: var(--accent); opacity: 0.5;
    animation: scrollAnim 2s ease-in-out infinite;
  }
  @keyframes scrollAnim {
    0%,100% { transform: scaleY(1); opacity: 0.5; }
    50% { transform: scaleY(0.5); opacity: 1; }
  }

  /* ABOUT */
  .about {
    padding: 8rem 3rem;
    display: grid; grid-template-columns: 1fr 1fr; gap: 6rem;
    align-items: center; max-width: 1400px; margin: 0 auto;
  }
  .about-label {
    font-family: 'DM Mono', monospace; font-size: 0.65rem;
    letter-spacing: 0.2em; color: var(--accent); text-transform: uppercase;
    margin-bottom: 2rem; display: flex; align-items: center; gap: 1rem;
  }
  .about-label::before {
    content: '01'; color: var(--muted); font-size: 0.6rem;
  }
  .about-heading {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(2.5rem, 4vw, 3.5rem);
    font-weight: 300; line-height: 1.2;
    margin-bottom: 2rem;
  }
  .about-heading em { font-style: italic; color: var(--accent); }
  .about-body {
    font-size: 0.9rem; line-height: 1.9;
    color: var(--muted); margin-bottom: 2rem;
  }
  .about-photo {
    position: relative; aspect-ratio: 3/4; max-height: 580px;
    overflow: hidden;
  }
  .about-photo-frame {
    position: absolute; inset: 0;
    background: linear-gradient(135deg, var(--card) 0%, #1a1410 100%);
    border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
  }
  .photo-placeholder {
    text-align: center;
  }
  .photo-placeholder .initials {
    font-family: 'Cormorant Garamond', serif;
    font-size: 5rem; font-weight: 300; color: var(--accent);
    opacity: 0.4; display: block;
  }
  .photo-placeholder p {
    font-family: 'DM Mono', monospace; font-size: 0.65rem;
    color: var(--muted); letter-spacing: 0.1em; margin-top: 1rem;
  }
  .about-photo::after {
    content: ''; position: absolute;
    bottom: -1px; right: -1px; width: 60%; height: 60%;
    border-right: 1px solid var(--accent); border-bottom: 1px solid var(--accent);
    opacity: 0.3;
  }
  .about-contacts { display: flex; flex-direction: column; gap: 0.6rem; }
  .contact-row {
    display: flex; align-items: center; gap: 1rem;
    font-family: 'DM Mono', monospace; font-size: 0.72rem;
    color: var(--muted);
  }
  .contact-row .label { color: var(--accent); min-width: 60px; }
  .contact-row a { color: var(--muted); text-decoration: none; transition: color 0.3s; }
  .contact-row a:hover { color: var(--white); }

  /* SKILLS */
  .skills-section {
    padding: 4rem 3rem 8rem;
    border-top: 1px solid var(--border);
    max-width: 1400px; margin: 0 auto;
  }
  .skills-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1px; background: var(--border); margin-top: 4rem; }
  .skill-card {
    background: var(--black); padding: 2.5rem 2rem;
    transition: background 0.3s;
  }
  .skill-card:hover { background: var(--card); }
  .skill-num {
    font-family: 'DM Mono', monospace; font-size: 0.6rem;
    color: var(--accent); letter-spacing: 0.15em; margin-bottom: 1.2rem;
  }
  .skill-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.4rem; font-weight: 400; margin-bottom: 0.8rem;
  }
  .skill-desc { font-size: 0.8rem; color: var(--muted); line-height: 1.7; }

  /* PROJECTS */
  .projects-section {
    padding: 6rem 3rem;
    max-width: 1400px; margin: 0 auto;
  }
  .section-header {
    display: flex; justify-content: space-between; align-items: flex-end;
    margin-bottom: 4rem;
  }
  .section-label {
    font-family: 'DM Mono', monospace; font-size: 0.65rem;
    letter-spacing: 0.2em; color: var(--accent); text-transform: uppercase;
    margin-bottom: 0.8rem;
  }
  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(2rem, 4vw, 3rem); font-weight: 300;
  }
  .section-title em { font-style: italic; color: var(--accent); }
  .projects-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 2px; background: var(--border); }
  .project-card {
    background: var(--card); padding: 3rem 2.5rem;
    position: relative; overflow: hidden;
    transition: background 0.4s;
    cursor: default;
  }
  .project-card::before {
    content: ''; position: absolute; top: 0; left: 0;
    width: 3px; height: 0; background: var(--accent);
    transition: height 0.4s ease;
  }
  .project-card:hover::before { height: 100%; }
  .project-card:hover { background: #161612; }
  .project-num {
    font-family: 'DM Mono', monospace; font-size: 0.6rem;
    letter-spacing: 0.15em; color: var(--muted);
    margin-bottom: 2rem; display: flex; justify-content: space-between;
    align-items: center;
  }
  .project-cat {
    font-size: 0.6rem; letter-spacing: 0.15em; color: var(--accent);
    text-transform: uppercase;
    background: rgba(200,169,126,0.08);
    padding: 0.2rem 0.6rem;
    border: 1px solid rgba(200,169,126,0.2);
  }
  .project-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.8rem; font-weight: 400; margin-bottom: 0.4rem;
  }
  .project-client {
    font-family: 'DM Mono', monospace; font-size: 0.7rem;
    color: var(--accent); margin-bottom: 1.2rem;
  }
  .project-desc { font-size: 0.82rem; color: var(--muted); line-height: 1.8; }
  .project-meta {
    margin-top: 2rem; padding-top: 1.5rem;
    border-top: 1px solid var(--border);
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem;
  }
  .meta-item { font-family: 'DM Mono', monospace; }
  .meta-label { font-size: 0.55rem; color: var(--muted); letter-spacing: 0.12em; text-transform: uppercase; margin-bottom: 0.3rem; }
  .meta-value { font-size: 0.7rem; color: var(--white); }

  /* EXPERIENCE */
  .experience-section {
    padding: 6rem 3rem;
    border-top: 1px solid var(--border);
    max-width: 1400px; margin: 0 auto;
  }
  .exp-grid { margin-top: 4rem; }
  .exp-row {
    display: grid; grid-template-columns: 200px 1fr auto;
    gap: 3rem; align-items: start;
    padding: 2rem 0; border-bottom: 1px solid var(--border);
    transition: opacity 0.3s;
  }
  .exp-row:hover { opacity: 0.75; }
  .exp-year {
    font-family: 'DM Mono', monospace; font-size: 0.7rem;
    color: var(--accent); letter-spacing: 0.1em;
  }
  .exp-role { font-size: 0.9rem; font-weight: 700; margin-bottom: 0.3rem; }
  .exp-company { font-family: 'DM Mono', monospace; font-size: 0.7rem; color: var(--muted); margin-bottom: 0.6rem; }
  .exp-desc { font-size: 0.8rem; color: var(--muted); line-height: 1.7; }
  .exp-tag {
    font-family: 'DM Mono', monospace; font-size: 0.6rem;
    color: var(--muted); letter-spacing: 0.1em; text-align: right;
    white-space: nowrap;
  }

  /* SOFTWARE */
  .software-section {
    padding: 6rem 3rem;
    max-width: 1400px; margin: 0 auto;
  }
  .sw-grid { display: flex; flex-wrap: wrap; gap: 1rem; margin-top: 3rem; }
  .sw-pill {
    font-family: 'DM Mono', monospace; font-size: 0.7rem;
    letter-spacing: 0.1em; color: var(--muted);
    padding: 0.6rem 1.4rem;
    border: 1px solid var(--border);
    transition: border-color 0.3s, color 0.3s;
  }
  .sw-pill:hover { border-color: var(--accent); color: var(--accent); }
  .sw-pill.advanced { border-color: rgba(200,169,126,0.3); color: var(--accent2); }

  /* WHY */
  .why-section {
    padding: 6rem 3rem;
    background: #0a0a08;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
  }
  .why-inner { max-width: 1400px; margin: 0 auto; }
  .why-list { margin-top: 4rem; }
  .why-item {
    display: flex; align-items: baseline; gap: 2rem;
    padding: 1.8rem 0; border-bottom: 1px solid var(--border);
    overflow: hidden;
  }
  .why-num {
    font-family: 'DM Mono', monospace; font-size: 0.6rem;
    color: var(--accent); letter-spacing: 0.15em; min-width: 30px;
  }
  .why-text {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(1.4rem, 2.5vw, 2rem); font-weight: 300;
  }

  /* CONTACT */
  .contact-section {
    padding: 10rem 3rem;
    text-align: center;
    position: relative; overflow: hidden;
  }
  .contact-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 50% 60% at 50% 50%, rgba(200,169,126,0.05) 0%, transparent 70%);
  }
  .contact-section .section-label { text-align: center; margin-bottom: 1.5rem; }
  .contact-big {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(3rem, 8vw, 7rem); font-weight: 300; line-height: 1;
    margin-bottom: 3rem;
  }
  .contact-big em { font-style: italic; color: var(--accent); }
  .contact-details {
    display: flex; justify-content: center; gap: 4rem;
    font-family: 'DM Mono', monospace; font-size: 0.75rem;
    color: var(--muted); flex-wrap: wrap;
  }
  .contact-item { display: flex; flex-direction: column; gap: 0.3rem; align-items: center; }
  .contact-item .cl { font-size: 0.6rem; letter-spacing: 0.15em; color: var(--accent); text-transform: uppercase; }
  .contact-item a { color: var(--muted); text-decoration: none; transition: color 0.3s; }
  .contact-item a:hover { color: var(--white); }

  /* FOOTER */
  footer {
    padding: 2rem 3rem;
    border-top: 1px solid var(--border);
    display: flex; justify-content: space-between; align-items: center;
    font-family: 'DM Mono', monospace; font-size: 0.6rem;
    color: var(--muted); letter-spacing: 0.1em;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .reveal {
    opacity: 0; transform: translateY(40px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* MARQUEE */
  .marquee-section {
    padding: 2rem 0; overflow: hidden;
    border-top: 1px solid var(--border); border-bottom: 1px solid var(--border);
    background: var(--dark);
  }
  .marquee-track {
    display: flex; gap: 4rem; width: max-content;
    animation: marquee 20s linear infinite;
  }
  .marquee-item {
    font-family: 'Cormorant Garamond', serif; font-style: italic;
    font-size: 1.1rem; color: var(--muted); white-space: nowrap;
    display: flex; align-items: center; gap: 4rem;
  }
  .marquee-item::after {
    content: '✦'; color: var(--accent); font-style: normal; font-size: 0.7rem;
  }
  @keyframes marquee {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  @media (max-width: 768px) {
    nav { padding: 1.2rem 1.5rem; }
    .nav-links { display: none; }
    .hero { padding: 0 1.5rem 4rem; }
    .about { grid-template-columns: 1fr; gap: 3rem; padding: 5rem 1.5rem; }
    .about-photo { order: -1; max-height: 350px; }
    .projects-grid { grid-template-columns: 1fr; }
    .skills-grid { grid-template-columns: 1fr; }
    .exp-row { grid-template-columns: 1fr; gap: 0.5rem; }
    .exp-tag { display: none; }
    .projects-section, .experience-section, .software-section, .skills-section { padding: 4rem 1.5rem; }
    .contact-section { padding: 6rem 1.5rem; }
    .contact-details { gap: 2rem; }
  }
</style>
</head>
<body>

<!-- Custom Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Deja Meilino</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>
  <div class="hero-year">© 2026 — Creative Design by Deja Meilino</div>
  <h1 class="hero-title">
    <em>Deja</em><br>Meilino
  </h1>
  <div class="hero-subtitle">
    3D Designer &amp; 3D Artist — Jakarta, Indonesia
  </div>
  <div class="hero-scroll">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-section">
  <div class="marquee-track">
    <span class="marquee-item">3D Modeling</span>
    <span class="marquee-item">Product Visualization</span>
    <span class="marquee-item">Lighting & Rendering</span>
    <span class="marquee-item">Booth Design</span>
    <span class="marquee-item">Packaging Design</span>
    <span class="marquee-item">Event Visualization</span>
    <span class="marquee-item">Texturing & Material</span>
    <span class="marquee-item">3D Modeling</span>
    <span class="marquee-item">Product Visualization</span>
    <span class="marquee-item">Lighting & Rendering</span>
    <span class="marquee-item">Booth Design</span>
    <span class="marquee-item">Packaging Design</span>
    <span class="marquee-item">Event Visualization</span>
    <span class="marquee-item">Texturing & Material</span>
  </div>
</div>

<!-- ABOUT -->
<section id="about" class="about">
  <div class="about-left reveal">
    <div class="about-label">About Me</div>
    <h2 class="about-heading">
      Menciptakan visual yang<br><em>bersih, elegan,</em><br>dan compelling.
    </h2>
    <p class="about-body">
      Saya adalah 3D Designer dengan pengalaman 2 tahun yang berfokus pada visualisasi produk, product rendering, dan desain booth pameran berbasis 3D. Saya memiliki ketertarikan dalam menciptakan visual yang bersih, elegan, dan mampu meningkatkan daya tarik komersial sebuah produk.
    </p>
    <p class="about-body">
      Saya terbiasa mengerjakan proses desain secara menyeluruh mulai dari 3D modeling, texturing, lighting, hingga rendering final untuk kebutuhan promosi dan branding visual. Sebagai pribadi yang kreatif, detail, dan berdedikasi, saya percaya bahwa visual yang kuat dapat membantu brand menyampaikan kualitas produk secara lebih meyakinkan kepada konsumen.
    </p>
    <div class="about-contacts">
      <div class="contact-row"><span class="label">Phone</span> 081380346983</div>
      <div class="contact-row"><span class="label">Email</span><a href="mailto:hellodejameilino@gmail.com">hellodejameilino@gmail.com</a></div>
      <div class="contact-row"><span class="label">Behance</span><a href="https://www.behance.net/dejalino" target="_blank">behance.net/dejalino</a></div>
      <div class="contact-row"><span class="label">LinkedIn</span><a href="https://www.linkedin.com/in/deja-meilino-ba49a72b4/" target="_blank">linkedin.com/in/deja-meilino</a></div>
      <div class="contact-row"><span class="label">Location</span> Jakarta, Indonesia</div>
    </div>
  </div>
  <div class="about-photo reveal">
    <div class="about-photo-frame">
      <div class="photo-placeholder">
        <span class="initials">DM</span>
        <p>Muhammad Deja Meilino<br>3D Designer / 3D Artist</p>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section class="skills-section">
  <div class="section-header reveal">
    <div>
      <div class="section-label">02 — Core Skills</div>
      <h2 class="section-title">Kemampuan &amp; <em>Keahlian</em></h2>
    </div>
  </div>
  <div class="skills-grid reveal">
    <div class="skill-card">
      <div class="skill-num">01</div>
      <div class="skill-name">3D Modeling &amp; Product Visualization</div>
      <div class="skill-desc">Pembuatan model 3D presisi tinggi untuk berbagai jenis produk komersial dan kebutuhan branding.</div>
    </div>
    <div class="skill-card">
      <div class="skill-num">02</div>
      <div class="skill-name">Lighting &amp; Rendering</div>
      <div class="skill-desc">Setup pencahayaan realistis dan rendering final berkualitas tinggi untuk promosi digital dan produksi.</div>
    </div>
    <div class="skill-card">
      <div class="skill-num">03</div>
      <div class="skill-name">Texturing &amp; Material Creation</div>
      <div class="skill-desc">Pengembangan material dan tekstur yang akurat untuk menghadirkan kesan visual yang elegan dan nyata.</div>
    </div>
    <div class="skill-card">
      <div class="skill-num">04</div>
      <div class="skill-name">Booth Design</div>
      <div class="skill-desc">Perancangan booth display 3D dari konsep hingga final rendering untuk kebutuhan retail dan pameran.</div>
    </div>
    <div class="skill-card">
      <div class="skill-num">05</div>
      <div class="skill-name">Composition &amp; Visual Presentation</div>
      <div class="skill-desc">Komposisi visual yang menarik dan komunikatif untuk meningkatkan daya tarik komersial produk.</div>
    </div>
    <div class="skill-card">
      <div class="skill-num">06</div>
      <div class="skill-name">Animation</div>
      <div class="skill-desc">Visualisasi animasi 3D untuk kebutuhan promosi digital, motion graphic, dan konten media sosial.</div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects" class="projects-section">
  <div class="section-header reveal">
    <div>
      <div class="section-label">03 — Selected Works</div>
      <h2 class="section-title">Proyek <em>Pilihan</em></h2>
    </div>
  </div>
  <div class="projects-grid reveal">

    <div class="project-card">
      <div class="project-num"><span>01 / 07</span><span class="project-cat">Booth Design</span></div>
      <div class="project-title">Batiste</div>
      <div class="project-client">Guardian Store — Jakarta</div>
      <div class="project-desc">Bertanggung jawab dalam pengembangan desain mulai dari konsep visual, pembuatan model 3D, hingga menghasilkan rendering akhir yang mendukung proses presentasi dan realisasi produksi display booth Batiste Dry Shampoo.</div>
      <div class="project-meta">
        <div class="meta-item"><div class="meta-label">Role</div><div class="meta-value">3D Artist</div></div>
        <div class="meta-item"><div class="meta-label">Software</div><div class="meta-value">Blender</div></div>
        <div class="meta-item"><div class="meta-label">Year</div><div class="meta-value">2026</div></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-num"><span>02 / 07</span><span class="project-cat">Booth Design</span></div>
      <div class="project-title">Pure Paw Paw</div>
      <div class="project-client">Assignment Project — 2024</div>
      <div class="project-desc">Merancang dan mengembangkan desain visual 3D booth dengan pendekatan tampilan yang bold, luxurious, dan feminine — mencakup konseptualisasi desain, pemodelan 3D, pengolahan material, pencahayaan, hingga final rendering.</div>
      <div class="project-meta">
        <div class="meta-item"><div class="meta-label">Role</div><div class="meta-value">3D Artist</div></div>
        <div class="meta-item"><div class="meta-label">Software</div><div class="meta-value">Blender, Ai</div></div>
        <div class="meta-item"><div class="meta-label">Year</div><div class="meta-value">2024</div></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-num"><span>03 / 07</span><span class="project-cat">Packaging</span></div>
      <div class="project-title">Vivie Atelier</div>
      <div class="project-client">Cosmetic Packaging — Malang</div>
      <div class="project-desc">Merancang desain visual 3D untuk kemasan produk kosmetik mulai dari pengembangan konsep, pemodelan produk, desain kemasan (diecut & print layout), hingga final rendering untuk promosi digital dan produksi.</div>
      <div class="project-meta">
        <div class="meta-item"><div class="meta-label">Role</div><div class="meta-value">3D Artist</div></div>
        <div class="meta-item"><div class="meta-label">Software</div><div class="meta-value">Blender, Ai</div></div>
        <div class="meta-item"><div class="meta-label">Year</div><div class="meta-value">2024</div></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-num"><span>04 / 07</span><span class="project-cat">Booth Design</span></div>
      <div class="project-title">Mutouch White</div>
      <div class="project-client">Guardian Store — Jakarta</div>
      <div class="project-desc">Visualisasi booth 3D untuk produk Mutouch body lotion yang mencakup pengembangan konsep, pemodelan produk, hingga proses final rendering — desain playful, warna cerah, dengan elemen interaktif yang memperkuat identitas brand.</div>
      <div class="project-meta">
        <div class="meta-item"><div class="meta-label">Role</div><div class="meta-value">3D Artist</div></div>
        <div class="meta-item"><div class="meta-label">Software</div><div class="meta-value">Blender, Ai</div></div>
        <div class="meta-item"><div class="meta-label">Year</div><div class="meta-value">2026</div></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-num"><span>05 / 07</span><span class="project-cat">Product Design</span></div>
      <div class="project-title">LushTint</div>
      <div class="project-client">Product Design — Jakarta</div>
      <div class="project-desc">Visualisasi 3D produk lipstick LushTint yang berfokus pada tampilan visual yang bold, luxurious, dan feminine untuk meningkatkan daya tarik produk — dari konseptualisasi, pemodelan 3D, material, lighting, hingga final rendering.</div>
      <div class="project-meta">
        <div class="meta-item"><div class="meta-label">Role</div><div class="meta-value">3D Artist</div></div>
        <div class="meta-item"><div class="meta-label">Software</div><div class="meta-value">Blender, Ai</div></div>
        <div class="meta-item"><div class="meta-label">Year</div><div class="meta-value">2025</div></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-num"><span>06 / 07</span><span class="project-cat">Display Booth</span></div>
      <div class="project-title">Mr.Vet</div>
      <div class="project-client">Assignment Project — CatFest</div>
      <div class="project-desc">Perancangan visual booth display 3D untuk brand Mr.Vet yang mencakup pengembangan konsep, struktur display produk, serta final rendering dengan pendekatan visual yang komunikatif dan menarik untuk kebutuhan retail activation.</div>
      <div class="project-meta">
        <div class="meta-item"><div class="meta-label">Role</div><div class="meta-value">3D Artist</div></div>
        <div class="meta-item"><div class="meta-label">Software</div><div class="meta-value">Blender, Ai</div></div>
        <div class="meta-item"><div class="meta-label">Year</div><div class="meta-value">2025</div></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-num"><span>07 / 07</span><span class="project-cat">Event Ballroom</span></div>
      <div class="project-title">Sampoerna Academy</div>
      <div class="project-client">Event Ballroom — Surabaya</div>
      <div class="project-desc">Visualisasi 3D ballroom event untuk Chinese New Year 2026. Mencakup pengembangan konsep desain, pemodelan elemen dekorasi dan display, hingga final rendering untuk mendukung kebutuhan visual event tahunan.</div>
      <div class="project-meta">
        <div class="meta-item"><div class="meta-label">Role</div><div class="meta-value">3D Artist</div></div>
        <div class="meta-item"><div class="meta-label">Software</div><div class="meta-value">Blender, Ai</div></div>
        <div class="meta-item"><div class="meta-label">Year</div><div class="meta-value">2026</div></div>
      </div>
    </div>

    <div class="project-card" style="background: #0d0d0b;">
      <div class="project-num"><span>+</span><span class="project-cat">Other Works</span></div>
      <div class="project-title" style="font-size:1.4rem; margin-top:1rem;">More Projects</div>
      <div class="project-desc" style="margin-top:1rem;">Edufarmer Ballroom · Aston Sentul New Year · Zoomlion Booth · WEGO Booth · Samsung Booth · Shopee Super Awards</div>
      <div class="project-desc" style="margin-top:1rem; color: var(--accent); font-family:'DM Mono',monospace; font-size:0.7rem;">2023 — 2026</div>
    </div>

  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience" class="experience-section">
  <div class="section-header reveal">
    <div>
      <div class="section-label">04 — Experience</div>
      <h2 class="section-title">Pengalaman <em>Kerja</em></h2>
    </div>
  </div>
  <div class="exp-grid reveal">
    <div class="exp-row">
      <div class="exp-year">Jan 2026</div>
      <div>
        <div class="exp-role">3D Designer &amp; Visualizer</div>
        <div class="exp-company">Batiste — Jakarta</div>
        <div class="exp-desc">Merancang visual booth 3D untuk kebutuhan display produk, mulai dari tahap perancangan hingga proses produksi untuk outlet Guardian di Jakarta.</div>
      </div>
      <div class="exp-tag">Booth Design</div>
    </div>
    <div class="exp-row">
      <div class="exp-year">Feb 2026</div>
      <div>
        <div class="exp-role">3D Designer &amp; Visualizer</div>
        <div class="exp-company">Mutouch — Jakarta</div>
        <div class="exp-desc">Merancang visual booth 3D untuk kebutuhan display produk, mulai dari tahap perancangan hingga proses produksi untuk outlet Guardian di Jakarta.</div>
      </div>
      <div class="exp-tag">Booth Design</div>
    </div>
    <div class="exp-row">
      <div class="exp-year">Feb 2026</div>
      <div>
        <div class="exp-role">Creative Decorator Staff</div>
        <div class="exp-company">Sampoerna Academy — Surabaya</div>
        <div class="exp-desc">Happy Lunar New Year 2026 — Petra Surabaya "Golden Horse Welcome Spring"</div>
      </div>
      <div class="exp-tag">Event</div>
    </div>
    <div class="exp-row">
      <div class="exp-year">Des 2025</div>
      <div>
        <div class="exp-role">Creative Decorator Staff</div>
        <div class="exp-company">Shopee — Jakarta</div>
        <div class="exp-desc">Pembuatan Iklan — Shopee Super Awards 2025</div>
      </div>
      <div class="exp-tag">Advertising</div>
    </div>
    <div class="exp-row">
      <div class="exp-year">Des 2025</div>
      <div>
        <div class="exp-role">Creative Decorator Staff</div>
        <div class="exp-company">Kementerian UMKM — Jakarta</div>
        <div class="exp-desc">Harmonisasi penyusunan regulasi data UMK. "Satu data UMKM menjadikan program UMKM tepat, terukur dan akuntabel"</div>
      </div>
      <div class="exp-tag">Government</div>
    </div>
    <div class="exp-row">
      <div class="exp-year">Okt 2024</div>
      <div>
        <div class="exp-role">Vice Executive Chair</div>
        <div class="exp-company">Toi — Malang Creative Center</div>
        <div class="exp-desc">International poster exhibition — Malang Creative Center "Piecefulness"</div>
      </div>
      <div class="exp-tag">Exhibition</div>
    </div>
  </div>
</section>

<!-- SOFTWARE -->
<section class="software-section">
  <div class="section-header reveal">
    <div>
      <div class="section-label">05 — Tools</div>
      <h2 class="section-title">Software <em>Skills</em></h2>
    </div>
  </div>
  <div class="sw-grid reveal">
    <span class="sw-pill advanced">Blender (Advanced)</span>
    <span class="sw-pill advanced">Adobe Illustrator (Advanced)</span>
    <span class="sw-pill">Substance Painter</span>
    <span class="sw-pill">Adobe Photoshop</span>
    <span class="sw-pill">V-Ray</span>
    <span class="sw-pill">After Effects</span>
    <span class="sw-pill">Canva</span>
    <span class="sw-pill">Figma</span>
  </div>
  <div style="margin-top:2rem; padding:1.5rem 0; border-top: 1px solid var(--border);">
    <div class="section-label" style="margin-bottom:1rem;">Workflow</div>
    <div style="font-family:'DM Mono',monospace; font-size:0.75rem; color:var(--muted); display:flex; flex-wrap:wrap; gap:0.5rem; align-items:center;">
      <span>Concept Research</span><span style="color:var(--accent)">→</span>
      <span>3D Modeling</span><span style="color:var(--accent)">→</span>
      <span>Material &amp; Texture Setup</span><span style="color:var(--accent)">→</span>
      <span>Lighting Setup</span><span style="color:var(--accent)">→</span>
      <span>Rendering</span><span style="color:var(--accent)">→</span>
      <span>Post Processing</span>
    </div>
  </div>
</section>

<!-- WHY -->
<section class="why-section">
  <div class="why-inner">
    <div class="section-label reveal">06 — Why Work With Me</div>
    <div class="why-list reveal">
      <div class="why-item">
        <span class="why-num">01</span>
        <span class="why-text">Spesialis visualisasi produk 3D berkualitas tinggi</span>
      </div>
      <div class="why-item">
        <span class="why-num">02</span>
        <span class="why-text">Presisi tinggi dalam lighting dan rendering</span>
      </div>
      <div class="why-item">
        <span class="why-num">03</span>
        <span class="why-text">Pemahaman mendalam tentang estetika brand kecantikan</span>
      </div>
      <div class="why-item">
        <span class="why-num">04</span>
        <span class="why-text">Kemampuan mengubah konsep menjadi visual yang compelling</span>
      </div>
      <div class="why-item">
        <span class="why-num">05</span>
        <span class="why-text">Pendekatan kreatif dalam pemecahan masalah</span>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact" class="contact-section">
  <div class="contact-bg"></div>
  <div class="section-label reveal">07 — Contact</div>
  <h2 class="contact-big reveal">
    Let's Create<br><em>Something Great</em><br>Together
  </h2>
  <div class="contact-details reveal">
    <div class="contact-item">
      <span class="cl">Phone</span>
      <span>081380346983</span>
    </div>
    <div class="contact-item">
      <span class="cl">Email</span>
      <a href="mailto:hellodejameilino@gmail.com">hellodejameilino@gmail.com</a>
    </div>
    <div class="contact-item">
      <span class="cl">Behance</span>
      <a href="https://www.behance.net/dejalino" target="_blank">@Deja Meilino</a>
    </div>
    <div class="contact-item">
      <span class="cl">LinkedIn</span>
      <a href="https://www.linkedin.com/in/deja-meilino-ba49a72b4/" target="_blank">@Deja Meilino</a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span>© 2026 Deja Meilino — All rights reserved</span>
  <span>Creative Design by Deja Meilino · Jakarta, Indonesia</span>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animCursor() {
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animCursor);
  }
  animCursor();

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
