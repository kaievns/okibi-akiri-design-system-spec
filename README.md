# Okibi 燠火 — Design Language

> おきび — *banked embers*, the coal that holds the fire.

The public reference site for **Okibi**, a design language built on one claim:
**a theme is an attention-allocation policy.** One charcoal spine, one ember,
a handful of quiet pigments — and code highlighting that engages only when you
do. Two grounds: **Okibi** (dark) and **Akari 灯り** (light).

**v1.8 · locked baseline** — generated from the Okibi design-system project;
tokens, spec, and exports are in sync at this version.

Served as a static **GitHub Pages** site — no framework, no build step, no
images. Everything is CSS and system/Google fonts.

## The site

- [`index.html`](index.html) — landing: the claim, the salience budget, the
  three-phase highlighting demo
- [`doctrine.html`](doctrine.html) · [`foundations.html`](foundations.html) ·
  [`code.html`](code.html) · [`markdown.html`](markdown.html) ·
  [`tools.html`](tools.html) · [`for-llms.html`](for-llms.html)
- [`llm-context.md`](llm-context.md) — the machine endpoint: hands an LLM the
  entire system as binding context (see also [`llms.txt`](llms.txt))

Supporting assets, everything the pages reference:

| Path | Purpose |
| --- | --- |
| `styles.css`, `tokens/` | the oklch token source (imported by every page) |
| `guidelines/` | foundation specimen cards, embedded on foundations/code/markdown pages |
| `components/` | component preview cards, embedded on the foundations page |
| `ui_kits/` | full-page templates: document, editor workbench, deck |
| `exports/` | grab-and-go artifacts: VS Code themes, Obsidian snippet, Prism/hljs CSS, terminal scheme, `okibi.tokens.json` |
| `spec/` | dynamic highlighting, static fallback, contrast matrix |
| `experiments/` | the phase transition machine (unsettled — not spec) |
| `SKILL.md` | agent skill wrapper for using the system elsewhere |

`favicon.svg` and `og-image.png` are the only binary assets;
[`.nojekyll`](.nojekyll) tells Pages to serve every path verbatim.

## Enable GitHub Pages

1. Push this repository to GitHub.
2. **Settings → Pages → Build and deployment → Source: _Deploy from a branch_.**
3. Branch: `main`, folder: `/ (root)`. Save.
4. The site goes live at `https://<user>.github.io/<repo>/` within a minute.

## Preview locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

---

OKIBI · 燠火 · 一つの背骨、一つの燠、注意こそ予算 · CC BY-NC 4.0 · © 2026 Kai Evans
