# OKIBI 燠火 — complete machine-readable context (v1.8)

You are reading the single-file source of truth for the Okibi design language. It concatenates: the doctrine + visual foundations (readme), the dynamic code-highlighting algorithm, the static fallback + markdown register, the contrast law, and every resolved token value. Follow it as binding when designing or building anything in this system. Key laws up front:

- A theme is an attention-allocation policy. Salience is a budget; <15% of any view coloured at rest.
- One ember (focus/action only, 1–2 per screen, never a link or token). Links are sora blue.
- Luminance and weight carry hierarchy; hue is rationed; nothing is distinguished by hue alone.
- Transitions are cuts (colour ease ≤0.2s max); calm-at-rest is a hard requirement.
- No italics (except comments), no teal (exceptions: async 205, spell 200), no pure magenta, no decorative textures, no emoji.
- Corners stay crisp: radii top out at 7px (cards), controls 4–5px; only pills/chips/circles are fully round.
- Dark ground "Okibi" is default (cool charcoal hue 250); light "Akari" is warm paper (hue 80) — different temperaments by design.

---

# Okibi 燠火 — Design System

**v1.8 · locked baseline · 2026-07-12** — tokens, spec, and exports are in sync at this version. Any token change bumps the version (see `CHANGELOG.md`) and regenerates `exports/`.

**Okibi** (おきび — *banked embers*, the coal that keeps the fire) is a personal design language: one warm-charcoal spine, one ember, and a handful of quiet pigments, applied with a strict attention budget. It began as a code-highlighting theme and grew a doctrine that generalises to every medium — web pages, documents, applications, editors, terminals.

Two grounds, one discipline:

- **Okibi 燠火** — the dark ground (default). Charcoal, hue 250, near-zero chroma.
- **Akari 灯り** — the light ground. Warm paper, hue 80. Set `data-theme="light"` on `<html>`.

## Sources

Built from three artifacts (copies in `reference/`, originals in the Okibi theme project):

