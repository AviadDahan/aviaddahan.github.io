# aviaddahan.com

Personal academic site for Aviad Dahan: a Jekyll site deployed to GitHub Pages.

## Hosting and monitoring
- Live at https://aviaddahan.com. The custom domain comes from `CNAME` and `url` in `_config.yml`. Don't delete either, and build absolute links on aviaddahan.com, not `*.github.io`.
- Deploys run through `.github/workflows/deploy.yml` on every push to `main`, building with `JEKYLL_ENV=production`. A push to `main` goes live.
- Cloudflare Web Analytics: the beacon is in `_layouts/default.html` inside `{% if jekyll.environment == "production" %}`. Keep it production-only.
- Google Search Console verification: `google3b13185b11d182c5.html` at the repo root. Don't remove it.

## Content
- The home page is `_pages/about.md` (layout `_layouts/about.html`). Publications are hand-written HTML blocks in that file, newest first, with thumbnails in `assets/img/publications/`.
- The scrolling organisation logos come from `_data/companies.yml`, rendered by `_includes/companies.html`, with logos in `assets/img/companies/`.
- Site metadata and social handles live in `_config.yml`.
- Styles: `assets/css/main.css`.
- `*.pdf` is gitignored, so the CV PDF isn't in the repo or on the live site.

## Design previews
- Design explorations go in `_design-previews/` as standalone HTML that references assets as `../assets/img/...`. The retro concepts start at `retro-index.html`. That folder, `preview.html` and `design-option-*.html` are excluded in `_config.yml`, so they never deploy.
- Any other new top-level file will deploy. Add it to `exclude` if it's a preview or tooling. `CLAUDE.md` is excluded too: Jekyll runs Liquid over Markdown files at the root, so a stray `{% %}` tag breaks the build.
- Preview locally with a static server from the repo root (`python3 -m http.server 8000`), then open `http://localhost:8000/_design-previews/<file>.html`. `jekyll serve` won't serve the excluded folder.

## Local build
`bundle exec jekyll serve` (Gemfile uses `github-pages`).
