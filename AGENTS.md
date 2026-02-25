# AGENTS.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

Static personal portfolio website for Zeeshan Ahmed (game developer). No build system, bundler, or package manager — just plain HTML, CSS, and vanilla JavaScript served directly from `index.html`.

## Running Locally

Open `index.html` directly in a browser, or use any local static file server:

```
python -m http.server 8000
```

There are no build, lint, or test commands.

## Architecture

### Single-page app structure

The site is a single `index.html` file that uses CSS class toggling (via `data-page` attributes) to switch between three page sections — **About**, **Resume**, and **Portfolio**. There is no client-side routing; navigation is handled in `assets/js/script.js` by matching navbar button text to `data-page` values on `<article>` elements.

### Key files

- `index.html` — All page content lives here. Sections are `<article>` elements with `data-page` attributes (`about`, `resume`, `portfolio`). A commented-out Blog section also exists.
- `assets/css/style.css` — All styling. Uses CSS custom properties defined in `:root` for colors, typography, shadows, and transitions. Dark theme with gold/yellow accent colors (`--orange-yellow-crayola`).
- `assets/js/script.js` — All interactivity: sidebar toggle, testimonials modal, portfolio category filter (via `data-filter-item` / `data-category`), contact form validation, page navigation, and resume PDF download.

### External dependencies (loaded via CDN)

- **Google Fonts**: Poppins (weights 300–600)
- **Ionicons 5.5.2**: icon system used throughout via `<ion-icon>` custom elements

### Images and assets

- `assets/images/` — SVG icons, avatar, logo, and per-project screenshot subdirectories (`UNiVerse/`, `SudoFighter/`, `FPS/`, `FliesKnockout/`, `SpaceShooter/`)
- `assets/resume/Zeeshan_Resume.pdf` — downloadable resume
- `website-demo-image/` — demo screenshot of the site

### Content conventions

Portfolio projects are added as `<li class="project-item">` elements inside `.project-list` in `index.html`. Each project item uses `data-filter-item` and `data-category` attributes for filtering, and contains a description block, tags, links (GitHub/video), and an image gallery.

### CSS note

The CSS file (~40KB) contains an original credit to `@codewithsadee`. The stylesheet uses a mobile-first approach with responsive breakpoints using `min-width` media queries. All styling uses the custom property system — when changing colors or typography, update the `:root` variables rather than individual rules.
