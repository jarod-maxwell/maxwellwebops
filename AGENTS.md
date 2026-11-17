## Development

When starting the dev server, use background mode:

```
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`.

## Documentation

Full documentation: https://docs.astro.build

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using React, Vue, Svelte, or other framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
- [Supporting multiple languages](https://docs.astro.build/en/guides/internationalization/)

## Business & Brand Positioning

- **Brand:** Maxwell Web Ops (`maxwellwebops.com`)
- **Founder / Operator:** Jarod Maxwell
- **Location:** Fort Wayne, Indiana (serving Fort Wayne and Northeast Indiana small businesses)
- **Core Services:**
  1. Small business web hosting, domain administration, and DNS management
  2. Google Workspace administration and email deliverability (SPF, DKIM, DMARC)
  3. Local directory management and Google Business Profile optimization
  4. Data hygiene, metadata/taxonomy structuring, and smart lead capture workflows
- **Tone & Voice:** Direct, practical, calm, and technically credible. Avoid agency buzzwords ("synergy", "10x", "disruptive", "revolutionary"). Explain technical value in plain English for local business owners.

## Tech Stack & Architecture

- **Framework:** Astro (static output by default; zero client-side JS unless explicitly justified)
- **Hosting:** Cloudflare Pages (`npm run build` -> `dist/`)
- **Styling:** Semantic HTML5 + vanilla CSS with CSS custom properties (`src/styles/global.css`) and component-scoped `<style>` blocks. Do not add Tailwind or heavy CSS frameworks unless explicitly requested.
- **Directory Structure:**
  - `src/layouts/` — Page wrappers (`BaseLayout.astro`)
  - `src/components/` — Reusable UI components (`Navbar.astro`, `Footer.astro`, `ServiceCard.astro`)
  - `src/pages/` — File-based routes
  - `src/styles/` — Global design tokens and base resets
  - `public/` — Static assets (`favicon.svg`, `robots.txt`, Open Graph images)

## Code, SEO & Accessibility Standards

- **HTML & Accessibility:** Use strict semantic landmarks (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`), proper heading hierarchy (one `<h1>` per page), descriptive `alt` text, and high-contrast, keyboard-accessible focus states.
- **Structured Data:** Every page using `BaseLayout.astro` must include valid JSON-LD schema (`LocalBusiness` / `ProfessionalService`) in the `<head>` and complete `<title>`, `<meta name="description">`, canonical URL, and Open Graph tags.
- **Performance:** Keep pages lightweight, use modern image formats (`webp`/`avif`) with explicit `width` and `height`, and avoid unnecessary third-party scripts or trackers.
- **Safe Edits:** Keep components small and single-purpose. Do not modify `BaseLayout.astro` global tokens or schema blocks when making localized page-copy updates.