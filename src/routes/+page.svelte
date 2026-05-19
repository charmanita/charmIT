<script lang="ts">
  import { onMount } from "svelte";

  let name = $state("");
  let email = $state("");
  let message = $state("");
  let loading = $state(false);
  let submitted = $state(false);
  let error = $state("");

  onMount(() => {
    const script = document.createElement("script");
    script.src = "https://challenges.cloudflare.com/turnstile/v0/api.js";
    script.async = true;
    script.defer = true;
    document.head.appendChild(script);
  });

  function getTurnstileToken(): string | null {
    const el = document.querySelector<HTMLInputElement>(
      'input[name="cf-turnstile-response"]',
    );
    return el?.value || null;
  }

  async function submit() {
    if (!name || !email || !message) {
      error = "please fill out all fields.";
      return;
    }

    const token = getTurnstileToken();
    if (!token) {
      error = "verification not complete. please wait a moment and try again.";
      return;
    }

    loading = true;
    error = "";
    try {
      const res = await fetch("https://charmit-form.hdroberson23.workers.dev", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ name, email, message, turnstileToken: token }),
      });
      if (res.ok) {
        submitted = true;
      } else {
        error = "something went wrong. try emailing directly.";
      }
    } catch {
      error = "something went wrong. try emailing directly.";
    }
    loading = false;
  }
</script>

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
  <a href="#contact" class="hero-cta">GET IN TOUCH</a>
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
        and system administration. I learn something new every single day.
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
        Hardware installation
      </div>
      <div class="skill-item">
        <div class="skill-dot"></div>
        File recovery (Windows only!)
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
    <div class="form-wrap">
      {#if submitted}
        <p class="success">✓ message sent — i'll get back to you soon.</p>
      {:else}
        <div class="form">
          <div class="field">
            <label for="name">name</label>
            <input
              id="name"
              type="text"
              bind:value={name}
              placeholder="your name"
            />
          </div>
          <div class="field">
            <label for="email">email</label>
            <input
              id="email"
              type="email"
              bind:value={email}
              placeholder="your@email.com"
            />
          </div>
          <div class="field">
            <label for="message">message</label>
            <textarea
              id="message"
              bind:value={message}
              rows="5"
              placeholder="what do you need help with?"
            ></textarea>
          </div>
          {#if error}
            <p class="error">{error}</p>
          {/if}
          <div
            class="cf-turnstile"
            data-sitekey="0x4AAAAAADSIWZmGesHPsI4B"
            data-theme="dark"
            data-size="compact"
          ></div>
          <button class="submit" onclick={submit} disabled={loading}>
            {loading ? "sending..." : "→ send message"}
          </button>
        </div>
      {/if}
    </div>
    <div class="contact-links">
      <a
        href="mailto:charmit@charmanita.dev?subject=%5BcharmIT%5D"
        class="contact-link">→ charmit@charmanita.dev</a
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
    align-items: flex-start;
    justify-content: space-between;
    gap: 2rem;
  }
  .form-wrap {
    flex: 1;
  }
  .form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  .field {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
  }
  label {
    font-family: var(--mono);
    font-size: 0.7rem;
    color: var(--accent);
    letter-spacing: 0.15em;
  }
  input,
  textarea {
    background: var(--bg);
    border: 1px solid var(--border);
    color: var(--text);
    font-family: var(--mono);
    font-size: 0.85rem;
    padding: 0.6rem 0.9rem;
    outline: none;
    resize: vertical;
    transition: border-color 0.2s;
  }
  input:focus,
  textarea:focus {
    border-color: var(--accent);
  }
  input::placeholder,
  textarea::placeholder {
    color: var(--muted);
  }
  .submit {
    font-family: var(--mono);
    font-size: 0.85rem;
    font-weight: 500;
    color: var(--bg);
    background: var(--accent);
    border: none;
    padding: 0.75rem 2rem;
    cursor: pointer;
    letter-spacing: 0.08em;
    transition: opacity 0.2s;
    align-self: flex-start;
  }
  .submit:hover {
    opacity: 0.85;
  }
  .submit:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }
  .success {
    font-family: var(--mono);
    font-size: 0.85rem;
    color: var(--accent);
  }
  .error {
    font-family: var(--mono);
    font-size: 0.8rem;
    color: #ff4444;
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
