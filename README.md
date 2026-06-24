# Okibi 燠火 — Design Specification

> おきび — *banked embers*, the coal that holds the fire.

The canonical design specification for **Okibi**, a colour system for code and
the interfaces around it. One principle — *attention is the only budget worth
spending* — dressed in charcoal, ash, and a single ember, across two grounds:
**Okibi** (dark) and **Akari 灯り** (light).

Served as a single-page static **GitHub Pages** site.

## The site

[`index.html`](index.html) is a fully self-contained page — no framework, no
build dependency at runtime, no images. Everything is CSS and system/Google
fonts. It includes:

- the full spec: philosophy, principles, two grounds, the neutral spine,
  accent & states, the syntax model, scope mapping, diagnostics, and building
  guidance
- an Okibi ⇄ Akari theme toggle (persisted in `localStorage`)
- a sticky table of contents with smooth-scroll
- OKLCH-authored colour tokens for both grounds

`favicon.svg` and `og-image.png` are the only assets; [`.nojekyll`](.nojekyll)
tells Pages to serve every path verbatim.

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

## Repository layout

| Path | Purpose |
| --- | --- |
| `index.html` | the published static site |
| `og-image.png`, `favicon.svg` | social card / icon |
| `.nojekyll` | Pages config |

---

OKIBI · 燠火 · 一つの背骨、一つの燠、注意こそ予算 · CC BY-NC 4.0 · © 2026 Kai Evans
