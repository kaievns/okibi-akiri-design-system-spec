# Okibi — Contrast pairing matrix

Measured WCAG ratios (sRGB approximation of the oklch tokens), generated from `tokens/*.css` at v1.6. Regenerate when tokens change. **Rules first, numbers after.**

## Legal pairings (law)

- **Readable text** (body, values, labels that must be read): `n9`+ at 12.5px+, `n10`+ for sustained prose. AA (≥4.5) holds for n9 on `n0–n4` dark and on `n2/n4` light; on other light surfaces use n10.
- **Furniture text** (`n8` at 10px, `n7` ghosts): deliberately sub-AA — glanceable structure, never content. Never put information only there.
- **Outline controls**: a quiet `--n1` fill + `--n6` (stroke-strong) border — never transparent-on-void, and never the default hairline, which vanishes against the Akari void (0.875 vs 0.90 L). `--line` is for passive dividers and card edges on content surfaces.
- **Hover fills (`n5`)**: transient — n9 drops to ~3.6 (dark); anything the user must read while hovering uses n10+.
- **Ember as text**: fine on content surfaces; on the page void in Akari it is ~3.9 — kickers survive (11px bold, uppercase, tracking = large-text equivalent), but never body-size ember prose on the light void.
- **State colours as text**: always with a glyph (redundancy law). Dark: all AA on n0–n3. Light: `err`/`ok` AA on n2/n4 only at 12.5px+; **`warn` was sub-AA everywhere and was darkened to L 0.53 at v1.6** — treat warn text as chip/notice-scale minimum 12.5px on n2/n4, or use warn as fill/underline instead.
- **Syntax on the editor ground (`n2`)**: every band-1 token ≥4.9 dark / ≥5.5 light except the deliberately receded tiers (keyword, punct, comment, number-at-rest — furniture by design).

## Measured ratios — Okibi (dark)

Text ↓ on surface → | n0 | n1 | n2 | n3 | n4 | n5
---|---|---|---|---|---|---
n7 ghost | 2.8 | 2.6 | 2.5 | 2.3 | 2.0 | 1.7
n8 faint | 4.0 | 3.8 | 3.5 | 3.2 | 2.9 | 2.4
n9 muted | 6.1 | 5.8 | 5.4 | 4.9 | 4.4 | 3.6
n10 secondary | 10.1 | 9.6 | 9.0 | 8.3 | 7.3 | 6.0
n11 primary | 14.7 | 14.0 | 13.0 | 12.0 | 10.6 | 8.8
ember | 7.4 | 7.1 | 6.6 | 6.1 | 5.4 | 4.4
syn-call | 8.2 | 7.8 | 7.3 | 6.7 | 5.9 | 4.9
syn-string | 10.2 | 9.7 | 9.0 | 8.3 | 7.3 | 6.1
ok | 10.3 | 9.7 | 9.1 | 8.4 | 7.4 | 6.1
warn | 9.5 | 9.0 | 8.4 | 7.7 | 6.8 | 5.7
err | 5.6 | 5.4 | 5.0 | 4.6 | 4.1 | 3.4

## Measured ratios — Akari (light, post-v1.6 warn fix pending regeneration)

Text ↓ on surface → | n0 | n1 | n2 | n3 | n4 | n5
---|---|---|---|---|---|---
n7 ghost | 1.6 | 1.8 | 2.0 | 1.8 | 2.1 | 1.6
n8 faint | 2.6 | 3.0 | 3.2 | 2.8 | 3.4 | 2.6
n9 muted | 4.1 | 4.7 | 5.1 | 4.5 | 5.5 | 4.1
n10 secondary | 8.0 | 9.2 | 10.0 | 8.8 | 10.7 | 8.0
n11 primary | 13.9 | 16.0 | 17.5 | 15.3 | 18.6 | 13.9
ember | 3.9 | 4.5 | 4.9 | 4.3 | 5.2 | 3.9
syn-call | 4.9 | 5.6 | 6.1 | 5.3 | 6.5 | 4.9
syn-string | 4.4 | 5.1 | 5.5 | 4.8 | 5.9 | 4.4
ok | 4.4 | 5.1 | 5.5 | 4.8 | 5.9 | 4.4
warn (pre-fix 0.575) | 3.3 | 3.8 | 4.1 | 3.6 | 4.4 | 3.3
err | 4.4 | 5.0 | 5.5 | 4.8 | 5.8 | 4.4

Notes: Akari surfaces are role-mapped, not luminance-monotonic (n3 and n5 dip below n2, n4 is brightest) — hence the non-monotonic rows. Large-text rule (≥18.7px, or 14px bold): 3.0 suffices; kickers and display type clear it everywhere.
