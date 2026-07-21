# Hirafu Capital GK - Karuizawa Property Showcase

## 🛠 Tech Stack
*   **Framework:** Astro (Static Site Generation)
*   **Styling:** Tailwind CSS
*   **Animations:** CSS Transitions (hardware-accelerated) + Lenis smooth scroll — no GSAP
*   **Fonts:** 
    *   Headings/Serif: Cormorant Garamond (`font-serif`)
    *   Body/Sans: Plus Jakarta Sans (`font-sans`)
*   **Deployment:** Vercel

## 🎨 Design System & Rules
Maintain a flat, clean, and modern aesthetic. **Strictly avoid heavy box-shadows or borders.**

*   **Global Background:** `#F4F4F5` (Tailwind `zinc-100` equivalent, custom-coded in CSS). This is the primary color of the entire website.
*   **Hero & Lightbox Overlays (Darkest):** `zinc-950` and `zinc-900`. Used for the hero background, image gradients, and the fullscreen lightbox to ground the site without feeling heavy.
*   **Primary Text & Buttons:** `zinc-800`. Used for main headings, button backgrounds, and form labels.
*   **Secondary Text:** `zinc-500`. Used for body paragraphs, providing a soft contrast that is easy to read.
*   **Subtle Accents & Borders:** 
    *   `zinc-400` (small caps/subtitles)
    *   `zinc-300` (form borders)
    *   `zinc-200` (section dividers and map placeholder)
*   **Card/Image Backgrounds:** `zinc-50` and `stone-50`. Used slightly off-white behind gallery thumbnails and floorplans to separate them from the main background.
*   **Typography Formatting:** Ensure all text has room to breathe. Always use `tracking-widest` for small caps and `leading-loose` for body paragraphs.

## 🏗 Project Architecture & Completed Implementations

### 1. Global Layout & Core (`src/layouts/Layout.astro`)
*   **Smooth Scrolling:** Integrated `@studio-freight/lenis` for high-performance smooth scrolling across the site.
*   **Preloader:** A custom, elegant typographic preloader that holds the scroll state, fades out, and triggers the hero animations.
*   **Custom Cursor:** A mix-blend-difference dot cursor for desktop users that scales up when hovering over interactable elements (`a, button, input, textarea, .floorplan-trigger, .gallery-thumb, #menu-toggle`).
*   **Hardware-Accelerated Reveals:** Utilizes `IntersectionObserver` targeting `.reveal-el` and `.hero-reveal` classes for buttery smooth fade-up animations.

### 2. Navigation (`src/components/Navigation.astro`)
*   **Smart Header:** A minimalist fixed header that transitions between transparent/white text (over the hero) and dark text (`zinc-800`/`zinc-500`) when scrolled past the hero section or when the mobile menu is open.
*   **Mobile Menu:** Fullscreen overlay menu with staggered animation for links using cubic-bezier easing, locking the Lenis scroll while active.
*   **Localization Structure:** Language dropdowns (EN, JP, ZH) are built-in, alongside a foundational auto-redirect script (currently commented out) based on the user's browser language.

### 3. Components
*   **`Carousel3D.astro`:** A highly modular, touch-friendly image carousel component. It supports swipe gestures, next/prev buttons, and dot indicators. It generates a unique `data-carousel-id` to sync bidirectionally with the global Lightbox engine.
*   **`Footer.astro`:** A minimal, elegant footer displaying the property context (Karuizawa) and current year copyright.

### 4. Main Page Structure (`src/pages/index.astro`)
The main landing page is fully constructed with the following sections:
*   **Hero:** Full-viewport height with a high-quality background (`imgHeroHQ`), a gradient overlay, and a custom vertical scroll indicator.
*   **Concept & Architecture:** Uses `Carousel3D` alongside elegant typography to showcase the Motor Court, Indoor Living, Accommodations, Wellness/Spa, and Grounds.
*   **Floorplans:** Sticky-scroll layout displaying the first and second-floor plans. Hovering reveals a "View Floorplan" CTA that ties into the Lightbox.
*   **Gallery:** A dual-mode gallery feature. Mobile displays a horizontal snap-scroll track with a custom blur mask, while desktop utilizes an asymmetrical grid.
*   **Overview / Map:** Structured property details list and an integrated Google Map iframe with a grayscale-to-color hover effect.
*   **Inquiry Form:** A minimal contact form featuring custom-styled inputs (bottom borders only) and a built-in success message toggle. **PROTOTYPE: the submit handler only simulates sending (setTimeout) — no backend/email is wired up yet.**

## 📋 Project Status & Pending Work
*   **Prototype stage** — English one-page site only.
*   **Contact form:** needs a real endpoint/email once the destination address exists.
*   **Localization (JP/ZH):** intentionally deferred until the English version is final. Nav language links are placeholders; auto-redirect script is commented out in `Navigation.astro`.
*   **Unused images** live in `src/assets/gallery/unused/` — kept as a pool for future gallery updates; Astro does not bundle them.
*   **Unified Lightbox Engine:** A robust, custom-built fullscreen lightbox at the bottom of the file that seamlessly handles triggers from the Gallery, the Floorplans, and the Carousels, supporting captions and bidirectional syncing.