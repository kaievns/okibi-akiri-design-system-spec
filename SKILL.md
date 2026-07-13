---
name: okibi-design
description: Use this skill to generate well-branded interfaces and assets for Okibi 燠火 — a warm-charcoal, one-ember, Japanese-inflected design language — either for production or throwaway prototypes/mocks/etc. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for prototyping across web, documents, applications, editors and terminals.
user-invocable: true
---

Read the README.md file within this skill — especially "Context & taste constants" (binding user constants: no italics, no teal, no decorative textures, calm-at-rest) — and explore the other available files. For code-highlighting work, spec/dynamic-highlighting.md is the algorithm of record; for non-LSP contexts (web, Obsidian, markdown) follow spec/static-fallback.md and use the generated artifacts in exports/.

Core law before designing anything: a theme is an attention-allocation policy. One charcoal spine (--n0…--n11), one ember (--ember, 1–2 uses per screen, never a link or token), quiet pigments only where meaning earns them, under ~15% of any view coloured at rest. Hierarchy rides luminance and weight; hue is rationed; anything that must be told apart carries a second channel (shape, weight, underline style). Transitions are cuts, not fades. No emoji; unicode glyphs in mono are the iconography.

Import `styles.css` for all tokens (dark Okibi is default; set data-theme="light" on <html> for Akari). Use the components in `components/` and the templates in `ui_kits/` as starting points.

If creating visual artifacts (slides, mocks, throwaway prototypes, etc), copy assets out and create static HTML files for the user to view. If working on production code, you can copy assets and read the rules here to become an expert in designing with this brand.
If the user invokes this skill without any other guidance, ask them what they want to build or design, ask some questions, and act as an expert designer who outputs HTML artifacts _or_ production code, depending on the need.
