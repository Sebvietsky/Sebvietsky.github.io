<script lang="ts">
  const stack = {
    Backend: ["Node.js", "TypeScript", "Express", "NestJS", "Prisma"],
    Frontend: ["React", "Svelte", "HTML / CSS", "JavaScript"],
    "Bases de données": ["PostgreSQL", "MongoDB"],
    "DevOps & outils": ["Docker", "Git", "Linux", "Nginx"],
  };

  type Project = {
    num: string;
    name: string;
    tagline: string;
    description: string;
    stack: string[];
    highlights: string[];
    github: string | null;
    status?: string;
  };

  const projects: Project[] = [
    {
      num: "01",
      name: "oquiz",
      tagline:
        "API REST microservices avec authentification JWT et logging distribué",
      description:
        "Plateforme de gestion de quiz construite en architecture microservices. Authentification double-token (JWT + refresh) avec rotation, RBAC à 3 niveaux, validation Zod stricte, logging distribué via Winston vers un service dédié MongoDB. Orchestration complète avec Docker Compose.",
      stack: [
        "Node.js",
        "TypeScript",
        "Express",
        "Prisma",
        "PostgreSQL",
        "MongoDB",
        "Docker",
      ],
      github: "https://github.com/Sebvietsky/quiz-api",
      highlights: [
        "8 tables relationnelles",
        "JWT avec rotation",
        "4 services dockerisés",
      ],
    },
    {
      num: "02",
      name: "oKanban",
      tagline:
        "Application Kanban full-stack avec authentification et intégration IA",
      description:
        "Application de gestion de tâches type Trello. Backend Node.js / Express / Sequelize, base PostgreSQL, frontend Svelte. Authentification JWT avec Argon2, gestion des rôles utilisateurs, et intégration de l'API Mistral pour la correction orthographique automatique des contenus saisis.",
      stack: [
        "Node.js",
        "Express",
        "Sequelize",
        "PostgreSQL",
        "Svelte",
        "JWT",
        "Mistral AI",
        "Docker",
      ],
      github: "https://github.com/Sebvietsky/kanban",
      highlights: [
        "Auth JWT + Argon2",
        "Intégration API Mistral",
        "Architecture full-stack",
      ],
    },
    {
      num: "03",
      name: "Kilterboard",
      tagline: "API NestJS pour le suivi d'entraînement d'escalade",
      description:
        "API REST construite avec NestJS et Prisma autour d'un usage personnel : tracker mes sessions d'escalade sur Kilterboard. Architecture monorepo, pipeline CI/CD GitHub Actions dès le départ, TypeScript strict.",
      stack: ["NestJS", "TypeScript", "Prisma", "PostgreSQL", "GitHub Actions"],
      github: null,
      status: "Projet en cours — repo privé",
      highlights: [
        "Architecture monorepo",
        "CI/CD intégrée",
        "TypeScript strict",
      ],
    },
  ];

  const experiences = [
    {
      period: "Nov. 2025 — Juin 2026",
      role: "Concepteur Développeur d'Application Web",
      company: "École O'clock",
      detail: "Formation intensive 798h — Bac +3/4 (Titre Pro niv. 6)",
      type: "formation",
    },
    {
      period: "Avril 2023 — Présent",
      role: "Sales associate & Skiman",
      company: "Salomon",
      detail:
        "Conseil technique, bootfitting, montage ski. Diplôme Sidas Académie Ski Rouge.",
      type: "pro",
    },
    {
      period: "Nov. 2022 — Avril 2023",
      role: "Conseiller de vente Outdoor",
      company: "Ekosport",
      detail: "Spécialité escalade : gestion de stock et réapprovisionnement.",
      type: "pro",
    },
    {
      period: "Mars — Août 2022",
      role: "Assistant Trade Marketing",
      company: "Millet Mountain Group",
      detail:
        "Gestion de projet marketing, déploiement d'outils en Europe, prise de parole.",
      type: "pro",
    },
    {
      period: "2021 — 2022",
      role: "Licence Pro Outdoor International Sales & Promotion",
      company: "Université Savoie Mont Blanc",
      detail: "Formation en anglais — Bac +3.",
      type: "formation",
    },
  ];
