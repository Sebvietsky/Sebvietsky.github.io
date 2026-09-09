<script lang="ts">
  const stack = [
    "Node.js",
    "TypeScript",
    "PostgreSQL",
    "Express / NestJS",
    "Docker",
    "React"
  ];

  type Project = {
    name: string;
    domain: string;
    url: string;
    preview: string;
    alt: string;
    pitch: string;
    points: string[];
  };

  const projects: Project[] = [
    {
      name: "Margot Hamel",
      domain: "margot-website-eta.vercel.app",
      url: "https://margot-website-eta.vercel.app/",
      preview: "/preview-margot.jpg",
      alt: "Page d'accueil du site de Margot Hamel, coach d'escalade à Annecy.",
      pitch:
        "Site vitrine et réservation pour une coach d'escalade à Annecy : formules d'accompagnement, cours particuliers et sorties en extérieur.",
      points: [
        "Next.js / React · déploiement continu sur Vercel",
        "Prise de rendez-vous intégrée · thème clair et sombre",
        "En-têtes de sécurité stricts (CSP, anti-framing)",
      ],
    },
    {
      name: "GamerChallenges",
      domain: "gamer-challenge-front-end.vercel.app",
      url: "https://gamer-challenge-front-end.vercel.app/",
      preview: "/preview-gamerchallenges.jpg",
      alt: "Page d'accueil de GamerChallenges, plateforme de défis de jeux vidéo.",
      pitch:
        "Plateforme communautaire de défis de jeux vidéo : chacun crée ses challenges, participe à ceux des autres et grimpe au classement.",
      points: [
        "Front Next.js / React branché sur une API dédiée",
        "Comptes utilisateurs, participations et favoris",
        "Classements et tri des challenges par tendance",
      ],
    },
  ];

  const experiences = [
    {
      period: "Nov. 2025 — Août 2026",
      role: "Concepteur Développeur d'Application Web",
      org: "École O'clock",
      detail: "Formation intensive 798h — Bac +3/4 (Titre Pro niv. 6)",
      current: true,
    },
    {
      period: "Avril 2023 — Présent",
      role: "Sales associate & Skiman",
      org: "Salomon",
      detail:
        "Conseil technique, bootfitting, montage ski.",
      current: false,
    },
    {
      period: "Mars — Août 2022",
      role: "Assistant Trade Marketing",
      org: "Millet Mountain Group",
      detail:
        "Gestion de projet marketing, déploiement d'outils en Europe, prise de parole.",
      current: false,
    },
    {
      period: "2021 — 2022",
      role: "Licence Pro Outdoor International Sales & Promotion",
      org: "Université Savoie Mont Blanc",
      detail: "Formation en anglais — Bac +3.",
      current: true,
    },
  ];

  const email = "sebastienfabie@gmail.com";
</script>

