# How To Update

## Local Development
1. Install dependencies:
   ```bash
   npm install
   ```
2. Start development server:
   ```bash
   npm run dev
   ```

## Deployment
The site is designed to be deployed via Cloudflare Workers/Pages.
1. Build the project:
   ```bash
   npm run build
   ```
2. Deploy to Cloudflare using `wrangler`.

## Content Updates
To add new pages or content, create `.mdx` files within the `src/pages/` directory.
