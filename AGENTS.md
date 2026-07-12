# AGENTS.md

Guidance for AI coding agents working in this repository.

## Project overview

This is a self-contained personal/professional GitHub Pages site for Ai-Hsien Adams Li, MD, PhD, MPH. There is no framework, build step, package manager, or dependency installation required.

## Repository layout

- `index.html` — the complete single-page website, with inline CSS in `<head>` and inline JavaScript at the bottom.
- `photo.jpg` — hero avatar image used by `index.html`.
- `README.md` — short project and verification notes.
- `CLAUDE.md` — additional Claude-oriented repository notes.

## Editing conventions

- Keep the site self-contained: avoid adding external CSS/JS frameworks, CDNs, or build tooling unless explicitly requested.
- Add new CSS to the existing `<style>` block and new JavaScript to the existing `<script>` block.
- Preserve the established visual palette: navy `#1a3a5c`, mid-blue `#2d6a9f`, light blue `#4a9edd`, and gold accent `#f0c040`.
- Preserve the UTF-8 BOM in `index.html` when rewriting it.
- Prefer small, static-site-friendly performance improvements: semantic HTML, explicit media dimensions, compressed local assets, and graceful degradation for network-dependent widgets.

## Verification

Before committing changes, run at least:

```bash
python3 -c "from html.parser import HTMLParser; HTMLParser().feed(open('index.html', encoding='utf-8-sig').read())"
```

For visual changes, serve the site locally and inspect it in a browser or headless Chromium:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` or capture a screenshot with the available headless browser.
