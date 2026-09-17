# Ezana AI — website

The marketing site for **Ezana AI**: an ontology-first AI engine for enterprise workflow
automation, deployed with controls, compliance and audit trails.

A statically generated Nuxt 3 site. All copy lives in one JSON file, so the content can be
edited without touching a component.

## Stack

| Layer | Choice |
|---|---|
| Framework | [Nuxt](https://nuxt.com/) 3 + Vue 3 |
| Styling | [Tailwind CSS](https://tailwindcss.com/) v4, via `@tailwindcss/vite` |
| Icons | inline SVG (`components/Glyph.vue`) — no runtime icon fetch |
| Fonts | Inter + IBM Plex Mono, from Google Fonts |
| Hosting | Netlify, prerendered by `nuxt generate` |

## Build setup

Requires [Node.js](https://nodejs.org/) v20.9+.

```bash
npm install      # install dependencies
npm run dev      # hot reload at localhost:3000
npm run generate # prerender the static site to .output/public
npm run preview  # preview the production build locally
```

## Editing the content

Everything the visitor reads is in [`data/index.json`](data/index.json), keyed by section:

| Key | Section |
|---|---|
| `company` | name, tagline, contact address |
| `hero` | headline, lede, buttons, the three assurances under them |
| `principles` | the "non-negotiables" strip |
| `platform` | the six capability cards (`glyph` names a key in `Glyph.vue`) |
| `pipeline` | the five stages of how the engine runs |
| `caseStudies` | one entry per case study — situation, what was deployed, what changed, stack |
| `assurance` | the four reviewer columns (risk, compliance, audit, security) |
| `cta`, `nav`, `footer` | call to action, navigation, footer |

`pages/index.vue` passes those objects to the components; no copy is hard-coded in a
component except the illustrative execution record in `components/TracePanel.vue`.

## Design system

Colour, type and texture are defined once as Tailwind theme tokens in
[`assets/css/main.css`](assets/css/main.css):

- `ink-*` — near-black cool surfaces
- `mist-*` — text, from primary (`100`) to faintest (`500`)
- `brass-*` — the accent
- `grid-field` / `eyebrow` — the blueprint backdrop and the mono section labels

Change a token there and it propagates across the site.

## Project structure

```
├── data/index.json   # every word on the site
├── components/       # Vue components, one per section + shared primitives
├── layouts/          # navbar + footer shell
├── pages/            # the single page
├── assets/css/       # Tailwind theme tokens and base styles
└── public/           # favicon
```

## Deploying

Netlify is configured in [`netlify.toml`](netlify.toml): it runs `npm run generate` and
publishes the prerendered output. Pushing to `main` is enough.
