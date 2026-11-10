# Paethrus

Placeholder static Italian site (`lang="it"`, "prossimamente") built with `@minimaz/sitekit`. A single `index.html`, no JS, no forms, no JSON-LD, no CSP.

## Commands

```bash
npm run build          # mz b --overwrite
npm start              # build, then serve ./dist
npm run format         # prettier --write .
npm run format:check   # also the Husky pre-commit hook
npm run lint           # htmlhint + stylelint + cspell; also lint:a11y, lint:links (build first)
```

No tests. The pre-commit hook runs `format:check` and the three lints; add legitimate names to `cspell.json` `words` rather than editing copy. Node `24.22.2` per `.nvmrc`; `engines` is `>=24` with `engine-strict=true`.

## Structure

- `src/pages/index.html` is the only page. `src/style.css` is the bundle entry, `src/styles/*.css` one concern per file (new stylesheets must be `@import`ed there).
- `src/public/`: `robots.txt` (blocks AI crawlers), `sitemap.xml` (one URL), `.well-known/security.txt`, `favicon.ico`.

bootstrap-icons is self-hosted only (`styles/bootstrap-icons.css` + the `externals` font copy); don't add a CDN link.

## Deploy

Push to `main` builds and rsyncs `dist/` to production over SSH (`.github/workflows/deploy.yml`), no staging. Work happens on `develop`. CI reads the Node version from `.nvmrc`.

## Scope

@SCOPE.md
