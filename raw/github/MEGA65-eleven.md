# MEGA65/eleven

## Metadata
- Stars: 12
- Primary language: Assembly
- Default branch: main
- Latest release: none
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/eleven

## Description
Eleven IDE - improving upon the BASIC 65 experience

## README
Eleven is an on-device BASIC 65 IDE and preprocessor for the MEGA65. Boot from the included D81 (11.D81) to launch EE, Eleven's full-screen text editor.

**Core features (preprocessor):**
- No line numbers — labels replace GOTO targets
- Named labels for flow control
- Variable declaration with arbitrary-length names
- `$` and `%` prefixes for hex and binary literals
- `#define CONSTNAME = val` for named constants
- Line continuation with `<-` (left arrow) at end of line
- `#ifdef` / `#endif` for conditional compilation
- Compilation debugging toggle (`CTRL+=`)

**Editor (EE):**
- Full-screen text editor with BASIC integration
- F1: load example; F5: compile and run; F2: new file
- F7: table of contents (in EE)
- Mark mode (`ESC,M`): select lines, cut (x), copy (c), paste (`ESC-P`)
- Navigation: `ESC,J` start of line; `ESC,K` end of line; `ESC,D` delete line; `CTRL+W`/`CTRL+U` word forward/back
- `Shift-InstDel`: delete current character

**Extra keywords supported:** WPOKE, WPEEK, SETBIT, EDMA, RPLAY

**ROM compatibility:**
- v2.3: works with 92xxxx ROMs
- v2.4: works with 99xxxx ROMs

**ALT+P integration:** Posts source over serial to PC using m65postbox tool, enabling version control of on-device source. (See `mega65-tools/src/tools/m65postbox.c`.)

**Example programs on disk:** hello.el, baseDemo.el, hopalong.el (fractal), ffire.el (forest fire), fieni (Snake), dizzy (palette shift).

**Install:** Copy D81 to MEGA65 SD card and BOOT from it. Press P during boot to access preferences.

**Maintainer:** Gurce. Confluence wiki: Eleven Walkthrough page.

## Top-level structure
- file 11.D81 — bootable disk image (complete IDE)
- file 11.edit, 11.edit.bas, 11.edit.el, 11.edit.elpc — editor modules
- file 11.parse, 11.parse.asm, 11.parse.bas, 11.parse.el, 11.parse.elpc — preprocessor/parser
- file 11.tokenize, 11.tokenize.bas — tokenizer
- file 11.post, 11.post.bas — m65postbox integration
- file 11.settings, 11.settings.bas — preferences
- file gurce.asm — assembly support routines
- file autoboot.c65, autoboot.c65.bas — boot sequence
- file 11.defaults — default settings
- file Makefile, .m65dbg_init — build and debugger init
- dir .github/ — CI
- file tests_autogen.sh — automated test generator
- file readme.txt, README.md — full documentation
