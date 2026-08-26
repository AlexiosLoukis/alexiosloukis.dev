# alexiosloukis.dev

Source for my personal site — a short profile of what I work with, what I'm
currently learning, and the projects behind those claims.

**Live:** [alexiosloukis.dev](https://alexiosloukis.dev)

## Stack

| Layer | Choice | Why |
|---|---|---|
| Framework | [Astro](https://astro.build) | Content site, not an application. Astro ships static HTML with no client-side JavaScript by default. |
| Styling | Plain CSS, custom properties | No build step, no framework to learn, no unused utility classes shipped to the browser. |
| Hosting | GitHub Pages | Free static hosting, deployed straight from this repository. |
| DNS & TLS | Cloudflare | DNS management; `.dev` is on the HSTS preload list, so HTTPS is enforced by the browser. |
| CI/CD | GitHub Actions | Builds and deploys on every push to `main`. |

## Local development

```bash
npm install      # install dependencies
npm run dev      # dev server on http://localhost:4321
npm run build    # production build into dist/
npm run preview  # serve the production build locally
```

Requires Node.js (LTS).

## Structure

```
src/
  layouts/Base.astro    shared <head>, fonts and global styles
  pages/                one file per route (file-based routing)
public/                 served as-is: cv.pdf, favicon
astro.config.mjs        site URL, used for canonical links
```

Pages are routed by file path: `src/pages/index.astro` serves `/`,
`src/pages/about.astro` serves `/about`.

## Deployment

Pushing to `main` triggers a GitHub Actions workflow that builds the site and
publishes `dist/` to GitHub Pages. The build output is not committed —
`dist/` and `node_modules/` are generated artifacts and stay out of version
control.

## License

Code is MIT. Content and CV are not.
