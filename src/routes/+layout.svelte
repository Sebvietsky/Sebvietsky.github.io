<script lang="ts">
  import "../app.css";
  import { onMount } from "svelte";

  let { children } = $props();
  let scrolled = $state(false);
  let theme = $state<"light" | "dark">("light");
  let progressEl: HTMLDivElement;

  onMount(() => {
    // Lire le thème actuel (déjà appliqué par le script anti-flash dans app.html)
    const current = document.documentElement.getAttribute("data-theme");
    theme = current === "dark" ? "dark" : "light";

    const heroParallax = document.querySelector<HTMLElement>(".hero-parallax");

    const updateScroll = () => {
      const scrollY = window.scrollY;
      scrolled = scrollY > 24;

      const docHeight =
        document.documentElement.scrollHeight - window.innerHeight;
      const progress = docHeight > 0 ? Math.min(scrollY / docHeight, 1) : 0;
      if (progressEl) {
        progressEl.style.transform = `scaleX(${progress})`;
      }

      if (heroParallax && scrollY < 800) {
        const offset = Math.min(scrollY * 0.25, 80);
        heroParallax.style.setProperty("--scroll-offset", String(-offset));
      }
    };

    window.addEventListener("scroll", updateScroll, { passive: true });
    updateScroll();

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

  function toggleTheme() {
    const newTheme = theme === "light" ? "dark" : "light";

    // Active la transition fluide juste pour ce changement
    document.documentElement.classList.add("theme-transition");

    theme = newTheme;
    document.documentElement.setAttribute("data-theme", newTheme);

    try {
      localStorage.setItem("theme", newTheme);
    } catch (e) {
      // localStorage indisponible (mode privé strict, etc.) — on ignore silencieusement
    }

    // Retire la classe de transition après l'animation pour ne pas affecter les autres animations
    window.setTimeout(() => {
      document.documentElement.classList.remove("theme-transition");
    }, 450);
  }
</script>

<!-- Barre de progression de scroll -->
<div class="scroll-progress" bind:this={progressEl}></div>

<header class:scrolled aria-label="Navigation principale">
  <div class="container nav-inner">
    <a href="#top" class="brand" aria-label="Retour en haut">
      <span class="brand-mark">SF</span>
      <span class="brand-text">Sébastien Fabié</span>
    </a>
    <nav>
      <a href="#projects" class="nav-link">Projets</a>
      <a href="#stack" class="nav-link">Stack</a>
      <a href="#parcours" class="nav-link">Parcours</a>

      <button
        type="button"
        class="theme-toggle"
        onclick={toggleTheme}
        aria-label={theme === "light"
          ? "Activer le mode sombre"
          : "Activer le mode clair"}
        title={theme === "light" ? "Mode sombre" : "Mode clair"}
      >
        {#if theme === "light"}
          <!-- Icône lune (= passer au dark) -->
          <svg
            width="18"
            height="18"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            aria-hidden="true"
          >
            <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z" />
          </svg>
        {:else}
          <!-- Icône soleil (= passer au light) -->
          <svg
            width="18"
            height="18"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            aria-hidden="true"
          >
            <circle cx="12" cy="12" r="4" />
            <path d="M12 2v2" />
            <path d="M12 20v2" />
            <path d="m4.93 4.93 1.41 1.41" />
            <path d="m17.66 17.66 1.41 1.41" />
            <path d="M2 12h2" />
            <path d="M20 12h2" />
            <path d="m6.34 17.66-1.41 1.41" />
            <path d="m19.07 4.93-1.41 1.41" />
          </svg>
        {/if}
      </button>

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
    background: var(--header-bg);
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
    gap: 1.5rem;
    font-size: 0.9rem;
    font-weight: 500;
  }

  .nav-link {
    color: var(--fg-muted);
    transition: color 0.2s ease;
    position: relative;
  }

  .nav-link:hover {
    color: var(--fg);
  }

  .cta {
    padding: 0.55rem 1.1rem;
    background: var(--accent);
    color: #fff;
    border-radius: 999px;
    font-weight: 600;
    transition:
      background 0.2s ease,
      color 0.2s ease;
  }

  .cta:hover {
    background: var(--accent-soft);
    color: #fff;
  }

  .theme-toggle {
    display: grid;
    place-items: center;
    width: 2.25rem;
    height: 2.25rem;
    background: transparent;
    border: 1px solid var(--border-strong);
    border-radius: 999px;
    color: var(--fg-muted);
    cursor: pointer;
    font-family: inherit;
    transition:
      color 0.2s ease,
      border-color 0.2s ease,
      background-color 0.2s ease,
      transform 0.2s ease;
  }

  .theme-toggle:hover {
    color: var(--accent);
    border-color: var(--accent);
    transform: rotate(15deg);
  }

  .theme-toggle:focus-visible {
    outline: 2px solid var(--accent);
    outline-offset: 2px;
  }

  .theme-toggle svg {
    display: block;
  }

  @media (max-width: 640px) {
    .brand-text {
      display: none;
    }

    nav {
      gap: 0.85rem;
      font-size: 0.85rem;
    }

    .nav-link {
      display: none;
    }

    .theme-toggle {
      width: 2rem;
      height: 2rem;
    }

    .theme-toggle svg {
      width: 16px;
      height: 16px;
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
