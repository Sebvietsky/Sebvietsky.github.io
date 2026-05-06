<script lang="ts">
  import "../app.css";
  import { onMount } from "svelte";

  let { children } = $props();
  let scrolled = $state(false);
  let progressEl: HTMLDivElement;

  onMount(() => {
    const heroParallax = document.querySelector<HTMLElement>(".hero-parallax");

    const updateScroll = () => {
      const scrollY = window.scrollY;
      scrolled = scrollY > 24;

      // D — progress bar : ratio scroll / page
      const docHeight =
        document.documentElement.scrollHeight - window.innerHeight;
      const progress = docHeight > 0 ? Math.min(scrollY / docHeight, 1) : 0;
      if (progressEl) {
        progressEl.style.transform = `scaleX(${progress})`;
      }

      // B — parallaxe douce sur le hero (max 80px de décalage)
      if (heroParallax && scrollY < 800) {
        const offset = Math.min(scrollY * 0.25, 80);
        heroParallax.style.setProperty("--scroll-offset", String(-offset));
      }
    };

    window.addEventListener("scroll", updateScroll, { passive: true });
    updateScroll();

    // A & C — reveal + stagger animations
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("in-view");
            observer.unobserve(entry.target);
          }
        });
      },
      { threshold: 0.12, rootMargin: "0px 0px -60px 0px" },
    );

    document
      .querySelectorAll(".reveal, .stagger")
      .forEach((el) => observer.observe(el));

    return () => {
      window.removeEventListener("scroll", updateScroll);
      observer.disconnect();
    };
  });
</script>

<!-- D — Barre de progression de scroll -->
<div class="scroll-progress" bind:this={progressEl}></div>

<header class:scrolled aria-label="Navigation principale">
  <div class="container nav-inner">
    <a href="#top" class="brand" aria-label="Retour en haut">
      <span class="brand-mark">SF</span>
      <span class="brand-text">Sébastien Fabié</span>
    </a>
    <nav>
      <a href="#projects">Projets</a>
      <a href="#stack">Stack</a>
      <a href="#parcours">Parcours</a>
      <a href="#contact" class="cta">Contact</a>
    </nav>
  </div>
</header>

<main id="top">
  {@render children()}
</main>

<footer>
  <div class="container footer-inner">
    <p class="mono">© 2026 — Sébastien Fabié. Construit avec SvelteKit.</p>
    <p class="mono muted">
      <a
        href="https://github.com/Sebvietsky/Sebvietsky.github.io"
        target="_blank"
        rel="noopener noreferrer">Code source</a
      >
    </p>
  </div>
</footer>

<style>
  header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;
    padding: 1.25rem 0;
    transition:
      background 0.3s ease,
      padding 0.3s ease,
      border-color 0.3s ease;
    border-bottom: 1px solid transparent;
  }

  header.scrolled {
    background: rgba(250, 250, 247, 0.85);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    padding: 0.85rem 0;
    border-bottom-color: var(--border);
  }

  .nav-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 2rem;
  }

  .brand {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    font-family: var(--font-display);
    font-weight: 500;
    letter-spacing: -0.01em;
  }

  .brand-mark {
    display: grid;
    place-items: center;
    width: 2.25rem;
    height: 2.25rem;
    background: var(--accent);
    color: #fff;
    font-family: var(--font-mono);
    font-weight: 700;
    font-size: 0.85rem;
    border-radius: 4px;
    transform: rotate(-4deg);
    transition: transform 0.3s ease;
  }

  .brand:hover .brand-mark {
    transform: rotate(0deg);
  }

  .brand-text {
    font-size: 1rem;
  }

  nav {
    display: flex;
    align-items: center;
    gap: 2rem;
    font-size: 0.9rem;
    font-weight: 500;
  }

  nav a {
    color: var(--fg-muted);
    transition: color 0.2s ease;
    position: relative;
  }

  nav a:hover {
    color: var(--fg);
  }

  nav a.cta {
    padding: 0.55rem 1.1rem;
    background: var(--accent);
    color: #fff;
    border-radius: 999px;
    font-weight: 600;
  }

  nav a.cta:hover {
    background: var(--accent-soft);
    color: #fff;
  }

  @media (max-width: 640px) {
    .brand-text {
      display: none;
    }

    nav {
      gap: 1.25rem;
      font-size: 0.85rem;
    }

    nav a:not(.cta) {
      display: none;
    }
  }

  footer {
    border-top: 1px solid var(--border);
    padding: 2.5rem 0;
    margin-top: 6rem;
    position: relative;
    z-index: 1;
  }

  .footer-inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 1rem;
    color: var(--fg-faded);
  }

  .footer-inner a {
    color: var(--fg-muted);
    border-bottom: 1px solid var(--border-strong);
    transition: color 0.2s ease;
  }

  .footer-inner a:hover {
    color: var(--accent);
  }
</style>
