# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # Dev server at http://localhost:4321 (hot reload)
npm run build     # Static build to ./dist/
npm run preview   # Preview ./dist/ locally
```

No test suite exists — this is a static portfolio site.

## Architecture

Single-page Astro 6 site (`src/pages/index.astro`) that composes section components in order: Navbar → Hero → About → Skills → Experience → Projects → Education → Contact → Footer. The base HTML shell lives in `src/layouts/Layout.astro` (loads Inter font, sets scroll-smooth).

Tailwind CSS 4 is wired via `@tailwindcss/vite` (not the legacy `@astrojs/tailwind` integration) — the entry point is `src/styles/global.css` imported in Layout.astro.

All interactivity (mobile hamburger, scroll-based Navbar styling, scroll-reveal animations) is vanilla JavaScript inside `<script>` tags within each `.astro` component. There is no JS framework — Astro ships zero client-side JS by default.

## Styling Conventions

- Global animation: `animate-fade-up` class + `IntersectionObserver` triggers reveal on scroll — each component manages its own observer.
- Section layouts use `max-w-6xl mx-auto px-6` as the standard container.
- Color scheme: slate for neutrals, blue-600/700 for primary actions, with per-section accent colors (violet, emerald, orange, sky, teal, rose).

## Content

All portfolio content (bio, skills, projects, experience, education) is hardcoded directly in the component `.astro` files — there is no CMS or data layer. To update content, edit the relevant component in `src/components/`.

The CV PDF is at `public/Luis David Oropeza Cordova - CV.pdf` and is linked directly from `Hero.astro`.
