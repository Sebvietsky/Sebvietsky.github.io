<script lang="ts">
  import "../app.css";
  import { onMount } from "svelte";

  let { children } = $props();
  let theme = $state<"light" | "dark">("light");
  let progressEl: HTMLDivElement;

  onMount(() => {
    // Le thème est déjà appliqué par le script anti-flash de app.html
    const current = document.documentElement.getAttribute("data-theme");
    theme = current === "dark" ? "dark" : "light";

    const updateScroll = () => {
      const docHeight =
        document.documentElement.scrollHeight - window.innerHeight;
      const progress =
        docHeight > 0 ? Math.min(window.scrollY / docHeight, 1) : 0;
      if (progressEl) progressEl.style.transform = `scaleX(${progress})`;
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
    const next = theme === "light" ? "dark" : "light";
    document.documentElement.classList.add("theme-transition");
    theme = next;
    document.documentElement.setAttribute("data-theme", next);

    try {
      localStorage.setItem("theme", next);
    } catch {
      // localStorage indisponible (navigation privée stricte) — on ignore
    }

    window.setTimeout(
      () => document.documentElement.classList.remove("theme-transition"),
      450,
    );
  }
</script>

<div class="scroll-progress" bind:this={progressEl}></div>

<header class="terminal-surface" aria-label="Navigation principale">
  <div class="container nav-inner">
    <a href="#top" class="brand" aria-label="Sébastien Fabié — retour en haut">
      <svg class="brand-logo" viewBox="0 0 150 72" aria-hidden="true">
        <text x="0" y="58" font-size="62" font-weight="500" fill="#c39cf0"
          >&#123;</text
        >
        <text
          x="42"
          y="56"
          font-size="56"
          font-weight="700"
          letter-spacing="-2"
          fill="#f1eef7">sf</text
        >
        <text x="112" y="58" font-size="62" font-weight="500" fill="#c39cf0"
          >&#125;</text
        >
      </svg>
      <span class="brand-prompt">sebastien@fabie:~$</span>
    </a>

    <nav>
      <a href="#projets" class="nav-link">Projets</a>
      <a href="#parcours" class="nav-link">Parcours</a>
      <a href="#contact" class="nav-link accent">Contact</a>

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
          <svg
            width="16"
            height="16"
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
          <svg
            width="16"
            height="16"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            aria-hidden="true"
          >
            <circle cx="12" cy="12" r="4" />
            <path d="M12 2v2" /><path d="M12 20v2" />
            <path d="m4.93 4.93 1.41 1.41" /><path
              d="m17.66 17.66 1.41 1.41"
            /><path d="M2 12h2" /><path d="M20 12h2" /><path
              d="m6.34 17.66-1.41 1.41"
            /><path d="m19.07 4.93-1.41 1.41" />
          </svg>
        {/if}
      </button>
    </nav>
  </div>
</header>

<main>
  {@render children()}
</main>

<style>
  header {
    position: sticky;
    top: 0;
    z-index: 100;
    border-bottom: 1px solid var(--term-border);
    background-color: rgba(42, 38, 51, 0.94);
    backdrop-filter: blur(6px);
    -webkit-backdrop-filter: blur(6px);
  }

  .nav-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1.5rem;
    padding-block: 0.9rem;
  }

  .brand {
    display: flex;
    align-items: center;
    gap: 0.7rem;
  }

  .brand-logo {
    height: 26px;
    width: auto;
    font-family: var(--font-mono);
  }

  .brand-prompt {
    font-size: 0.8125rem;
    font-weight: 600;
    color: var(--term-fg);
  }

  nav {
    display: flex;
    align-items: center;
    gap: 1.4rem;
    font-size: 0.78rem;
    font-weight: 500;
  }

  .nav-link {
    color: var(--term-faded);
    transition: color 0.15s ease;
  }

  .nav-link.accent {
    color: var(--accent-bright);
  }

  .nav-link:hover {
    color: var(--term-fg);
  }

  .theme-toggle {
    display: grid;
    place-items: center;
    width: 2rem;
    height: 2rem;
    background: transparent;
    border: 1px solid var(--term-ghost-border);
    border-radius: 4px;
    color: var(--term-muted);
    cursor: pointer;
    transition:
      color 0.15s ease,
      border-color 0.15s ease;
  }

  .theme-toggle:hover {
    color: var(--accent-bright);
    border-color: var(--accent-bright);
  }

  @media (max-width: 640px) {
    .brand-prompt {
      display: none;
    }

    nav {
      gap: 1rem;
      font-size: 0.75rem;
    }
  }
</style>
