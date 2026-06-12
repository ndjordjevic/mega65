---
type: source
source_url: https://github.com/MEGA65/eleven
tags: [basic65, ide, preprocessor, on-device, labels, line-numbers, text-editor, cross-development]
related: [dansanderson-tpn65, MEGA65-mega65-tools]
product: eleven
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**Eleven** is an on-device BASIC 65 IDE and preprocessor for the MEGA65 — a complete programming environment that runs entirely on the machine itself. It eliminates BASIC line numbers through labels, adds long variable names, hex/binary literals, conditional compilation, and integrates a full-screen text editor (EE). Its host-side counterpart for cross-development workflows is [[dansanderson-tpn65]], which provides the same label/long-name transpiler for use on a PC. The ALT+P feature posts source to a PC via m65postbox (part of [[MEGA65-mega65-tools]]) for version control.

_All claims below are sourced from ../../raw/github/MEGA65-eleven.md unless otherwise noted._

## What it does

Boot from `11.D81` to enter EE, Eleven's full-screen text editor. Write BASIC source using Eleven's enhanced syntax, press F5 to compile and run. The preprocessor translates Eleven syntax to numbered BASIC 65, which is then tokenized and executed by the ROM.

Preprocessor features:
- Named labels replacing line numbers
- Arbitrary-length variable names
- `$` and `%` prefixes for hex/binary integers
- `#define CONSTNAME = val` for constants
- Line continuation with `<-` (left arrow) at end of line
- `#ifdef` / `#endif` conditional compilation
- Extra keywords: WPOKE, WPEEK, SETBIT, EDMA, RPLAY

EE editor features:
- F1: load example; F2: new file; F5: compile & run
- ESC,J/K: start/end of line; ESC,D: delete line
- CTRL+W/U: word forward/back; Shift-InstDel: delete char
- Mark mode (ESC,M): select lines, cut (x), copy (c), paste (ESC-P)
- F7: table of contents (Eleven viewer)

## Installation

Copy `11.D81` to the MEGA65 SD card and `BOOT` from it. Press P during boot to access preferences. ROM compatibility: v2.3 for 92xxxx ROMs, v2.4 for 99xxxx ROMs.

## Key features

- Fully on-device: no PC required for writing, building, or running BASIC 65 programs
- ALT+P integration with m65postbox for PC version control
- Complete example programs on the disk: fractal, forest fire, snake, palette shift
- Makefile for rebuilding from source (requires MEGA65 toolchain)

## Architecture

Separate assembly modules for each stage: tokenizer (`11.tokenize`), parser/preprocessor (`11.parse`), editor (`11.edit`), settings (`11.settings`), and postbox integration (`11.post`). Each has `.bas`, `.el`, `.elpc` variants. `gurce.asm` provides support routines.

## Example usage

```
BOOT                  ← boot from 11.D81
F1                    ← load an example
F5                    ← compile and run
```

Write a program without line numbers; Eleven's F5 key compiles and runs it. Use `#define ROWS = 25` for magic-number constants.

## Maintenance status

12 stars, 4 forks, GPL-3.0, last pushed 2026-01-04. Actively maintained by Gurce. Confluence walkthrough page available (mega65.atlassian.net). No formal release tags — use latest from main branch.

## Ecosystem

Pairs with [[dansanderson-tpn65]] (host-side cross-transpiler for the same Eleven-like syntax) for hybrid on/off-device workflows. The on-device editor makes Eleven the natural starting point for MEGA65-native BASIC development.
