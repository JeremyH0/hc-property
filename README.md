# The Karuizawa Estate — Hirafu Capital GK

One-page property showcase site for a private luxury estate in Karuizawa, Nagano, Japan.

**Status: prototype** — English only. Contact form is UI-only (no backend yet). JP/ZH translations deferred until the English version is final.

## Tech

- [Astro](https://astro.build) (static site)
- Tailwind CSS 4 (via `@tailwindcss/vite`)
- Lenis smooth scroll
- Fonts: Cormorant Garamond (serif) + Plus Jakarta Sans (sans)

## Commands

| Command | Action |
| :-- | :-- |
| `npm install` | Install dependencies |
| `npm run dev` | Dev server at `localhost:4321` |
| `npm run build` | Production build to `./dist/` |
| `npm run preview` | Preview the build locally |

## Structure

- `src/pages/index.astro` — the entire landing page (sections, lightbox, gallery, form)
- `src/layouts/Layout.astro` — head, fonts, preloader, Lenis, custom cursor, scroll reveals
- `src/components/` — `Navigation`, `Footer`, `Carousel3D`
- `src/assets/gallery/` — images used on the page; `unused/` holds the spare image pool (not bundled)

See `CLAUDE.md` for the design system and detailed architecture notes.