</script>

<!-- ========================================================================
     HERO  —  parallaxe douce (B)
     ======================================================================== -->
<section class="hero">
  <div class="container hero-grid hero-parallax">
    <div class="hero-content">
      <p class="mono eyebrow">— Disponible pour un stage en juin 2026</p>
      <h1>
        Développeur <em>fullstack</em>,<br />
        avec un détour <span class="accent">par la montagne</span>.
      </h1>
      <p class="lede">
        Je viens du commerce et du marketing outdoor. Aujourd'hui, je transpose
        ces réflexes — comprendre l'utilisateur, livrer en équipe, soigner le
        détail — au code. Spécialisation backend Node.js / TypeScript.
      </p>
      <div class="hero-actions">
        <a href="#projects" class="btn-primary">Voir les projets</a>
        <a href="#contact" class="btn-ghost">Me contacter</a>
        <a
          href="/cv-sebastien-fabie.pdf"
          download
          class="btn-cv"
          aria-label="Télécharger mon CV au format PDF"
        >
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
            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" />
            <polyline points="7 10 12 15 17 10" />
            <line x1="12" y1="15" x2="12" y2="3" />
          </svg>
          <span>Télécharger le CV</span>
        </a>
      </div>
    </div>

    <aside class="hero-card">
      <div class="card-row">
        <span class="mono label">Localisation</span>
        <span>Annecy, France</span>
      </div>
      <div class="card-row">
        <span class="mono label">Formation</span>
        <span>O'clock — CDA</span>
      </div>
      <div class="card-row">
        <span class="mono label">Stack principale</span>
        <span>Node.js · TypeScript</span>
      </div>
      <div class="card-row">
        <span class="mono label">Recherche</span>
        <span>Stage 2-3 mois</span>
      </div>
      <div class="card-row last">
        <span class="mono label">Statut</span>
        <span class="status">
          <span class="dot"></span>
          En recherche active
        </span>
      </div>
    </aside>
  </div>
</section>

<!-- ========================================================================
     ABOUT  —  reveal classique
     ======================================================================== -->
<section class="about reveal">
  <div class="container about-grid">
    <div class="section-header">
      <p class="mono section-num">/ 00</p>
      <h2>À propos</h2>
    </div>
    <div class="about-content">
      <p>
        Quatre ans dans le retail outdoor — Salomon, Ekosport, Millet — m'ont
        appris quelque chose qui me sert tous les jours en code&nbsp;: <strong
          >la rigueur du détail compte</strong
        >. Quand tu déformes une coque de chaussure de ski pour le pied d'un
        client, l'erreur ne pardonne pas. C'est le même état d'esprit que
        j'apporte aux tests, aux migrations de base de données, à la qualité du
        code.
      </p>
      <p>
        Aujourd'hui en formation intensive chez <a
          href="https://oclock.io"
          target="_blank"
          rel="noopener noreferrer">O'clock</a
        >, je construis des projets backend avec Node.js, TypeScript, Express,
        NestJS, Prisma. Mon attrait&nbsp;: les architectures structurées, la
        sécurité applicative, et tout ce qui se passe quand une requête HTTP
        arrive sur un serveur.
      </p>
    </div>
  </div>
</section>

<!-- ========================================================================
     STACK  —  stagger reveal sur les blocs
     ======================================================================== -->
