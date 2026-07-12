# MasterAdams.github.io

Personal professional website for Ai-Hsien Adams Li, MD, PhD, MPH, hosted with GitHub Pages.

## Local preview

This is a static, dependency-free site. Preview it from the repository root with:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Verification

Run a lightweight HTML parser check before committing:

```bash
python3 -c "from html.parser import HTMLParser; HTMLParser().feed(open('index.html', encoding='utf-8-sig').read())"
```
