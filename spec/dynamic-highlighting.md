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