<section id="stack" class="stack reveal">
  <div class="container">
    <div class="section-header centered">
      <p class="mono section-num">/ 01</p>
      <h2>Stack technique</h2>
      <p class="section-sub">Les outils que je manipule au quotidien.</p>
    </div>

    <div class="stack-grid stagger">
      {#each Object.entries(stack) as [category, items]}
        <div class="stack-block">
          <h3 class="mono">{category}</h3>
          <ul>
            {#each items as item}
              <li>{item}</li>
            {/each}
          </ul>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ========================================================================
     PROJECTS  —  stagger reveal sur les cards
     ======================================================================== -->
<section id="projects" class="projects reveal">
  <div class="container">
    <div class="section-header">
      <p class="mono section-num">/ 02</p>
      <h2>Projets</h2>
      <p class="section-sub">
        Trois projets construits pendant ma formation pour explorer l'écosystème
        backend moderne.
      </p>
    </div>

    <div class="project-list stagger">
      {#each projects as project}
        <article class="project" class:locked={project.status}>
          <div class="project-meta">
            <span class="mono project-num">{project.num}</span>
          </div>
          <div class="project-body">
            {#if project.status}
              <div class="project-badge" aria-label={project.status}>
                <svg
                  width="12"
                  height="12"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2.4"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  aria-hidden="true"
                >
                  <rect x="3" y="11" width="18" height="11" rx="2" ry="2" />
                  <path d="M7 11V7a5 5 0 0 1 10 0v4" />
                </svg>
                <span>{project.status}</span>
              </div>
            {/if}

            <h3>{project.name}</h3>
            <p class="project-tagline">{project.tagline}</p>
            <p class="project-desc">{project.description}</p>

            <ul class="project-highlights">
              {#each project.highlights as h}
                <li>{h}</li>
              {/each}
            </ul>

            <ul class="project-stack">
              {#each project.stack as tech}
                <li>{tech}</li>
              {/each}
            </ul>

            {#if project.github}
              <a
                href={project.github}
                target="_blank"
                rel="noopener noreferrer"
                class="project-link"
              >
                <span>Voir sur GitHub</span>
                <svg
                  width="14"
                  height="14"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <line x1="7" y1="17" x2="17" y2="7"></line>
                  <polyline points="7 7 17 7 17 17"></polyline>
                </svg>
              </a>
            {/if}
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<!-- ========================================================================
     PARCOURS  —  stagger reveal sur les items de timeline
     ======================================================================== -->
<section id="parcours" class="parcours reveal">
  <div class="container">
    <div class="section-header">
      <p class="mono section-num">/ 03</p>
      <h2>Parcours</h2>
      <p class="section-sub">Du retail outdoor au code backend.</p>
    </div>

    <ol class="timeline stagger">
      {#each experiences as exp}
        <li class="timeline-item" data-type={exp.type}>
          <div class="timeline-period mono">{exp.period}</div>
          <div class="timeline-content">
            <h3>{exp.role}</h3>
            <p class="timeline-company">{exp.company}</p>
            <p class="timeline-detail">{exp.detail}</p>
          </div>
        </li>
      {/each}
    </ol>
  </div>
</section>

<!-- ========================================================================
     CONTACT  —  reveal classique
     ======================================================================== -->
<section id="contact" class="contact reveal">
  <div class="container">
    <div class="contact-card">
      <p class="mono section-num">/ 04</p>
      <h2>On échange&nbsp;?</h2>
      <p class="contact-lede">
        Je cherche un stage à partir de juin 2026 pour rejoindre une équipe
        technique, monter en compétences, et contribuer dès les premières
        semaines.
      </p>

      <div class="contact-links">
        <a href="mailto:sebastien.fabie@gmail.com" class="contact-link primary">
          <span class="mono link-label">Email</span>
          <span class="link-value">sebastien.fabie@gmail.com</span>
        </a>
        <a
          href="https://github.com/Sebvietsky"
          target="_blank"
          rel="noopener noreferrer"
          class="contact-link"
        >
          <span class="mono link-label">GitHub</span>
          <span class="link-value">@Sebvietsky</span>
        </a>
        <a
          href="https://www.linkedin.com/in/sebastienfabie/"
          target="_blank"
          rel="noopener noreferrer"
          class="contact-link"
        >
          <span class="mono link-label">LinkedIn</span>
          <span class="link-value">Sébastien Fabié</span>
        </a>
        <a href="tel:+33673241187" class="contact-link">
          <span class="mono link-label">Téléphone</span>
          <span class="link-value">+33 6 73 24 11 87</span>
        </a>
      </div>
    </div>
  </div>
</section>

<style>
  /* =========================================================================
	   Section commune
	   ========================================================================= */
  section {
    padding: 6rem 0;
    position: relative;
  }

  .section-header {
    margin-bottom: 3.5rem;
  }

  .section-header.centered {
    text-align: center;
  }

  .section-num {
    color: var(--accent);
    margin-bottom: 0.75rem;
    letter-spacing: 0.05em;
  }

  h2 {
    font-family: var(--font-display);
    font-weight: 400;
    font-size: clamp(2rem, 4.5vw, 3rem);
    line-height: 1.1;
    letter-spacing: -0.02em;
    color: var(--fg);
  }

  .section-sub {
    color: var(--fg-muted);
    margin-top: 0.75rem;
    max-width: 540px;
    font-size: 1.05rem;
  }

  .section-header.centered .section-sub {
    margin-inline: auto;
  }

  /* =========================================================================
	   HERO
	   ========================================================================= */
  .hero {
    padding-top: 9rem;
    padding-bottom: 7rem;
    min-height: 92vh;
    display: flex;
    align-items: center;
  }

  .hero-grid {
    display: grid;
    grid-template-columns: 1.6fr 1fr;
    gap: 4rem;
    align-items: center;
  }

  .eyebrow {
    color: var(--accent);
    margin-bottom: 1.5rem;
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
  }

  .hero-content h1 {
    font-family: var(--font-display);
    font-weight: 300;
    font-size: clamp(2.5rem, 6vw, 4.5rem);
    line-height: 1.05;
    letter-spacing: -0.025em;
    margin-bottom: 1.75rem;
  }

  .hero-content h1 em {
    font-style: italic;
    font-variation-settings: "opsz" 144;
    color: var(--fg);
  }

  .hero-content h1 .accent {
    color: var(--accent);
    font-style: italic;
  }

  .lede {
    font-size: 1.15rem;
    color: var(--fg-muted);
    max-width: 520px;
    margin-bottom: 2.5rem;
  }

  .hero-actions {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .btn-primary,
  .btn-ghost {
    display: inline-flex;
    align-items: center;
    padding: 0.85rem 1.5rem;
    font-weight: 600;
    font-size: 0.95rem;
    border-radius: 999px;
    transition: all 0.25s ease;
    font-family: var(--font-body);
  }

  .btn-primary {
    background: var(--accent);
    color: #fff;
  }

  .btn-primary:hover {
    background: var(--accent-soft);
    transform: translateY(-2px);
  }

  .btn-ghost {
    border: 1px solid var(--border-strong);
    color: var(--fg);
  }

  .btn-ghost:hover {
    border-color: var(--fg);
    background: var(--bg-card);
  }

  .btn-cv {
    display: inline-flex;
    align-items: center;
    gap: 0.55rem;
    padding: 0.85rem 1.4rem;
    font-weight: 600;
    font-size: 0.95rem;
    border-radius: 999px;
    border: 1px dashed var(--border-strong);
    color: var(--fg-muted);
    transition: all 0.25s ease;
    font-family: var(--font-body);
  }

  .btn-cv:hover {
    border-style: solid;
    border-color: var(--accent);
    color: var(--accent);
    transform: translateY(-2px);
  }

  .btn-cv svg {
    transition: transform 0.25s ease;
  }

  .btn-cv:hover svg {
    transform: translateY(2px);
  }

  .hero-card {
    background: var(--bg-elev);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.75rem;
    font-size: 0.92rem;
    transform: rotate(0.8deg);
    box-shadow: 0 18px 50px -22px rgba(60, 50, 35, 0.2);
  }

  .card-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.65rem 0;
    border-bottom: 1px dashed var(--border);
    gap: 1rem;
  }

  .card-row.last {
    border-bottom: none;
  }

  .label {
    color: var(--fg-faded);
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .status {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    color: var(--accent);
  }

  .dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 0 4px var(--accent-glow);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%,
    100% {
      box-shadow: 0 0 0 4px var(--accent-glow);
    }
    50% {
      box-shadow: 0 0 0 8px var(--accent-glow);
    }
  }

  @media (max-width: 860px) {
    .hero-grid {
      grid-template-columns: 1fr;
      gap: 3rem;
    }

    .hero-card {
      transform: none;
    }
  }

  /* =========================================================================
	   ABOUT
	   ========================================================================= */
  .about-grid {
    display: grid;
    grid-template-columns: 280px 1fr;
    gap: 4rem;
    align-items: start;
  }

  .about-content p {
    font-size: 1.1rem;
    color: var(--fg-muted);
    max-width: 620px;
  }

  .about-content p + p {
    margin-top: 1.5rem;
  }

  .about-content strong {
    color: var(--fg);
    font-weight: 600;
  }

  .about-content a {
    color: var(--accent);
    border-bottom: 1px solid var(--accent);
    transition: opacity 0.2s ease;
  }

  .about-content a:hover {
    opacity: 0.7;
  }

  @media (max-width: 760px) {
    .about-grid {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
  }

  /* =========================================================================
	   STACK
	   ========================================================================= */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1.5rem;
  }

  .stack-block {
    background: var(--bg-elev);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 1.5rem;
    transition:
      border-color 0.3s ease,
      transform 0.3s ease,
      box-shadow 0.3s ease;
  }

  .stack-block:hover {
    border-color: var(--border-strong);
    transform: translateY(-2px);
    box-shadow: 0 12px 30px -18px rgba(60, 50, 35, 0.15);
  }

  .stack-block h3 {
    color: var(--accent);
    font-size: 0.8rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-bottom: 1rem;
  }

  .stack-block ul {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .stack-block li {
    color: var(--fg);
    font-size: 0.95rem;
    padding-left: 1rem;
    position: relative;
  }

  .stack-block li::before {
    content: "·";
    position: absolute;
    left: 0;
    color: var(--accent);
    font-weight: 700;
  }

  /* =========================================================================
	   PROJECTS
	   ========================================================================= */
  .project-list {
    display: flex;
    flex-direction: column;
    gap: 3.5rem;
  }

  .project {
    display: grid;
    grid-template-columns: 100px 1fr;
    gap: 2rem;
    padding: 2.5rem;
    background: var(--bg-elev);
    border: 1px solid var(--border);
    border-radius: 12px;
    position: relative;
    transition:
      border-color 0.3s ease,
      transform 0.3s ease,
      box-shadow 0.3s ease;
  }

  .project:not(.locked):hover {
    border-color: var(--border-strong);
    transform: translateY(-3px);
    box-shadow: 0 18px 40px -22px rgba(60, 50, 35, 0.2);
  }

  /* Variante "projet en cours" */
  .project.locked {
    opacity: 0.78;
    border-style: dashed;
    background: var(--bg-card);
  }

  .project.locked .project-num {
    color: var(--fg-faded);
    opacity: 0.6;
  }

  .project-badge {
    position: absolute;
    top: 1.5rem;
    right: 1.5rem;
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.35rem 0.7rem;
    font-family: var(--font-mono);
    font-size: 0.72rem;
    font-weight: 500;
    color: var(--accent);
    background: var(--bg);
    border: 1px solid var(--border-strong);
    border-radius: 999px;
    letter-spacing: 0.02em;
  }

  .project-badge svg {
    flex-shrink: 0;
  }

  .project-num {
    font-size: 2rem;
    color: var(--fg-faded);
    font-weight: 300;
  }

  .project h3 {
    font-family: var(--font-display);
    font-weight: 500;
    font-size: 1.85rem;
    letter-spacing: -0.01em;
    margin-bottom: 0.4rem;
  }

  .project-tagline {
    color: var(--accent);
    font-weight: 500;
    font-size: 0.95rem;
    margin-bottom: 1.25rem;
  }

  .project-desc {
    color: var(--fg-muted);
    margin-bottom: 1.5rem;
    max-width: 680px;
  }

  .project-highlights {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
    list-style: none;
  }

  .project-highlights li {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    color: var(--fg);
    background: var(--bg-card);
    border: 1px solid var(--border);
    padding: 0.35rem 0.8rem;
    border-radius: 4px;
  }

  .project-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem 0.8rem;
    list-style: none;
    margin-bottom: 1.75rem;
  }

  .project-stack li {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    color: var(--fg-muted);
  }

  .project-stack li::after {
    content: "/";
    margin-left: 0.8rem;
    color: var(--fg-faded);
  }

  .project-stack li:last-child::after {
    display: none;
  }

  .project-link {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    color: var(--accent);
    font-weight: 600;
    font-size: 0.95rem;
    border-bottom: 1px solid var(--accent);
    padding-bottom: 2px;
    transition: gap 0.2s ease;
  }

  .project-link:hover {
    gap: 0.75rem;
  }

  @media (max-width: 700px) {
    .project {
      grid-template-columns: 1fr;
      padding: 1.75rem;
      gap: 1rem;
    }

    .project-num {
      font-size: 1.5rem;
    }

    .project-badge {
      top: 1rem;
      right: 1rem;
    }
  }

  /* =========================================================================
	   PARCOURS / TIMELINE
	   ========================================================================= */
  .timeline {
    list-style: none;
    max-width: 800px;
    position: relative;
    padding-left: 2rem;
  }

  .timeline::before {
    content: "";
    position: absolute;
    left: 0;
    top: 0.5rem;
    bottom: 0.5rem;
    width: 1px;
    background: linear-gradient(
      to bottom,
      transparent,
      var(--border-strong) 10%,
      var(--border-strong) 90%,
      transparent
    );
  }

  .timeline-item {
    position: relative;
    padding-bottom: 2.5rem;
    display: grid;
    grid-template-columns: 180px 1fr;
    gap: 2rem;
  }

  .timeline-item:last-child {
    padding-bottom: 0;
  }

  .timeline-item::before {
    content: "";
    position: absolute;
    left: -2.4rem;
    top: 0.5rem;
    width: 11px;
    height: 11px;
    border-radius: 50%;
    background: var(--bg);
    border: 2px solid var(--fg-faded);
    transition: all 0.3s ease;
  }

  .timeline-item[data-type="formation"]::before {
    border-color: var(--accent);
    background: var(--accent);
  }

  .timeline-period {
    color: var(--fg-faded);
    padding-top: 0.15rem;
    font-size: 0.78rem;
  }

  .timeline-content h3 {
    font-family: var(--font-display);
    font-weight: 500;
    font-size: 1.15rem;
    margin-bottom: 0.2rem;
  }

  .timeline-company {
    color: var(--accent);
    font-weight: 500;
    font-size: 0.95rem;
    margin-bottom: 0.5rem;
  }

  .timeline-detail {
    color: var(--fg-muted);
    font-size: 0.95rem;
  }

  @media (max-width: 640px) {
    .timeline-item {
      grid-template-columns: 1fr;
      gap: 0.5rem;
    }
  }

  /* =========================================================================
	   CONTACT
	   ========================================================================= */
  .contact-card {
    background: var(--bg-elev);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: clamp(2.5rem, 5vw, 4rem);
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
    position: relative;
    overflow: hidden;
    box-shadow: 0 24px 60px -28px rgba(60, 50, 35, 0.25);
  }

  .contact-card::before {
    content: "";
    position: absolute;
    inset: 0;
    background: radial-gradient(
      ellipse at top,
      var(--accent-glow) 0%,
      transparent 60%
    );
    pointer-events: none;
  }

  .contact-card > * {
    position: relative;
    z-index: 1;
  }

  .contact-card h2 {
    margin-top: 0.5rem;
  }

  .contact-lede {
    color: var(--fg-muted);
    font-size: 1.1rem;
    max-width: 520px;
    margin: 1.25rem auto 2.5rem;
  }

  .contact-links {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 0.75rem;
    text-align: left;
  }

  .contact-link {
    display: flex;
    flex-direction: column;
    gap: 0.35rem;
    padding: 1.1rem 1.25rem;
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: 10px;
    transition: all 0.25s ease;
  }

  .contact-link:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
  }

  .contact-link.primary {
    border-color: var(--accent);
    background: linear-gradient(135deg, var(--bg), var(--accent-glow));
  }

  .link-label {
    color: var(--fg-faded);
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  .link-value {
    color: var(--fg);
    font-weight: 500;
    font-size: 1rem;
  }
</style>
