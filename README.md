# Portfolio personnel

Code source de mon site portfolio. Construit avec SvelteKit, déployé automatiquement sur GitHub Pages via GitHub Actions à chaque push sur `main`.

🌐 **Site en ligne :** [sebvietsky.github.io](https://sebvietsky.github.io)

---

## Stack

- **SvelteKit** (mode statique, adapter `@sveltejs/adapter-static`)
- **TypeScript**
- **CSS pur** avec variables custom — pas de framework UI
- **Google Fonts** (Fraunces, Manrope, JetBrains Mono)
- **GitHub Actions** pour le déploiement continu
- **GitHub Pages** pour l'hébergement

Aucune dépendance JavaScript runtime côté client : le site est entièrement pré-rendu au build, ce qui le rend rapide et sans dépendance à un serveur Node.

---

## Lancer en local

Prérequis : Node.js 20+ et npm.

```bash
npm install
npm run dev
```

Le site est servi sur `http://localhost:5173` avec hot-reload.

---

## Build et déploiement

```bash
npm run build      # génère le dossier build/
npm run preview    # sert le build en local pour vérification
```

---

## Structure du projet

```
.
├── src/
│   ├── app.css                # design tokens, reset, utilitaires, animations
│   ├── app.html               # template HTML, meta SEO et Open Graph
│   └── routes/
│       ├── +layout.svelte     # nav, footer, animations globales (scroll, reveal)
│       ├── +layout.ts         # active le prerendering pour tout le site
│       └── +page.svelte       # contenu du portfolio (sections + styles)
├── static/                    # assets servis tels quels (favicons, OG, CV)
│   ├── favicon.svg
│   ├── favicon-32.png
│   ├── apple-touch-icon.png
│   ├── og-image.png
│   └── cv-sebastien-fabie.pdf
├── .github/workflows/
│   └── deploy.yml             # CI/CD vers GitHub Pages
└── svelte.config.js           # configuration de l'adapter static
```

---

## Choix techniques

Quelques décisions notables, pour celles et ceux qui se demanderaient pourquoi tel ou tel choix :

- **SvelteKit plutôt que du HTML pur** : cohérence avec ma stack (j'utilise Svelte sur d'autres projets), single source of truth pour le routing, et adapter static qui produit un site équivalent à du HTML pur côté performance.
- **Pas de framework CSS** : le portfolio est suffisamment petit pour que Tailwind soit un overkill. Les variables CSS et un peu de discipline suffisent largement.
- **Animations en CSS pur + IntersectionObserver** : pas de bibliothèque d'animation. Tout tient en ~100 lignes de CSS et ~30 lignes de JS, et c'est plus performant que GSAP ou Motion sur ce volume.

---

## Licence

Le **code** est distribué sous licence MIT — n'hésite pas à t'en inspirer pour ton propre portfolio.

Le **contenu** (textes, biographie, expériences professionnelles, projets, photos) reste personnel et ne peut être réutilisé.
