# Architecture

## Tech Stack
- **Framework**: [Astro](https://astro.build/) (Static Site Generator)
- **Content**: [MDX](https://mdxjs.com/) (Markdown + JSX)
- **Hosting**: [Cloudflare Workers](https://workers.cloudflare.com/)
- **Domain**: surfdweller.org

## Design System
- **Theme**: Blue on Gray background.
- **Typography**: [Comfortaa](https://fonts.google.com/specimen/Comfortaa) for logo and headings.
- **Visuals**: Rotating background images (Beachside/Roadside) with a 1.5s fade transition every 8 seconds.

## File Structure
- `src/layouts/`: Core page templates and background rotation logic.
- `src/pages/`: Site routes and MDX content pages.
- `public/images/`: Static assets (logos, backgrounds).
