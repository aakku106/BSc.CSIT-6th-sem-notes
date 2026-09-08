# AGENTS.md

Eleventy 3 "Digital Garden" site (Obsidian Digital Garden template) publishing BSc.CSIT 6th-sem notes. Deployed to GitHub Pages on push to `main` via `.github/workflows/deploy.yml` (Node 22, `npm ci`, `npm run build`), served under path prefix `/BSc.CSIT-6th-sem-notes/`.

## Content lives only in `src/site/notes/`

- All published content is under `src/site/notes/`; subdirs mirror the Obsidian vault (`TW/`, `TW/Old_sets/`). Everything else in the tree (`src/helpers/`, `src/plugins/`, `src/site/*.njk`) is build/site code, not content.
- A note is published only when frontmatter contains `"dg-publish": true`. Notes use **single-line JSON frontmatter** (e.g. `{"dg-publish":true,"permalink":"/tw/syllabus/","tags":["syllabus","exam","tw"],...}`) — keep this shape, do not reformat to block YAML. `\|` must stay escaped inside strings; `src/helpers/matterOptions.js` strips it before YAML parse.
- `permalink:` in frontmatter sets the URL (trailing slash). The note tagged `gardenEntry` (`BSc.CSIT.md`) becomes the site home at `/`.
- `src/site/notes/README.md` is itself a published note (`/readme/`) describing the *Obsidian vault* — its layout tree does not match this repo.

## Links: the dead-link gotcha

`[[wikilinks]]`, `[[Page|Alias]]`, `[[Note#Heading]]`, and markdown relative `.md` links are resolved at build time to real permalinks. Links to vault files **not present** under `src/site/notes/` render as dead links pointing to `/404`. The repo currently holds all subject hubs plus their `Syllabus` and `Old_sets/` notes (CDC, DOTNET, E-Com, E-Gov, SE, TW), so those links resolve live. Only link to files that actually exist in `src/site/notes/`, or accept the intentional dead link (e.g. the `[[wikilinks]]` doc example in the published `README.md`).

## Commands

- `node_modules` is not committed — run `npm install` first (Node 22).
- `npm run dev` — Elleventy `--serve` + sass watch (dev env: no minify, no image optimization). Runs `get-theme` once at startup, which **fetches `THEME` from `.env` — needs network**.
- `npm run build` — full prod build: `get-theme` (network) → compressed sass + eleventy in parallel. Deliberately memory-heavy (`build:eleventy` sets `UV_THREADPOOL_SIZE=16`, `NODE_OPTIONS=--max-old-space-size=3072`). Output `dist/` (gitignored).
- `npm test` — `vitest run`; unit tests colocated in `src/helpers/*.test.js` and `src/helpers/__tests__/`. Covers helper logic only, never a full build.

## Site config & plugins (not content)

- `.env` is **tracked in git** and is the main config: `SITE_NAME_HEADER`, `SITE_BASE_URL`, `THEME`, `BASE_THEME`, per-feature flags (`dgHomeLink`, `dgShowToc`, `dgEnableSearch`, …). Per-note frontmatter overrides env defaults; there are no secrets committed.
- Feature plugins live in `src/plugins/` (`dg-search`, `dg-filetree`, `dg-link-preview`, `dg-timestamps`, `dg-math`). `src/site/_includes/plugins/` is **generated and gitignored** — edit plugin templates in `src/plugins/`, never the copies. Enable/disable via `src/plugins/plugins.json`.
- Build new plugins by following `skills/garden-plugin-author/SKILL.md` (also describes the existing plugin API).
- Custom styling: `src/site/styles/custom-style.scss`. A downloaded Obsidian theme is written to `src/site/styles/_theme.*.css` (gitignored).

## Build quirks

- HTML minification (with per-input caching in `.eleventy.js`) applies only in prod (`ELEVENTY_ENV=prod`).
- Markdown extensions: Obsidian callouts `> [!note]`, `ad-*` fenced callouts with `title:/icon:/collapse:/color:` metadata lines, plus `mermaid`, `transclusion`, `gist`, `plantuml` fences, and image width syntax `![[img.png|400]]`.
- Images become responsive `<picture>` (500/700 widths, webp/jpeg) unless `USE_FULL_RESOLUTION_IMAGES=true`; images sharp can't decode keep their original `<img>`.