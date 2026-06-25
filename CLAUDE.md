# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the public-facing website for the **2026 National Survey of Community Rehabilitation Providers (CRP)**, a research project by the Institute for Community Inclusion (ICI) at UMass Boston in partnership with ANCOR. It describes the three-study research project and links to the Qualtrics survey.

## Commands

```sh
npm run dev       # Start local dev server at localhost:4321
npm run build     # Build production site to ./dist/
npm run preview   # Preview the production build locally
```

There are no tests or linting scripts configured.

## Architecture

Single-page Astro site. The entire page content lives in `src/components/Welcome.astro` — this is the main working file. `src/layouts/Layout.astro` is the shell: it loads Bootstrap 5.3 from CDN, imports `src/assets/styles/ici.css`, and renders the CRP/ANCOR header logos before yielding to `<slot />`.

**Key design constraints:**
- Styling uses Bootstrap 5 utility classes plus ICI-branded CSS variables defined in `ici.css` (e.g., `--ici-blue`, `--ici-purple`). Custom utility classes like `.bg_ici_lightgrey`, `.boxed`, `.boxer`, `.row-striped`, `.border-bottom-animate`, and `.reveal` (entrance animation) are all in `ici.css`.
- The `<body>` has a blue border effect via `padding: 1em` on `body` + white `.wrapper` div — it is not a real border.

**Redirects** (`public/_redirects` — Netlify syntax):
- `/faqs` → DD Agencies fact sheet PDF
- `/crpfaqs` → General fact sheet PDF
- `/respond` → Qualtrics survey URL

Images are in `src/assets/img/` (processed by Astro's `<Image>` component) and PDFs are in `public/pdfs/` (served as static assets).
