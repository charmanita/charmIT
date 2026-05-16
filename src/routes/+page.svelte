<nav>
  <div class="nav-logo">charm<span>IT</span></div>
  <ul class="nav-links">
    <li><a href="#about">about</a></li>
    <li><a href="#contact">contact</a></li>
  </ul>
</nav>

<div class="hero">
  <div class="grid-bg"></div>
  <div class="hero-tag">// tech help for everyone</div>
  <h1 class="hero-title">charm<span>IT</span></h1>
  <p class="hero-sub">
    Here to help you navigate the world of technology - one problem at a time.
  </p>
  <a href="https://forms.gle/xnQqd2eUVEtyBRHR9" class="hero-cta" target="_blank"
    >GET IN TOUCH</a
  >
</div>

<div class="divider"></div>

<section id="about">
  <div class="section-label">// about</div>
  <div class="section-title">get to know charmIT</div>
  <div class="about-grid">
    <div class="about-text">
      <p>
        My name is Hunter Roberson. I am a Computer Science student with a
        passion for all things technology - from Windows systems to Linux,
        networking, and beyond.
      </p>
      <p>
        I'm planning to pursue a degree in computer science with a focus on IT
        and systems administration. I learn something new every single day.
      </p>
      <p>
        Whether it's troubleshooting a broken install, setting up a drive, or
        just figuring out why something isn't working — I'm here to help.
      </p>
      <p>
        Reach me at <a href="mailto:charmit@charmanita.dev"
          >charmit@charmanita.dev</a
        >
      </p>
    </div>
    <div class="skills-list">
      <div class="skill-item">
        <div class="skill-dot"></div>
        Windows OS (advanced)
      </div>
      <div class="skill-item">
        <div class="skill-dot"></div>
        Linux (learning)
      </div>
      <div class="skill-item">
        <div class="skill-dot"></div>
        ChromeOS
      </div>
      <div class="skill-item">
        <div class="skill-dot"></div>
        Hardware (HDD/SSD installs)
      </div>
      <div class="skill-item">
        <div class="skill-dot"></div>
        File management & recovery
      </div>
      <div class="skill-item">
        <div class="skill-dot"></div>
        General IT helpdesk
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<section id="contact">
  <div class="section-label">// contact</div>
  <div class="section-title">need help?</div>
  <div class="contact-box">
    <p>
      Got a tech problem that you can't quite wrap your head around? Fill out
      the contact form or directly send me a email. Response times are usually
      pretty quick (1-2 hours)
    </p>
    <div class="contact-links">
      <a
        href="https://forms.gle/xnQqd2eUVEtyBRHR9"
        class="contact-link"
        target="_blank">→ contact form</a
      >
      <a href="mailto:charmit@charmanita.dev" class="contact-link"
        >→ charmit@charmanita.dev</a
      >
    </div>
  </div>
</section>

<footer>© 2026 Hunter Roberson · charmIT</footer>

