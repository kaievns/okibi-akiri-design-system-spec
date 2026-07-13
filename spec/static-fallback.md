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
