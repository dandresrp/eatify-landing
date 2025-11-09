# Eatify Landing - AI Coding Agent Instructions

## Project Overview

This is an **Astro 5.x** static site landing page using **Tailwind CSS v4** (via Vite plugin). The project follows Astro's basics template structure with TypeScript strict mode enabled.

## Tech Stack & Architecture

- **Framework**: Astro 5.15.4 (static site generation)
- **Styling**: Tailwind CSS v4.1.17 via `@tailwindcss/vite` plugin
- **Package Manager**: pnpm (check `pnpm-lock.yaml` exists, always use pnpm)
- **TypeScript**: Strict mode (`extends: "astro/tsconfigs/strict"`)
- **Build Output**: `./dist/` directory

## Key Patterns & Conventions

### Component Structure

- **Layouts**: Place in `src/layouts/` - see `Layout.astro` for the base HTML shell
- **Components**: Place in `src/components/` - see `Welcome.astro` for reference
- **Pages**: Place in `src/pages/` - file-based routing (index.astro = homepage)
- **Static Assets**: SVGs and images in `src/assets/` (processed by Astro) vs `public/` (copied as-is)

### Styling Approach

- **Tailwind v4 import**: Use `@import "tailwindcss";` in CSS files (see `src/styles/global.css`)
- **Scoped styles**: Prefer `<style>` blocks in `.astro` components for component-specific CSS
- **No separate config**: Tailwind v4 uses CSS-based configuration, no `tailwind.config.js` needed

### Astro Component Syntax

```astro
---
// Component script (runs at build time)
import Component from '../components/Component.astro';
---

<!-- Template with scoped styles -->
<div>Content</div>

<style>
  /* Scoped by default */
</style>
```

## Developer Workflows

### Essential Commands

```bash
pnpm dev          # Dev server at localhost:4321
pnpm build        # Production build to ./dist/
pnpm preview      # Preview production build locally
```

### Development Notes

- Dev server runs on **port 4321** by default
- Hot module replacement (HMR) works for `.astro`, CSS, and imported assets
- TypeScript files are type-checked but not transformed (Astro handles this)

## Configuration Files

- **`astro.config.mjs`**: Astro config with Tailwind Vite plugin integration
- **`tsconfig.json`**: Extends Astro's strict TypeScript preset
- **`package.json`**: Type is "module" - use ESM imports everywhere

## Project-Specific Guidelines

1. **Import paths**: Use relative imports (`../components/`) not aliases (no path mapping configured)
2. **Static assets**: Import SVGs/images from `src/assets/` for optimization, or use `public/` for direct serving
3. **Tailwind v4**: Import via CSS, not as a PostCSS plugin - see Vite plugin in `astro.config.mjs`
4. **Layout pattern**: Use `<slot />` in layouts (see `Layout.astro`) to render page content
5. **No framework UI**: Pure Astro components, no React/Vue/Svelte integrations currently enabled
