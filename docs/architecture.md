# Architecture — Surf Dweller Web

## Overview

Surf Dweller Web is a static marketing site for the **Surf Dweller Condominium** on Florida's Emerald Coast. It is built with Astro and deployed as a Cloudflare Worker with Static Assets.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Framework** | [Astro](https://astro.build/) v4 (Static Site Generator) |
| **Content** | [MDX](https://mdxjs.com/) (Markdown + JSX) via `@astrojs/mdx` |
| **UI Runtime** | React 18 (for any interactive components) |
| **Hosting** | [Cloudflare Workers](https://workers.cloudflare.com/) + Workers Static Assets |
| **Fonts** | Google Fonts — Comfortaa (loaded via `fonts.googleapis.com`) |

## Design System

- **Theme**: Blue accent on gray background (`#333` body, `#007bff` links/buttons)
- **Typography**: Comfortaa (variable weight 300–700) from Google Fonts
- **Visuals**: Two rotating background images (`SD_beachside.jpg`, `SD_roadside.jpg`) with 1.5s CSS fade transitions, cycling every 8 seconds
- **Favicon**: PNG file (`favicon.png`) — the 🏖️ emoji, used for cross-browser compatibility (Safari on macOS does not reliably render emoji inside inline SVG `<text>` nodes)

## File Structure

```
surf-dweller-web/
├── astro.config.mjs          # Astro config (MDX integration, Vite allowedHosts)
├── package.json              # Dependencies: astro ^4.0, @astrojs/mdx ^3.0, react ^18
├── public/
│   ├── favicon.png           # Site favicon (emoji PNG)
│   └── images/
│       ├── SD_beachside.jpg  # Background image 1
│       └── SD_roadside.jpg   # Background image 2
├── src/
│   ├── layouts/
│   │   └── Layout.astro      # Root layout: HTML head, background rotation script, styles
│   └── pages/
│       └── index.astro       # Home page (hero section, logo, CTA link)
└── dist/                     # Build output (static files for Workers deployment)
    ├── index.html
    └── images/
```

## Key Components

### Layout (`src/layouts/Layout.astro`)

- Serves as the root HTML template for all pages
- Defines inline CSS for body, background images, content container, logo, and CTA button
- Background rotation is handled by a client-side `<script>` that toggles `.active` class on `.bg-image` divs every 8 seconds
- The `<head>` section includes meta tags, Google Fonts preconnect links, and the favicon link

### Home Page (`src/pages/index.astro`)

- Single-page layout with:
  - Logo image (centered, responsive width)
  - Heading: "SURF DWELLER CONDOMINIUM"
  - Tagline: "Your home on the Emerald Coast"
  - Address (clickable link opening maps)
  - CTA button linking to the portal

## Deployment Model

The site is a **static build** (`astro build`) that produces a `dist/` directory of HTML, CSS, JS, and image files. This output is deployed to Cloudflare Workers as a **Static Assets** Worker — no server-side rendering, no API routes. The Workers runtime simply serves the pre-built files with Cloudflare's edge CDN caching.

## Security & Privacy Notes

- No user data collection or analytics
- No API keys, secrets, or credentials in the codebase
- Background images are static assets served from Cloudflare's edge
- Google Fonts is loaded from `fonts.googleapis.com` — no local font hosting