- `Okibi - Theme JP clear v2.html` — the shipped resting theme: spine, ember, pigments, UI components.
- `Okibi - Thesis.html` — the implementation doctrine: attention-allocation, the depth model, transition policy.
- `Okibi - Editor Mock v3.html` — the working editor prototype: identity tints, risk register, refined syntax resting state.
- `OKIBI-CONTEXT.md` — the author's context-transfer document: decisions, rationale, rejected alternatives, taste constants. **Read this first when extending the system.**
- `Okibi - Syntax Spec.html` — the reproducible build sheet for the highlighting system.
- `Okibi - Spec.html` — the published one-page spec of the overall theme.
- (`Okibi - Token Taxonomy Research.html` remains in the source project — LOCKED, don't touch.)

## The doctrine (§ short form)

The load-bearing claim: **a theme is an attention-allocation policy.** Salience is a budget; every element lit dims every other. Six convictions, settled:

1. **Conserve salience.** Default everything to the ground. Under ~15% of any view carries colour at rest.
2. **Luminance leads, hue is rationed.** Hierarchy rides lightness and weight (high-bandwidth, CVD-safe). Hue marks a few nominal categories, kept muted.
3. **One ember, kept sacred.** The single warm accent marks focus and primary action only — once or twice per screen. It never colours a token, a link, or decoration.
4. **Calm over clever.** Near-monochrome, low saturation, muted ground. Sensory ergonomics, not taste.
5. **The rule is constant, even when the pixels are not.** Predictability of behaviour is the contract.
6. **Redundant where it counts.** Anything that must be told apart carries a second channel beyond hue — shape, weight, underline style.

**Motion policy:** transitions are cuts, not fades. Colour may ease ≤ 0.2s; nothing animates, pulses, or slides. State changes fire on discrete intentional boundaries, with hysteresis — never on scroll or drift.

## Content fundamentals

- **Tone:** doctrinal and warm — short declarative sentences, then a long clause that earns its length. Claims are made plainly ("This is the whole thesis."). Honest caveats are stated in-line ("a defensible bet under uncertainty").
- **Casing:** sentence case everywhere, including headings and buttons. UPPERCASE belongs only to mono kickers/labels.
- **Separators:** the middot ` · ` joins metadata ("01 · sumi", "one spine · one ember"). Em-dashes for asides. Arrows `→` for mappings.
- **Japanese naming:** every named thing carries kanji + romaji + meaning: *Okibi 燠火*, sections read "01 · sumi / The neutral spine / すみ · charcoal & ash". Colours use traditional pigment names: **Sora 空** (blue), **Wakaba 若葉** (green), **Kurenai 紅** (red), **Kuchiba 朽葉** (dead-leaf gold), **Asagi 浅葱** (pale cyan), **Kikyō 桔梗** (bellflower violet), **Yamabuki 山吹** (amber), **Ake 緋** (scarlet).
- **Bold** marks the load-bearing phrase of a paragraph, not decoration. `code` spans for identifiers.
- **No emoji.** Ever.

## Visual foundations

### Colour
- The **spine** (`--n0…--n11` + `--line`) is twelve steps of one near-neutral: void → chrome → content → raised → input → hover → borders → gutter → faint → muted → secondary → primary text. Nothing in a UI is a one-off colour; every surface and tone is a step.
- The **ember** (`--ember`) owns: primary buttons, focused borders + `--ring`, selection (`--ember-soft`), active indicators (2px inset bars), the caret, the current line number, badges. Budget: 1–2 appearances per screen.
- **Links are sora** (`--link` = `--call`), never ember.
- **States:** ok/warn/err/info/spell. Warm cluster (ember·yamabuki·ake) = focus & alarm. Notices tint their fill at 9%, border at 32% (`color-mix`).
- **Hue no-go zones (law):** teal 180–230 and pure magenta 325–345 stay empty, with exactly two sanctioned minor exceptions — async cyan 205 and the spell-overlay teal 200. No vanilla purple, no pumpkin orange, no muddy low-contrast colours. On dark grounds, warm hues need lower L / higher C than cool hues to read as equal.
- **Light theme is not an inversion** — it re-grounds to warm paper (hue 80) and raises chroma on all meaning hues to hold against white.
- **Two temperaments, by design (law):** Okibi is cool ash (hue 250) so the ember reads hotter; Akari is warm paper (hue 80). The grounds are *supposed* to feel different — never "harmonize" them onto one hue.
- **Legal text/surface pairings** are measured and codified in `spec/contrast-matrix.md` — n9+ for readable text, n8/n7 are furniture, state-colour text always ≥12.5px with a glyph.
- **Never hue alone (law):** some roles intentionally share hues (ok ≈ wakaba, info = sora). Every status indicator therefore carries a glyph or letter (`M ✓ + ⑂ ✕ ▲`) as the primary channel; colour only reinforces. A colour-only indicator is a defect.

### Typography
- **Shippori Mincho B1** (`--mincho`) — display: hero kanji, titles, section heads, seals. Weights 500–800.
- **Zen Kaku Gothic New** (`--gothic`) — body prose and UI text. 400/500/700.
- **JetBrains Mono** (`--mono`) — code, labels, kickers, filenames, values, numbers-as-data. (Native editors use an Iosevka-class font — "Ioskeley Mono" — with wide weight range + true italics; JetBrains Mono is the web stand-in.)
- Scale in `tokens/typography.css`. Body 15.5/1.64; code 13/1.85; minimum on web 9.5px mono labels; print minimum 12pt body.
- The **kicker** (11px mono 600, uppercase, .26em, ember) and the **label** (10px mono 600, uppercase, .14em, `--n8`) are the two workhorse micro-styles.
- **Faint labels are furniture, not reading matter (stated choice):** n8 at 10px is deliberately sub-AA — glanceable structure, never content. Anything that must be *read* uses n9+ at 12.5px+.
- **Emphasis in JP-capable families is weight, never slant** — Shippori/Zen Kaku have no true italics and synthetic oblique is forbidden. Only the mono family may italicize (comments).

### Surfaces, borders, elevation
- Cards: `--surface-content` fill, 1px `--line` hairline, `--radius-card` (7px), **no shadow at rest**. Shadows (`--shadow-pane`, `--shadow-window`) are for floating things: windows, popovers, pinned pills.
- **Elevation law: chrome sits BELOW the content; the working surface is the brightest plane.** Bars/sidebars on `--n1`, content on `--n2` — attention economy applied to UI. Active rows get `--ember-soft` fill + 2px inset ember bar. Borders are soft visible hairlines — never bright, never darker-than-panel voids.
- Hairline dividers may fade: `color-mix(in srgb, var(--n6) 55%, transparent)`.
- **Control text centers by construction (law):** every button/pill/chip/badge sets `line-height: 1` + symmetric padding inside a flex-centered box. JP fonts carry tall, asymmetric line boxes — default leading is never trusted for control text.

### Motifs (the signature moves)
- **The signature rule** — a header's bottom border is ember for the first 64px, then hairline (`--rule-signature`).
- **The ember glow** — the page void carries one radial breath of warmth, top-right (`.okibi-ground` / `--glow-ember`). No patterns or textures on the ground.
- **Section title-cards** — big mincho kanji with a 4px ember bar at left; mono number-kicker; mincho title; kana reading in wide tracking.
- **判 the seal** — a rotated (-3°) ember square, radius 6px, bearing one mincho kanji. The brand mark.
- **Vertical kanji** — hero marks set `writing-mode: vertical-rl`, with a soft ember text-shadow.

### Iconography
- **No icon font, no drawn SVGs.** Unicode glyphs are the icon set, set in mono: `◐ ◑` theme, `⑂` branch, `▤ ⌕ ◈ ⬡ ⚙` activity, `✕` error, `▲` warning, `ⓘ` info, `•` hint, `✓` ok, `▾ ▸` disclosure, `×` close, `燠` brand. Kanji serve as icons in callouts and phase chips (構 流 異, 墨 燠 層…).
- macOS traffic lights are the only fixed-colour exception (`#ec6a5e #f4bf4f #61c554`).

## Code highlighting — the dynamic system (canon)

Okibi does **not** do static rainbow highlighting. Code colouring is a three-band system where salience follows intent; each band engages only as you engage, and withdraws on the way back out:

- **Band 1 · the resting register** (`--syn-*`) — the only colouring that is always on, and the register for code *anywhere it is merely shown* (documents, decks, review, this spec). Variables are foreground — the data is the text. **Calls carry the one strong hue** (sora); members and types are quieter steps of the same blue; keywords, operators and punctuation recede into the spine; literal numbers recede at rest (clay `--syn-number-engaged` only inside an engaged scope — builtins are decisions, digits are noise); `true/false/null` + named constants kurenai; strings wakaba; comments faint italic. Definitions bold; escape keywords (`return throw break await`) bold with no hue (`--flow-fg`). At rest a file is charcoal + one blue + a whisper of green.
- **Band 2 · identity tints** (`--id-1…7`, `--idg-*`, `--id-self`) — Focus phase. Summoned only when a scope is engaged, bounded to that block: ordered slots (amber → periwinkle → green → rose → chartreuse → violet), gold reserved for `this`/`self`; out-of-function bindings bold and traced file-wide.
- **Band 3 · risk & flow** (`--risk-*`) — Edit phase, focused scope only: escaping writes dashed, `await` cyan, `any`/`as`/unsafe bold danger; local mutation stays silent.

Status: band 1 values are settled. Band 2–3 mechanics are specified in **`spec/dynamic-highlighting.md`** (focus resolution, classification, tint assignment, risk rules, prototype deviations) — treat that file as v0: canon direction, evolving details.

**Deprecated:** the static six-pigment token mapping from "Theme JP clear v2" (keywords kikyō, types kuchiba, numbers kurenai…). It is the christmas-light model the system moves away from — build no new code surfaces with it. The pigments themselves remain canon as **UI** meaning hues only (links, states, file marks, data categories, ANSI slots).

**Diagnostic underline grammar** (`.u-*` classes): the *style* carries severity — error = wavy, warning/hint/spell = dotted, escaping-write/mutation = dashed — colour only reinforces. Maps 1:1 to terminal undercurl/underdashed/underdotted.

## Context & taste constants (from OKIBI-CONTEXT.md — binding)

- **Aesthetic brief:** modern Japanese — action anime (Hathaway, Chainsaw Man, GITS), **not** sakura/pastel. Colours feel like *a glow in the dark*: sparse, meaningful, legible as colour — "restrained ≠ washed out."
- **Calm-at-rest is a hard requirement** (AuDHD user profile). Flicker and visual churn are hostile. This is why transitions are cuts and phases are cumulative supersets.
- **Environment of record:** nvim + VS Code interchangeably (terminal fidelity matters), LSP everywhere, font = IoskeleyMonoTerm Nerd Font (Ioskeley Mono).
- **Hates (never do):** italics (except faint-italic comments), teal, cyan-on-principle, vanilla purple, pumpkin orange, muddy low-contrast colours, brown-tinted dark backgrounds, bright/pronounced borders, dark void borders, decorative background textures.
- **Loves:** viridian green, periwinkle as a distinct accent, the ember, yamabuki gold (esp. as `this`/`self`), scarlet-derived reds, bold-for-globals, glow-in-the-dark saturation used sparingly.
- **Naming:** "wakaba" appears twice in the author's vocabulary — string green 146 (UI pigments) and identity-tint chartreuse 102. Disambiguate by hue.
- **Corners stay crisp:** radii top out at 7px (cards); controls 4–5px; tags 3px. Only pills, chips and circles are fully round.
- **Working preferences:** present options as complete alternatives side by side, not knob panels; iterate by pointing ("too close to X", "dial down"). Slides/screens are referenced 1-indexed.

## Per-medium guidance

- **Web pages / specs:** `.okibi-ground` void, `--page-max` wrap, section title-cards, signature rule under the header, prose at `--measure`. Hero = vertical kanji + seal + romaji.
- **Markdown / prose editors:** the markdown register (`spec/static-fallback.md`): sigils ghost, headings by weight not hue, links sora, inline code steel, ==highlight== yamabuki wash, frontmatter as data.
- **Documents / print:** Akari ground; sheet on `--n4`/white; 12pt minimum; the ember survives in the kicker, section bars, and seal only. Diagnostics grammar works in black-and-white because shape carries it. Data tables: mono uppercase column labels on a hairline, rows separated by faded hairlines (no zebra fills), numerals in mono, aligned right; the one live row may take `--ember-soft`.
- **Applications:** chrome on `--n1`, content `--n2`, inputs `--n4`; active = soft fill + inset ember bar; status bars mono 11px; focus ring `--ring`.
- **Decks / slides:** dark ground only, no per-slide background changes; one ember note per slide; footer = mincho 燠火 left, mono page number right; ≥24px text at 1920×1080; cuts between slides. Template in `ui_kits/deck/`.
- **Editors / terminals:** band 1 always; bands 2–3 engage with focus/edit intent. Neutralise fallback grammars to foreground so nothing fireworks before semantic tokens resolve. Terminals map ANSI-16 via `tokens/terminal.css`: red→ake, green→wakaba, yellow→yamabuki, blue→sora, magenta→kikyō, cyan→asagi; brights one L-step up, never neon; fg `--n10`, bg `--n0`/`--n2`, cursor = the ember. Severity underlines translate to undercurl/underdotted/underdashed.
- **TUI applications:** build from the 16 slots + default fg/bg so they survive any terminal. Chrome (borders, box-drawing, inactive titles) sits on the spine (`--n5`/`--n8`); one active pane carries the ember pair — ember border + `--term-sel` selection; the statusline mode chip is the one solid-ember element. Diff/status letters use the ANSI meaning hues (M green, ? yellow, deletions red). Strict-16 contexts approximate the ember with `ansi-9`; truecolor uses it directly. Spec TUI layouts at line-height 1 (the character cell); the 1.85 code leading is a web/GUI luxury.

## Index

- `styles.css` — entry point (imports everything under `tokens/`).
- `tokens/` — `colors.css`, `syntax.css`, `typography.css`, `geometry.css`, `terminal.css` (ANSI-16), `base.css`, `fonts.css`.
- `guidelines/` — foundation specimen cards (Design System tab).
- `components/` — React primitives: `forms/` (Button, Field, Segmented, Toggle, Checkbox, Radio, Slider), `feedback/` (Chip, Badge, Notice, Progress), `structure/` (Kicker, SectionHead, Callout, Seal, MetaPill, ThemeSwitch), `code/` (CodePane).
- `ui_kits/document/` — the spec-document template (hero, sections, callouts, footer).
- `ui_kits/editor/` — the workbench: activity bar, explorer, tabs, code, status bar.
- `ui_kits/deck/` — the slide grammar: cover, divider, content, code, close (1920×1080).
- `exports/` — derived dev artifacts, all generated from the tokens (never hand-edit): `okibi.tokens.json`, `terminal-scheme.md`, `vscode/` (two drop-in fallback themes), `web/okibi-highlight.css` (Prism + hljs), `obsidian/okibi-snippet.css` (editor + markdown register).
- `spec/dynamic-highlighting.md` — the band 2–3 algorithm: focus, classification, tint ordering, risk, rejected alternatives.
- `spec/contrast-matrix.md` — measured contrast ratios + legal pairing rules.
- `spec/static-fallback.md` — the capability ladder, scope→token port table, and the markdown register.
- `CHANGELOG.md` — version history; bump with every token change.
- `experiments/` — live experiments; currently the phase transition machine (unsettled — do not treat as spec).
- `reference/` — the three source artifacts, verbatim.
- `SKILL.md` — agent skill wrapper for using this system elsewhere.
- `site/` — the publishable static reference site (front door `site/index.html`; deploy the whole project folder, `site/llm-context.md` is the machine endpoint).

### Intentional additions
- Semantic aliases (`--surface-*`, `--text-*`, `--accent*`, `--link`) — role names over the source's raw steps, so non-editor mediums read cleanly. Values are unchanged.
- `--syn-*` names band 1 of the dynamic system (the Mock v3 resting values). The deprecated v2 static code mapping is deliberately not tokenized, so it cannot silently come back.

### Known gaps
- The automatic phase-transition machine passed its browser experiment (`experiments/transition-machine.html`; defaults ≈1.4s / 12s / 350ms feel acceptable) — final dwell values must be dialled in inside a real editor.
- `spec/dynamic-highlighting.md` §8 lists known prototype deviations (HRW free-check gap, global overflow, name-keyed shadowing) — resolved in spec, not yet in the prototype.
- No logo files exist beyond the seal motif (a styled div, not an asset). No font binaries — Google Fonts CDN; Iosevka/"Ioskeley Mono" is unavailable there and is substituted by JetBrains Mono on the web.


---

# ══ SPEC · Dynamic highlighting (code, canon) ══

# Okibi — Dynamic highlighting: algorithm specification

The implementable rule set for the three-phase system, reconciled from the working prototype (`reference/Okibi - Editor Mock v3.html`), the build sheet (`reference/Okibi - Syntax Spec.html`) and the context-transfer document (`reference/OKIBI-CONTEXT.md`). Where the prototype's code deviates from the settled design, the deviation is listed in §8 — **the design wins**. Values live in `tokens/syntax.css`; this file defines behaviour.

Status: **band 1 settled · bands 2–3 design settled, transition machine unbuilt (§3.6)**.

## 1 · Vocabulary

- **Brace-block** — any `{…}` span, header line through closing line.
- **Function body** — a brace-block whose header is a function/method/constructor declaration (not `if/for/while/switch/catch/do/else/return/with`).
- **Focus** — the *innermost* brace-block containing the caret line. Deepest scope wins, plain and predictable. (A smarter hysteresis version was tried and **scrapped as confusing**; revisit only with real editor intent signals.)
- **Current function** — smallest function body containing the focus.
- **Phases** — Survey 構 (viewing) · Focus 流 (reading) · Edit 異 (writing). **Cumulative supersets**: each phase only ADDS a layer. Never dim-the-rest (tried, rejected: dimming fights the gaze and churns the screen).

## 2 · Band 1 — the resting register (always on)

Priority of attention (the doctrine's order): **variables & calls → properties/operators → keywords → types → comments → punctuation.** Syntax is the boring part; what matters is data and transformations.

- variables → foreground (`--syn-fg`); the data is the text
- calls & `.method(` → `--syn-call` — the one strong hue
- members → `--syn-member`; types → `--syn-type` (quiet slate; types recede, they do not lead)
- keywords → `--syn-keyword` (receded — block-openers like `if/for/while` stay quiet; indentation already shows them)
- **escape keywords bold + lifted** (`--flow-fg`): `return throw break continue yield await …` — jumps indentation can't show
- strings → `--syn-string` (viridian green — a user constant); comments → `--syn-comment`, faint + italic (the only italics in the system)
- `true false null nil undefined NaN` + named constants → `--syn-builtin` (kurenai — rare = worth salience)
- **literal numbers recede at rest** (`--syn-number`); clay (`--syn-number-engaged`) only inside the focused scope of an engaged phase. Builtins deserve more attention than numbers; never mix the two roles.
- **Definition sites bold** (`function foo`, `class Bar`, method heads).

## 3 · Phases, focus & transitions

1. Focus changes **only on discrete intentional input**: caret line change (click, arrow key). Never on scroll, hover, or time. Calm-at-rest is a hard requirement; flicker and visual churn are hostile.
2. On input, focus := innermost brace-block containing the caret; current function := smallest enclosing function body.
3. In Survey, an intentional caret placement auto-advances to Focus.
4. All phase and focus changes are **cuts** — no fades, no movement.
5. Focused block renders: faint fill (2% fg), 2px inset `--ember-line` bar, `focused scope` flag on its header. Bands 2–3 apply only within it (plus traces, §5.4).
6. **Production trigger (validated in-browser, dial in per-editor):** editor state drives the phase — viewing → Survey; cursor enters a block → Focus; typing / insert-mode → Edit. Vim modes map naturally. The browser experiment (`experiments/transition-machine.html`) confirmed auto-switching feels acceptable at roughly: edit→focus dwell ≈ 1.4s, focus→survey dwell ≈ 12s, min-hold ≈ 350ms — treat these as starting values, not canon; final tuning happens in a real editor with real typing rhythm.

## 4 · Classification (band 2 input)

For every *variable* the focused block uses, classify by **how far you must look to find where it is bound** — identity is relational, not categorical:

- **block-local** — declared inside the focused block (`let/const/var`, params, `for`/`catch` bindings).
- **fn-local** — declared in the current function (incl. its params) but outside the block: borrowed in.
- **out-of-fn** — module globals (all declarations outside every function body), captures from enclosing functions, and any name with no visible declaration.

**Weight encodes the in/out-of-function boundary** — that is the single most important read: the global-variable gotcha visible at a glance, with no loud mark. Globals the block doesn't touch stay plain; nothing is marked "just for being global."

Shadowing note: the prototype classifies by *name*, first match wins. A real implementation must key by *symbol* (LSP binding), not name.

## 5 · Tint assignment — an ordering problem, not hashing

1. **Pre-vetted pool of six** + one reserved. A hash never picks the gamut; the palette was chosen by hand once:
   - slot 1 · kohaku amber 50 — slot 3 · fuji periwinkle 285 — slot 4 · moegi green 128 — slot 5 · akabeni rose 354 — slot 6 · wakaba chartreuse 102 — slot 7 · ayame violet 312
   - slot 2 ✦ · **yamabuki gold 88 — reserved for `this`/`self`/`@`** (bold, stable across the current function), never assigned to a variable.
   - (Naming note: "wakaba" also names string-green 146 in the UI-theme vocabulary; disambiguate by hue.)
   - Hues sit clear of the category hues (builtin 24, ember 38, number-clay 48, string 146, call 252) and of each other; warm tints run lower-L/higher-C so they don't wash toward white.
2. **Interleaved slot order `[1,3,4,5,6,7]`** — consecutive picks land >100° apart. Most blocks use 2–4 tints, so the *prefix* must be the most-separated subset.
3. **Salience ranking**: assign out-of-fn first (they need stable, prominent colours: `--idg-*`, bold) → then fn-local (`--id-*`, normal) → then block-local **used ≥ 2 times**, by frequency. Once-used block-locals stay neutral — dense blocks stay calm. Fn-locals have no count threshold: borrowed wiring is always shown.
4. **Stability**: a module global's colour is fixed by **order of first appearance in the file** — it keeps that colour wherever you focus. Names keep their colours while on screen; nothing shuffles under a still cursor. Re-tinting may occur only at a focus change (a cut).
5. **Trace ranges**: block-locals tint inside the block; fn-locals trace across the current function; out-of-fn trace **file-wide** (globals) or across their home function (captures) — you see what the block is wired to and where that state lives.
6. **Overflow → neutral. NEVER recycle a hue.** A shared colour reads as a false "same binding" — worse than no colour. The pool never grows; the salience budget is fixed. (Six vivid tints coexist with a calm screen *because* colour is spatially bounded — the ≤6-hue ceiling applies to competing fills across a whole screen, not inside one focused block.)

## 6 · Risk layer (band 3 — Edit phase, focused block only)

- **Only mutation that ESCAPES the focused block is marked** — dashed underline (`--risk-escape`) on a write/compound-write to an out-of-block binding, or a mutating method (`set push pop delete clear add sort splice shift unshift`) on a receiver wired from outside; the receiver is marked too. **Local bookkeeping gets nothing** (`let x=0; x+=1`, `.push` on a local). The original "loudest non-error mark" doctrine rule was empirically wrong for mutable languages and was revised.
- **Async boundary** — `await`/`async` in cyan (`--risk-async`) — the sanctioned minor cyan.
- **Trust erosion** — `as` casts and `any` in `--risk-danger`, bold.
- **Diagnostics** (LSP): error undercurl, warning underdotted, inline message at the line end in the severity colour.
- Everything band 3 adds is shape + colour, never colour alone.

## 7 · Composition order & pipeline

Per token: band 1 role class → (engaged) identity tint if its mark covers the line → (Edit, in focus) risk decorations → diagnostics. Strictly additive.

```
per line:    lex → roleize (first-match-wins) → structurePass (def/flow) → semantic (mut/async/diag)
whole file:  buildScopeIndex (brace blocks, fn:true) · buildDeclMap (name → decl sites)
             buildGlobalSet (module-level-only decls)
per focus:   setFocus(line) → innermost block → classify used names → assign slots (§5)
render:      role + identity + risk — additive
```

Production uses **LSP scopes/references** for classification and escaping-write detection; the prototype's regex lexer is a portability stand-in.

## 8 · Prototype deviations (the design wins)

1. **Vestigial HRW**: the prototype's comments and helper functions describe rendezvous hashing — a **rejected** approach (§10). Its capture-tinting path still hashes (`poolC(hrwHash(n))`) without checking slot availability; implement §5.3's salience ordering instead.
2. **Global overflow recycling**: the prototype cycles >6 globals through the pool modulo — violates §5.6 (never recycle). Overflow globals render bold, no hue.
3. **Name-keyed marks**: shadowed names share one mark; same-name locals in other functions can pick up a tint (bounded by home-fn spans, not eliminated). LSP symbol keying fixes it.
4. **If-block focus detection** had recurring edge bugs (nested/else chains); the logic is simple deepest-block — verify when porting.
5. **Dead code**: `tint()`, `ID_N=5` — ignore.

## 9 · Terminal mapping

Undercurl = error, underdashed = escaping write, underdotted = warning/hint/spell; thickness never relied on. Identity tints require truecolor; in strict-16, bands 2–3 are disabled entirely (band 1 survives via the ANSI mapping). Real deliverable per editor: a theme + an extension for the dynamic layer (VS Code), nvim equivalents; a VS Code token-colour dump exists in the source project for mapping the full TextMate/semantic token space.

## 10 · Rejected alternatives — do not re-tread

- `hash(name) % N` tinting — adjacent names collide on one tint (false identity).
- Rendezvous/HRW hashing with skip-on-taken — fixed collisions but colours still felt random; replaced by order-of-appearance + salience.
- Tinting ALL locals — christmas tree; recurring-only + bounded fixed it.
- Tinting ONLY globals — "confusing"; reverted.
- Focus = whole function — two-screen functions ≈ whole-screen highlight; same failure as highlighting the whole class.
- Dim-the-rest instead of cumulative layers — flicker, churn, fights the gaze.
- Smart hysteresis focus unit — scrapped as confusing; deepest-block won.


---

# ══ SPEC · Static fallback + markdown register ══

# Okibi — Static fallback & the capability ladder

How the system degrades when the runtime can't power it. **The fallback is not a second theme** — it is band 1 (the resting register) mapped onto whatever token vocabulary the host has. Same visual language everywhere; tiers drop, colours never substitute.

## The capability ladder (law)

1. **Truecolor + LSP/tree-sitter references** — the full dynamic system (bands 1–3).
2. **Grammar only** (TextMate, tree-sitter captures, Prism, highlight.js, CodeMirror) — band 1. Definitions-bold survives where the grammar marks def sites (`entity.name.function`, `@function` captures); escape-keyword bold survives only where `keyword.control.flow`-class scopes exist; both degrade silently to their unbolded/receded tier elsewhere.
3. **Strict-16 ANSI** — the terminal mapping (`tokens/terminal.css`); bands 2–3 disabled.
4. **Monochrome** — weight + underline style only. The system still works: that is what redundancy is for.

**Neutralize-first rule:** every port begins by setting the host's *default* token colour to foreground and its punctuation/operator noise to the receded tiers — an allowlist, never inheritance. A grammar you haven't mapped must render quiet, not wrong.

**Data-format numbers rule:** in code, literal numbers rest receded. In data formats (JSON, YAML, TOML, CSV, frontmatter) the values *are* the content — numbers take the engaged clay (`--syn-number-engaged`) as their resting state. Strings stay wakaba-green in both.

## Scope → token mapping (the port table)

Okibi token | TextMate scopes | tree-sitter captures | Prism | highlight.js | CodeMirror (cm-)
---|---|---|---|---|---
syn-fg | variable, variable.parameter, source | @variable, @parameter | (default) | (default) | variable, variable-2
syn-call | entity.name.function†, support.function, meta.function-call | @function†, @function.call, @function.method | function | title.function_† | def†
syn-string | string, string.regexp | @string, @string.regex | string, regex, attr-value | string, regexp | string
syn-number | constant.numeric | @number, @float | number | number | number
syn-number-engaged | constant.numeric in data sources | @number (data langs) | number under language-json/yaml/toml | number under language-json/… | number in frontmatter
syn-builtin | constant.language | @boolean, @constant.builtin | boolean, constant | literal | atom
syn-member | variable.other.property, variable.other.member | @property, @field | property, attr-name | property, attr | property, attribute
syn-type | entity.name.type, entity.name.class, support.type, support.class | @type, @constructor | class-name | title.class_ | type
syn-keyword | keyword, storage | @keyword | keyword | keyword | keyword
flow-fg (bold) | keyword.control.flow, keyword.control.return, keyword.control.trycatch | @keyword.return, @exception | — (degrades) | — (degrades) | — (degrades)
syn-operator | keyword.operator | @operator | operator | operator | operator
syn-punct | punctuation | @punctuation.* | punctuation | punctuation | punctuation, bracket
syn-comment (italic) | comment | @comment | comment | comment | comment
syn-call (tags) | entity.name.tag | @tag | tag | name.tag | tag

† bold — definition sites.

## Markdown — the prose register

Markdown is the "data is the text" extreme: **prose is the content; every sigil is furniture.** Rules:

- **Sigils recede to ghost** (`--n7`): `# * _ > - + 1. [ ] ( ) == ---` and fence backticks. You should see your writing, not its plumbing.
- **Headings**: content `--n11`, weight (and size, where the host allows) carries hierarchy — **no hue on headings**. Luminance leads, in prose as in code.
- **Bold** → `--n11` 600. **Italic** → keep the slant (authored emphasis is typography, not syntax — the no-italics law governs *syntax*), also `--n11`.
- **Links & wikilinks**: text in sora (`--link` law); the URL itself receded to ghost; brackets ghost.
- **Inline code** → `--syn-member` steel-blue (a technical token in prose — quiet, distinct, never string-green); where the host allows a background, the standard 9% fg chip. **Fenced code** → the full band-1 register; the language tag → label tier (`--n8`).
- **Blockquote** → text `--n9`, 2px `--n6` left border. Never ember — quotation is not focus.
- **Lists**: markers `--n7`/`--n8`, content normal. **Task checkboxes**: unchecked `--n7`; checked tick `--ok`; completed text `--n8` strikethrough.
- **==Highlight==** → yamabuki wash (`--warn` at ~16%) with `--n11` text — a literal highlighter, the one warm mark in prose. Not ember: highlight is authored emphasis, not focus.
- **Tags** (`#tag`) → kikyō violet (`--kw`), quiet. **Frontmatter** → data-format rules (keys member-blue, strings green, numbers clay, delimiters ghost).
- **Horizontal rule** → `--line`.

## The artifacts (generated from `exports/okibi.tokens.json` — regenerate together)

- `exports/vscode/okibi-dark-color-theme.json` + `okibi-akari-color-theme.json` — drop-in VS Code themes: band-1 tokenColors, minimal workbench colours (chrome below content per the elevation law), `semanticHighlighting: false` (this IS the fallback).
- `exports/web/okibi-highlight.css` — Prism + highlight.js, both grounds (`[data-theme]` + `prefers-color-scheme`), neutralize-first.
- `exports/obsidian/okibi-snippet.css` — Obsidian CSS snippet: CM6 live-preview/source classes + reading-view Prism, markdown register included, both Obsidian base themes.
- Terminal/nvim: band 1 via tree-sitter captures per the table above; ANSI via `exports/terminal-scheme.md`.


---

# ══ SPEC · Contrast pairing matrix ══

# Okibi — Contrast pairing matrix

Measured WCAG ratios (sRGB approximation of the oklch tokens), generated from `tokens/*.css` at v1.6. Regenerate when tokens change. **Rules first, numbers after.**

## Legal pairings (law)

- **Readable text** (body, values, labels that must be read): `n9`+ at 12.5px+, `n10`+ for sustained prose. AA (≥4.5) holds for n9 on `n0–n4` dark and on `n2/n4` light; on other light surfaces use n10.
- **Furniture text** (`n8` at 10px, `n7` ghosts): deliberately sub-AA — glanceable structure, never content. Never put information only there.
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


---

# ══ TOKENS · resolved values ══

# Token values (resolved)

Format: `token · dark-hex / light-hex · dark-source`. CSS custom properties in tokens/*.css are the source of truth; hex are sRGB approximations.

## spine
- `--n0` · #0f1113 / #e1ddd8 · oklch(0.175 0.006 250)
- `--n1` · #15171a / #efece8 · oklch(0.205 0.006 250)
- `--n2` · #1b1e20 / #f9f6f2 · oklch(0.232 0.006 250)
- `--n3` · #222527 / #ebe7e2 · oklch(0.262 0.006 250)
- `--n4` · #2c2e31 / #fffdfa · oklch(0.30 0.006 250)
- `--n5` · #383b3e / #e1ddd7 · oklch(0.35 0.007 250)
- `--n6` · #474b4f / #d4d0ca · oklch(0.41 0.008 250)
- `--n7` · #585b5f / #b5b0a9 · oklch(0.47 0.007 250)
- `--n8` · #707376 / #8d8982 · oklch(0.555 0.006 250)
- `--n9` · #8f9296 / #6c6863 · oklch(0.66 0.006 250)
- `--n10` · #bbbec1 / #403d38 · oklch(0.80 0.005 250)
- `--n11` · #e1e3e5 / #13110e · oklch(0.915 0.004 250)
- `--line` · #2f3235 / #d9d5d0 · oklch(0.315 0.006 250)

## ember
- `--ember` · #ff7c50 / #c63a00 · oklch(0.74 0.178 38)
- `--ember-fg` · #231103 / #fffbed · oklch(0.20 0.04 60)
- `--ember-soft` · #3f2d28 / #f2dcd0 · color-mix(in srgb, var(--ember) 16%, var(--n2))
- `--ember-line` · #ff7c5080 / #c63a008c · color-mix(in srgb, var(--ember) 50%, transparent)

## states
- `--ok` · #89cf8e / #257231 · oklch(0.79 0.115 146)
- `--warn` · #e6af2b / #956000 · oklch(0.785 0.15 84)
- `--err` · #f85052 / #c71529 · oklch(0.665 0.205 24)
- `--info` · #6daff7 / #015ba6 · oklch(0.74 0.125 252)
- `--spell` · #67acb0 / #147175 · oklch(0.70 0.07 200)

## pigments_ui
- `--call` · #6daff7 / #015ba6 · oklch(0.74 0.125 252)
- `--str` · #8eca96 / #2d713b · oklch(0.785 0.097 148)
- `--type` · #ceb687 / #7d6535 · oklch(0.785 0.068 84)
- `--num` · #eb8278 / #b1322d · oklch(0.72 0.13 27)
- `--prop` · #91c9d4 / #347d8b · oklch(0.80 0.06 212)
- `--kw` · #998cb3 / #705e91 · oklch(0.665 0.058 300)
- `--punc` · #707376 / #8a867f · oklch(0.555 0.006 250)

## band1_resting
- `--syn-fg` · #e1e3e5 / #13110e · var(--n11)
- `--syn-call` · #6daff7 / #005eac · oklch(0.74 0.125 252)
- `--syn-string` · #8ecd92 / #257231 · oklch(0.79 0.105 146)
- `--syn-number` · #b7bfc7 / #989186 · oklch(0.80 0.014 250)
- `--syn-number-engaged` · #c9a18d / #9f7661 · oklch(0.74 0.055 48)
- `--syn-builtin` · #f2716c / #be222d · oklch(0.70 0.16 24)
- `--syn-member` · #a2bedb / #516f8e · oklch(0.79 0.052 250)
- `--syn-type` · #a5b6c8 / #52657a · oklch(0.77 0.032 250)
- `--syn-keyword` · #7c8894 / #6b7681 · oklch(0.62 0.024 250)
- `--syn-operator` · #9fa5ac / #585e65 · oklch(0.72 0.012 250)
- `--syn-punct` · #4e5358 / #9c9890 · oklch(0.44 0.010 250)
- `--syn-comment` · #646a70 / #8b857d · oklch(0.52 0.012 250)
- `--flow-fg` · #c5cbd2 / #262f39 · oklch(0.84 0.012 250)

## band2_identity
- `--id-1` · #fa9d67 / #be642a · oklch(0.78 0.132 50)
- `--id-2` · #dabe78 / #9d7300 · oklch(0.81 0.095 88)
- `--id-3` · #a6a2fc / #6b61c4 · oklch(0.75 0.128 285)
- `--id-4` · #a3ca70 / #5d821a · oklch(0.79 0.125 128)
- `--id-5` · #f38bb7 / #b14578 · oklch(0.76 0.135 354)
- `--id-6` · #cfc152 / #8f7f00 · oklch(0.80 0.132 102)
- `--id-7` · #ca94ec / #8b50ad · oklch(0.75 0.135 312)
- `--idg-1` · #ff9a52 / #af4200 · oklch(0.80 0.165 50)
- `--idg-2` · #ecc254 / #986800 · oklch(0.83 0.135 88)
- `--idg-3` · #aba3ff / #5844bc · oklch(0.77 0.160 285)
- `--idg-4` · #a4d35f / #447000 · oklch(0.81 0.155 128)
- `--idg-5` · #ff85bf / #ac1f6a · oklch(0.78 0.170 354)
- `--idg-6` · #dac721 / #7e6900 · oklch(0.82 0.165 102)
- `--idg-7` · #d793ff / #7c30a2 · oklch(0.77 0.165 312)
- `--id-self` · #ecc254 / #986800 · var(--idg-2)
- `--id-outer` · #ff9c7c / #bb461e · oklch(0.79 0.13 38)

## band3_risk
- `--risk-async` · #4bc8d5 / #007481 · oklch(0.77 0.11 205)
- `--risk-mut` · #eeb64f / #a86d00 · oklch(0.81 0.135 80)
- `--risk-escape` · #f57c5f / #be3a16 · oklch(0.72 0.155 35)
- `--risk-danger` · #f66e60 / #be241f · oklch(0.70 0.17 28)

## terminal
- `--term-bg` · #0f1113 / #f9f6f2 · var(--n0)
- `--term-fg` · #bbbec1 / #403d38 · var(--n10)
- `--term-cursor` · #ff7c50 / #c63a00 · var(--ember)
- `--term-sel` · #3f2d28 / #f2dcd0 · var(--ember-soft)
- `--ansi-0` · #15171a / #13110e · var(--n1)
- `--ansi-1` · #f85052 / #c71529 · var(--err)
- `--ansi-2` · #8eca96 / #2d713b · var(--str)
- `--ansi-3` · #e6af2b / #a36d00 · var(--warn)
- `--ansi-4` · #6daff7 / #015ba6 · var(--call)
- `--ansi-5` · #998cb3 / #705e91 · var(--kw)
- `--ansi-6` · #91c9d4 / #347d8b · var(--prop)
- `--ansi-7` · #bbbec1 / #8d8982 · var(--n10)
- `--ansi-8` · #585b5f / #b5b0a9 · var(--n7)
- `--ansi-9` · #ff6060 / #b00018 · oklch(0.72 0.21 24)
- `--ansi-10` · #98dfa2 / #096125 · oklch(0.84 0.11 148)
- `--ansi-11` · #f8c143 / #8e5b00 · oklch(0.84 0.15 84)
- `--ansi-12` · #7abfff / #004c9b · oklch(0.79 0.13 252)
- `--ansi-13` · #ab9acd / #604b83 · oklch(0.72 0.075 300)
- `--ansi-14` · #97dbe8 / #0e6978 · oklch(0.85 0.07 212)
- `--ansi-15` · #e1e3e5 / #13110e · var(--n11)

## geometry (non-colour)
- radii: tag 3px · input 4px · control 5px · notice 6px · card 7px · pill 999px — corners stay crisp; only pills/circles fully round
- borders: 1px hairlines in --line; shadows only on floating surfaces
- type: mincho display / gothic body 15.5/1.64 / mono code 13/1.85; kicker 11px .26em; label 10px .14em