<style>
  nav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem 2.5rem;
    background: rgba(8, 11, 15, 0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: var(--mono);
    font-size: 1.1rem;
    font-weight: 600;
    color: var(--accent);
    letter-spacing: -0.02em;
  }
  .nav-logo span {
    color: var(--text);
  }
  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }
  .nav-links a {
    font-family: var(--mono);
    font-size: 0.8rem;
    color: var(--muted);
    letter-spacing: 0.05em;
    transition: color 0.2s;
  }
  .nav-links a:hover {
    color: var(--accent);
  }
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 6rem 2rem 4rem;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 600px;
    height: 600px;
    background: radial-gradient(
      circle,
      rgba(0, 255, 136, 0.06) 0%,
      transparent 70%
    );
    pointer-events: none;
  }
  .grid-bg {
    position: absolute;
    inset: 0;
    background-image: linear-gradient(var(--border) 1px, transparent 1px),
      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    mask-image: radial-gradient(
      ellipse at center,
      rgba(0, 0, 0, 0.3) 0%,
      transparent 70%
    );
  }
  .hero-tag {
    font-family: var(--mono);
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.15em;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s ease forwards 0.2s;
    opacity: 0;
  }
  .hero-title {
    font-family: var(--mono);
    font-size: clamp(3rem, 8vw, 6rem);
    font-weight: 600;
    color: var(--text);
    letter-spacing: -0.04em;
    line-height: 1;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s ease forwards 0.35s;
    opacity: 0;
  }
  .hero-title span {
    color: var(--accent);
  }
  .hero-sub {
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 480px;
    margin-bottom: 3rem;
    font-weight: 300;
    animation: fadeUp 0.6s ease forwards 0.5s;
    opacity: 0;
  }
  .hero-cta {
    display: inline-block;
    font-family: var(--mono);
    font-size: 0.85rem;
    font-weight: 500;
    color: var(--bg);
    background: var(--accent);
    padding: 0.75rem 2rem;
    letter-spacing: 0.08em;
    transition:
      opacity 0.2s,
      transform 0.2s;
    animation: fadeUp 0.6s ease forwards 0.65s;
    opacity: 0;
  }
  .hero-cta:hover {
    opacity: 0.85;
    transform: translateY(-1px);
  }
  .divider {
    height: 1px;
    background: var(--border);
    max-width: 900px;
    margin: 0 auto;
  }
  section {
    padding: 6rem 2rem;
    max-width: 900px;
    margin: 0 auto;
  }
  .section-label {
    font-family: var(--mono);
    font-size: 0.7rem;
    color: var(--accent);
    letter-spacing: 0.2em;
    margin-bottom: 1rem;
  }
  .section-title {
    font-family: var(--mono);
    font-size: 1.8rem;
    font-weight: 600;
    color: var(--text);
    letter-spacing: -0.03em;
    margin-bottom: 2rem;
  }
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    align-items: start;
  }
  .about-text {
    color: var(--muted);
    font-size: 0.95rem;
    line-height: 1.8;
  }
  .about-text p {
    margin-bottom: 1rem;
  }
  .about-text a {
    color: var(--accent);
  }
  .about-text a:hover {
    text-decoration: underline;
  }
  .skills-list {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }
  .skill-item {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    font-family: var(--mono);
    font-size: 0.8rem;
    color: var(--muted);
    padding: 0.6rem 1rem;
    border: 1px solid var(--border);
    background: var(--surface);
  }
  .skill-dot {
    width: 6px;
    height: 6px;
    background: var(--accent);
    border-radius: 50%;
    flex-shrink: 0;
  }
  .contact-box {
    border: 1px solid var(--border);
    background: var(--surface);
    padding: 2.5rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 2rem;
  }
  .contact-box p {
    color: var(--muted);
    font-size: 0.95rem;
    max-width: 400px;
  }
  .contact-links {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    flex-shrink: 0;
  }
  .contact-link {
    font-family: var(--mono);
    font-size: 0.8rem;
    color: var(--accent);
    letter-spacing: 0.05em;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.5rem 1rem;
    border: 1px solid rgba(0, 255, 136, 0.25);
    transition: background 0.2s;
  }
  .contact-link:hover {
    background: var(--accent-dim);
  }
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem;
    text-align: center;
    font-family: var(--mono);
    font-size: 0.75rem;
    color: var(--muted);
    letter-spacing: 0.05em;
  }
  @keyframes fadeUp {
    from {
      opacity: 0;
      transform: translateY(16px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  @media (max-width: 600px) {
    nav {
      padding: 1rem 1.25rem;
    }
    .nav-links {
      gap: 1rem;
    }
    .about-grid {
      grid-template-columns: 1fr;
    }
    .contact-box {
      flex-direction: column;
    }
    section {
      padding: 4rem 1.25rem;
    }
  }
</style>