<!-- ============================ HERO ============================ -->
<section id="top" class="hero terminal-surface">
  <div class="container hero-inner">
    <div class="gutter-lines" aria-hidden="true">
      {#each Array(20) as _, i}
        <span>{i + 1}</span>
      {/each}
    </div>

    <div class="hero-content">
      <div class="whoami">
        <p class="prompt"><span class="dollar">$</span> whoami</p>
        <p class="identity">Sébastien Fabié - développeur web fullstack (appétence forte au backend)</p>
        <p>
          <span class="badge-available"
            >● Disponible - CDI ou missions freelance · Annecy / à distance</span
          >
        </p>
      </div>

      <h1>
        Des sites et des API<br />solides, pensés<br />pour durer et grandir<span
          class="caret">_</span
        >
      </h1>

      <p class="lede">
        Je conçois le moteur de vos applications : bases de données,
        authentification, connexions entre services. Fiable, sécurisé,
        documenté.
      </p>

      <div class="stack">
        <span class="label">MA STACK</span>
        <div class="chips">
          {#each stack as tech}
            <span class="chip">{tech}</span>
          {/each}
        </div>
      </div>

      <div class="actions">
        <a href="#projets" class="btn btn-solid">
          <span class="btn-main">Voir mes projets →</span>
          <span class="btn-sub">$ ls ./projets</span>
        </a>
        <a href="/cv-sebastien-fabie.pdf" class="btn btn-ghost" download>
          <span class="btn-main">Télécharger mon CV</span>
          <span class="btn-sub">$ curl cv.pdf</span>
        </a>
        <a href="#contact" class="btn btn-ghost">
          <span class="btn-main">Me contacter</span>
          <span class="btn-sub">$ mail sebastien</span>
        </a>
      </div>

      <p class="note">
        # J'apprends en continu et peux étendre ma stack pour répondre à vos besoins.
      </p>
    </div>
  </div>
</section>

<!-- ============================ PROJETS ============================ -->
<section id="projets" class="section">
  <div class="container">
    <div class="section-head reveal">
      <h2>Projets en ligne</h2>
      <span class="cmd"
        >$ ls ./projets --prod · {projects.length} résultats</span
      >
    </div>

    <div class="projects stagger">
      {#each projects as p}
        <article class="card">
          <div class="card-chrome">
            <span class="dot red"></span>
            <span class="dot yellow"></span>
            <span class="dot green"></span>
            <span class="card-domain">{p.domain}</span>
            <span class="card-live">● EN LIGNE</span>
          </div>

          <a
            class="card-preview"
            href={p.url}
            target="_blank"
            rel="noopener noreferrer"
            aria-label="Ouvrir {p.name} dans un nouvel onglet"
          >
            <img src={p.preview} alt={p.alt} loading="lazy" width="1200" height="538" />
            <span class="card-preview-cta">Voir le site en ligne ↗</span>
          </a>

          <div class="card-body">
            <div class="card-title">
              <h3>{p.name}</h3>
              <a href={p.url} target="_blank" rel="noopener noreferrer"
                >Ouvrir le site ↗</a
              >
            </div>
            <p class="card-pitch">{p.pitch}</p>
            <ul class="card-points">
              {#each p.points as point}
                <li><span class="chevron">›</span> {point}</li>
              {/each}
            </ul>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<!-- ============================ PARCOURS ============================ -->
<section id="parcours" class="section bordered">
  <div class="container">
    <div class="section-head reveal">
      <h2>Parcours</h2>
      <span class="cmd">$ git log --date=short</span>
    </div>

    <div class="timeline stagger">
      {#each experiences as exp, i}
        <div class="tl-row">
          <div class="tl-rail">
            <span class="tl-dot" class:filled={exp.current}></span>
            {#if i < experiences.length - 1}
              <span class="tl-line"></span>
            {/if}
          </div>
          <span class="tl-period">{exp.period}</span>
          <div class="tl-body" class:last={i === experiences.length - 1}>
            <h3>{exp.role}</h3>
            <span class="tl-org">{exp.org}</span>
            <p>{exp.detail}</p>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ============================ CONTACT ============================ -->
<section id="contact" class="section terminal-surface">
  <div class="container">
    <div class="section-head reveal">
      <h2>Parlons de votre projet</h2>
      <span class="cmd">$ ./contact.sh</span>
    </div>

    <p class="contact-lede reveal">
      CDI ou mission freelance, à Annecy ou à distance. Décrivez-moi votre
      besoin en quelques lignes.
    </p>

    <div class="actions stagger">
      <a href="mailto:{email}" class="btn btn-solid">
        <span class="btn-main">Envoyer un e-mail →</span>
        <span class="btn-sub">{email}</span>
      </a>
      <a
        href="https://github.com/Sebvietsky"
        target="_blank"
        rel="noopener noreferrer"
        class="btn btn-ghost"
      >
        <span class="btn-main">GitHub ↗</span>
        <span class="btn-sub">@Sebvietsky</span>
      </a>
      <a
        href="https://www.linkedin.com/in/sebastienfabie/"
        target="_blank"
        rel="noopener noreferrer"
        class="btn btn-ghost"
      >
        <span class="btn-main">LinkedIn ↗</span>
        <span class="btn-sub">sébastien fabié</span>
      </a>
    </div>

    <footer class="term-footer">
      <span class="ok">[portfolio]</span>
      <span>Sébastien Fabié - Annecy · 2026</span>
      <a
        href="https://github.com/Sebvietsky/Sebvietsky.github.io"
        target="_blank"
        rel="noopener noreferrer">code source</a
      >
      <span class="exit">exit 0</span>
    </footer>
  </div>
</section>

<style>
  /* ---------- Blocs de section ---------- */
  .section {
    padding-block: 3.75rem 4rem;
  }

  .section.bordered {
    border-top: 1px solid var(--border-soft);
  }

  .section-head {
    display: flex;
    align-items: baseline;
    gap: 0.9rem;
    flex-wrap: wrap;
  }

  .section-head h2 {
    font-size: clamp(1.35rem, 3.4vw, 1.75rem);
    font-weight: 700;
    letter-spacing: -0.02em;
  }

  .section-sub {
    margin-top: 0.5rem;
    font-size: 0.84rem;
    color: var(--fg-muted);
  }

  /* ---------- Hero ---------- */
  .hero-inner {
    display: grid;
    grid-template-columns: 44px minmax(0, 1fr);
    padding-block: 3.5rem 3.75rem;
  }

  .gutter-lines {
    display: flex;
    flex-direction: column;
    font-size: 0.75rem;
    line-height: 1.75;
    color: var(--term-line);
    text-align: right;
    padding-right: 0.875rem;
    border-right: 1px solid var(--term-border);
  }

  .hero-content {
    padding-left: 2.125rem;
    display: flex;
    flex-direction: column;
    gap: 1.6rem;
  }

  .whoami {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    font-size: 0.845rem;
    line-height: 1.75;
  }

  .dollar {
    color: var(--accent-bright);
  }

  .identity {
    font-size: 1.0625rem;
    font-weight: 600;
    line-height: 1.5;
  }

  .badge-available {
    display: inline-block;
    background: var(--ok-bg);
    color: var(--ok-fg);
    padding: 0.1875rem 0.625rem;
    font-size: 0.8125rem;
    font-weight: 600;
  }

  h1 {
    font-size: clamp(2rem, 6vw, 3rem);
    line-height: 1.15;
    font-weight: 700;
    letter-spacing: -0.03em;
    max-width: 860px;
  }

  .lede {
    max-width: 600px;
    font-size: 0.9375rem;
    line-height: 1.7;
    color: var(--term-muted);
  }

  .stack {
    display: flex;
    flex-direction: column;
    gap: 0.625rem;
  }

  .label {
    font-size: 0.6875rem;
    font-weight: 500;
    letter-spacing: 0.06em;
    color: var(--term-faded);
  }

  .chips {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .chip {
    font-size: 0.78rem;
    font-weight: 600;
    background: #3a2a52;
    color: #e2d3f7;
    padding: 0.375rem 0.75rem;
    border-radius: 4px;
  }

  .note {
    font-size: 0.75rem;
    line-height: 1.6;
    color: var(--term-faded);
  }

  /* ---------- Boutons ---------- */
  .actions {
    display: flex;
    gap: 0.875rem;
    flex-wrap: wrap;
  }

  .btn {
    display: flex;
    flex-direction: column;
    gap: 0.1875rem;
    padding: 0.75rem 1.375rem;
    border-radius: 4px;
    border: 1px solid transparent;
  }

  .btn-main {
    font-size: 0.875rem;
    font-weight: 600;
  }

  .btn-sub {
    font-size: 0.65rem;
  }

  .btn-solid {
    background: var(--btn-bg);
    color: var(--btn-fg);
    transition: background 0.15s ease;
  }

  .btn-solid .btn-sub {
    color: var(--btn-sub);
  }

  .btn-solid:hover {
    background: var(--btn-bg-hover);
  }

  .btn-ghost {
    border-color: var(--term-ghost-border);
    color: var(--term-fg);
    padding-block: 0.6875rem;
    transition: border-color 0.15s ease;
  }

  .btn-ghost .btn-sub {
    color: var(--term-faded);
  }

  .btn-ghost:hover {
    border-color: var(--accent-bright);
  }

  /* ---------- Cartes projets ---------- */
  .projects {
    margin-top: 1.625rem;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(min(100%, 340px), 1fr));
    gap: 1.25rem;
  }

  .card {
    display: flex;
    flex-direction: column;
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
    background: var(--bg-elev);
    box-shadow: var(--shadow-card);
    transition:
      border-color 0.15s ease,
      box-shadow 0.25s ease,
      transform 0.25s ease;
  }

  .card:hover {
    border-color: var(--accent);
    box-shadow: var(--shadow-card-hover);
    transform: translateY(-3px);
  }

  .card-chrome {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.625rem 0.875rem;
    background: var(--bg-panel);
    border-bottom: 1px solid var(--border-panel);
  }

  .dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    flex: none;
  }

  .dot.red {
    background: #e5534b;
  }
  .dot.yellow {
    background: #d4a72c;
  }
  .dot.green {
    background: #57ab5a;
  }

  .card-domain {
    margin-left: 0.5rem;
    font-size: 0.6875rem;
    font-weight: 500;
    color: var(--fg-muted);
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .card-live {
    margin-left: auto;
    flex: none;
    font-size: 0.6rem;
    font-weight: 600;
    background: var(--accent-tint-bg);
    color: var(--accent-tint-fg);
    padding: 0.125rem 0.4375rem;
    border-radius: 4px;
  }

  .card-preview {
    position: relative;
    display: block;
    height: 240px;
    overflow: hidden;
    background: var(--bg-panel);
  }

  .card-preview img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: top center;
    transition: transform 0.5s cubic-bezier(0.2, 0.8, 0.2, 1);
  }

  .card-preview::after {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(
      to top,
      rgba(42, 38, 51, 0.55),
      rgba(42, 38, 51, 0) 55%
    );
    opacity: 0;
    transition: opacity 0.25s ease;
  }

  .card-preview-cta {
    position: absolute;
    left: 50%;
    bottom: 1rem;
    transform: translate(-50%, 8px);
    z-index: 1;
    font-size: 0.75rem;
    font-weight: 600;
    color: #fff;
    background: var(--btn-bg);
    padding: 0.5rem 0.9rem;
    border-radius: 4px;
    opacity: 0;
    transition:
      opacity 0.25s ease,
      transform 0.25s ease;
    pointer-events: none;
  }

  .card:hover .card-preview img {
    transform: scale(1.04);
  }

  .card:hover .card-preview::after,
  .card:hover .card-preview-cta,
  .card-preview:focus-visible .card-preview-cta {
    opacity: 1;
  }

  .card:hover .card-preview-cta {
    transform: translate(-50%, 0);
  }

  .card-body {
    padding: 1.25rem 1.375rem 1.375rem;
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  .card-title {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    gap: 0.75rem;
    flex-wrap: wrap;
  }

  .card-title h3 {
    font-size: 1.3125rem;
    font-weight: 700;
  }

  .card-title a {
    font-size: 0.78rem;
    font-weight: 600;
    color: var(--accent);
    white-space: nowrap;
    transition: color 0.15s ease;
  }

  .card-title a:hover {
    color: var(--fg);
  }

  .card-pitch {
    font-size: 0.8125rem;
    line-height: 1.65;
    color: var(--fg-muted);
  }

  .card-points {
    list-style: none;
    font-size: 0.78rem;
    line-height: 1.9;
    color: var(--fg-muted);
  }

  .chevron {
    color: var(--accent);
  }

  /* ---------- Timeline ---------- */
  .timeline {
    margin-top: 2.25rem;
    display: flex;
    flex-direction: column;
  }

  .tl-row {
    display: grid;
    grid-template-columns: 24px 190px minmax(0, 1fr);
    gap: 0 1.5rem;
    align-items: start;
  }

  .tl-rail {
    display: flex;
    flex-direction: column;
    align-items: center;
    align-self: stretch;
  }

  .tl-dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    flex: none;
    margin-top: 4px;
    background: var(--bg);
    border: 2px solid var(--border);
  }

  .tl-dot.filled {
    background: var(--accent);
    border-color: var(--accent);
  }

  .tl-line {
    width: 1px;
    flex: 1;
    background: var(--border);
    margin-top: 6px;
  }

  .tl-period {
    font-size: 0.75rem;
    line-height: 1.6;
    font-weight: 500;
    color: var(--fg-faded);
    padding-top: 2px;
  }

  .tl-body {
    display: flex;
    flex-direction: column;
    gap: 0.375rem;
    padding-bottom: 2.5rem;
  }

  .tl-body.last {
    padding-bottom: 0;
  }

  .tl-body h3 {
    font-size: 1.0625rem;
    line-height: 1.3;
    font-weight: 700;
  }

  .tl-org {
    font-size: 0.8125rem;
    font-weight: 600;
    color: var(--accent);
  }

  .tl-body p {
    font-size: 0.8125rem;
    line-height: 1.65;
    color: var(--fg-muted);
  }

  /* ---------- Contact ---------- */
  #contact .section-head h2,
  #contact .contact-lede {
    color: var(--term-fg);
  }

  .contact-lede {
    margin-block: 1.5rem;
    max-width: 620px;
    font-size: 0.9rem;
    line-height: 1.75;
    color: var(--term-muted);
  }

  .term-footer {
    display: flex;
    align-items: center;
    gap: 1.125rem;
    flex-wrap: wrap;
    margin-top: 2.25rem;
    padding-top: 1.5rem;
    border-top: 1px solid var(--term-border);
    font-size: 0.6875rem;
    font-weight: 500;
    color: var(--term-faded);
  }

  .term-footer .ok {
    color: var(--ok-fg);
  }

  .term-footer a {
    border-bottom: 1px solid var(--term-ghost-border);
    transition: color 0.15s ease;
  }

  .term-footer a:hover {
    color: var(--accent-bright);
  }

  .term-footer .exit {
    margin-left: auto;
  }

  /* ---------- Responsive ---------- */
  @media (max-width: 720px) {
    .hero-inner {
      grid-template-columns: minmax(0, 1fr);
    }

    .gutter-lines {
      display: none;
    }

    .hero-content {
      padding-left: 0;
    }

    .tl-row {
      grid-template-columns: 24px minmax(0, 1fr);
      gap: 0 1rem;
    }

    .tl-rail {
      grid-row: 1 / span 2;
    }

    .tl-period {
      grid-column: 2;
      padding-bottom: 0.25rem;
    }

    .tl-body {
      grid-column: 2;
    }

    .btn {
      flex: 1 1 100%;
    }

    .term-footer .exit {
      margin-left: 0;
    }
  }
</style>
