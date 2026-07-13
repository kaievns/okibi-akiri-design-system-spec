# Okibi — terminal scheme (resolved hex)

Generated from `tokens/terminal.css` + `tokens/colors.css` (v1.7). ANSI slots use the UI pigments (a 16-slot legacy surface, not code highlighting). The cursor is the ember; brights are one L-step up, never neon.

## Okibi (dark)

| token | source | hex |
|---|---|---|
| `term-bg` | var(--n0) | `#0f1113` |
| `term-fg` | var(--n10) | `#bbbec1` |
| `term-cursor` | var(--ember) | `#ff7c50` |
| `term-sel` | var(--ember-soft) | `#3f2d28` |
| `ansi-0` | var(--n1) | `#15171a` |
| `ansi-1` | var(--err) | `#f85052` |
| `ansi-2` | var(--str) | `#8eca96` |
| `ansi-3` | var(--warn) | `#e6af2b` |
| `ansi-4` | var(--call) | `#6daff7` |
| `ansi-5` | var(--kw) | `#998cb3` |
| `ansi-6` | var(--prop) | `#91c9d4` |
| `ansi-7` | var(--n10) | `#bbbec1` |
| `ansi-8` | var(--n7) | `#585b5f` |
| `ansi-9` | oklch(0.72 0.21 24) | `#ff6060` |
| `ansi-10` | oklch(0.84 0.11 148) | `#98dfa2` |
| `ansi-11` | oklch(0.84 0.15 84) | `#f8c143` |
| `ansi-12` | oklch(0.79 0.13 252) | `#7abfff` |
| `ansi-13` | oklch(0.72 0.075 300) | `#ab9acd` |
| `ansi-14` | oklch(0.85 0.07 212) | `#97dbe8` |
| `ansi-15` | var(--n11) | `#e1e3e5` |

## Akari (light)

| token | source | hex |
|---|---|---|
| `term-bg` | var(--n2) | `#f9f6f2` |
| `term-fg` | var(--n10) | `#403d38` |
| `term-cursor` | var(--ember) | `#c63a00` |
| `term-sel` | var(--ember-soft) | `#f2dcd0` |
| `ansi-0` | var(--n11) | `#13110e` |
| `ansi-1` | var(--err) | `#c71529` |
| `ansi-2` | var(--str) | `#2d713b` |
| `ansi-3` | var(--warn) | `#956000` |
| `ansi-4` | var(--call) | `#015ba6` |
| `ansi-5` | var(--kw) | `#705e91` |
| `ansi-6` | var(--prop) | `#347d8b` |
| `ansi-7` | var(--n8) | `#8d8982` |
| `ansi-8` | var(--n7) | `#b5b0a9` |
| `ansi-9` | oklch(0.47 0.20 24) | `#b00018` |
| `ansi-10` | oklch(0.43 0.12 148) | `#096125` |
| `ansi-11` | oklch(0.51 0.15 84) | `#8e5b00` |
| `ansi-12` | oklch(0.42 0.15 252) | `#004c9b` |
| `ansi-13` | oklch(0.46 0.09 300) | `#604b83` |
| `ansi-14` | oklch(0.48 0.08 212) | `#0e6978` |
| `ansi-15` | var(--n11) | `#13110e` |

Severity underlines: error = undercurl, warning/hint/spell = underdotted, escaping-write = underdashed — style carries the failure mode; colour only reinforces. Identity tints require truecolor; strict-16 disables bands 2–3.

TUI layouts are specced at line-height 1 (the character cell); GUI code leading (1.85) does not apply.
