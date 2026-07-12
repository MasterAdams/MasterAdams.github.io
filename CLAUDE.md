# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What this is

Personal/professional website for Ai-Hsien Adams Li, MD, PhD, MPH, hosted on
GitHub Pages. The site deploys automatically from the `main` branch — there is
no build step, no framework, no package manager, and no dependencies to install.

## Repository layout

- `index.html` — the entire site: one self-contained page with inline CSS in
  `<head>` and inline JavaScript at the bottom (`<script>` starts near line 750).
- `photo.jpg` — the hero avatar image.
- `README.md` — one-line description.

## Page structure

Content sections in `index.html`, anchored by the sticky nav:
`#about`, `#current`, `#education`, `#experience`, `#research`, `#plans`,
`#publications`, `#news`, `#contact`.

Inline JavaScript provides two dynamic features:
1. **Monday countdown** — fills `#next-monday-text` with days until the next
   Monday (the author's manual review day).
2. **Live news widget** — fetches biomedical RSS feeds (Google News, STAT,
   Medical News Today, ScienceDaily) into `#live-news-container`, trying
   multiple public CORS proxies (rss2json, corsproxy.io, allorigins) in order.
   This is the page's only external runtime dependency; it degrades gracefully
   if all proxies fail.

## Conventions

- Keep the page self-contained: no external CSS/JS frameworks or CDNs unless
  explicitly requested. New styles go in the existing `<style>` block, new
  scripts in the existing `<script>` block.
- Match the existing style: Georgia serif body, Arial for nav/tags, and the
  established palette — navy `#1a3a5c`, mid-blue `#2d6a9f`, light blue
  `#4a9edd`, gold accent `#f0c040`.
- The file is saved with a UTF-8 BOM; preserve it when rewriting the file.

## Previewing and verifying changes

There is no test suite; verification means rendering the page.

1. Serve locally: `python3 -m http.server 8000` (from the repo root), then open
   `http://localhost:8000`. In remote/headless sessions, screenshot with the
   pre-installed headless Chromium instead:
   ```
   find /opt/pw-browsers -name headless_shell | head -1
   <that-binary> --headless --no-sandbox --window-size=1280,2000 \
     --screenshot=/tmp/preview.png --virtual-time-budget=8000 http://localhost:8000/
   ```
   then read the PNG to confirm the page renders.
2. Sanity-check the HTML parses (catches unclosed tags) before committing:
   `python3 -c "from html.parser import HTMLParser; HTMLParser().feed(open('index.html', encoding='utf-8-sig').read())"`
3. Check the browser console for JS errors if you touched the `<script>` block.
