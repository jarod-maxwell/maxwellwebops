# AGENTS.md — Maxwell Web Ops

## Project Overview
- **Business Name:** Maxwell Web Ops
- **Operator:** Jarod Maxwell
- **Location:** Fort Wayne, Indiana (serving Fort Wayne & Northeast Indiana)
- **Production URL:** `https://maxwellwebops.com`
- **Repository:** `github.com/jarod-maxwell/maxwellwebops` (branch: `main`)

## Architecture & Infrastructure
- **Framework:** Astro (Static Site Generation / SSG)
- **Hosting & CI/CD:** Cloudflare Pages (`npm run build` -> `dist/`), auto-deploying on push to `main`
- **Registrar & DNS:** Registered at Namecheap; nameservers delegated to Cloudflare
- **Canonical Routing:**
  - `https://maxwellwebops.com` serves the primary site via Cloudflare Pages custom domain
  - `www.maxwellwebops.com` has a proxied `A` record (`192.0.2.1`) with a Cloudflare 301 Redirect Rule (`concat("https://maxwellwebops.com", http.request.uri.path)`)
- **Email & Authentication:**
  - Google Workspace Business Standard (`jarod@maxwellwebops.com`)
  - MX routed to `smtp.google.com`; SPF (`v=spf1 include:_spf.google.com ~all`), 2048-bit DKIM (`google._domainkey`), and DMARC (`v=DMARC1; p=none; rua=mailto:jarod@maxwellwebops.com`) configured and passing
- **Contact Form & Booking:** Web3Forms HTML endpoint in `src/pages/contact.astro` (using honeypot field `botcheck`), redirecting to `src/pages/thanks.astro` with embedded Cal.com scheduling

## Codebase Conventions
- **Styling:** Semantic HTML5, shared layout/button utility classes (`.container`, `.section`, `.section-alt`, `.section-header`, `.page-header`, `.eyebrow`, `.page-lead`, `.cta-box`, `.btn`) and CSS custom properties in `src/styles/global.css`, paired with route-specific scoped Astro `<style>` blocks. Do NOT introduce Tailwind CSS, Bootstrap, or client-side JS frameworks (React/Vue/Svelte) unless explicitly requested.
- **Directory Structure:**
  - `src/layouts/BaseLayout.astro`: Global HTML shell, `<head>` metadata, JSON-LD `LocalBusiness` schema, sticky header/footer wrapper
  - `src/components/`: Reusable UI modules (`Navbar.astro`, `Footer.astro`, `ServiceCard.astro`)
  - `src/pages/`:
    - `index.astro` — Hero, 2×2 `ServiceCard` grid, 3-column operating principles, bottom CTA
    - `services.astro` — Detailed service breakdowns with anchor `#id`s + 3 engagement models
    - `about.astro` — Founder background, Practice Snapshot sidebar, 3 operating standards
    - `contact.astro` — Structured intake form + "What Happens Next" sidebar
    - `thanks.astro` — Post-submission confirmation page with embedded Cal.com booking
- **Layout Breakpoints:**
  - 4-card service grid uses a 2×2 layout (`repeat(2, minmax(0, 1fr))`), collapsing to 1 column at `max-width: 44rem`
  - 3-column principles/standards grids use `repeat(3, minmax(0, 1fr))`, collapsing to 1 column at `max-width: 48rem` / `52rem`

## Tone & Copy Guidelines
- Plain-English, practical, non-jargon communication aimed at Fort Wayne small business owners.
- Emphasize client ownership of domains/accounts, clean data/DNS hygiene, and zero agency bloat.
- Never reference `jaymax.co` or `jaymaxco` in commits, comments, or copy.