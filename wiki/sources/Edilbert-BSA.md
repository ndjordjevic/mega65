---
type: source
source_url: https://github.com/Edilbert/BSA
tags: [assembler, 45gs02, 6502, 65c02, cross-assembler, single-file, unlicense, mega65-toolchain]
related: [dansanderson-bsa-vscode, cc65-cc65, MEGA65-mega65-code-snippets]
product: bsa
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**BSA** (Bit Shift Assembler) by Edilbert is a cross-assembler for 6502, 65C02, and 45GS02 CPUs — the upstream of the MEGA65/BSA fork used in MEGA65 development. Its notable property is single-file distribution: the entire assembler is one portable C file (`bsa.c`). [[dansanderson-bsa-vscode]] provides VS Code language server support. [[cc65-cc65]]'s `ca65` is the main alternative for assembly-only work; BSA targets a simpler, self-contained workflow.

_All claims below are sourced from ../../raw/github/Edilbert-BSA.md unless otherwise noted._

## What it does

Translates 6502/65C02/45GS02 assembly source (`.asm`) into binary output files. Reads one input file, produces a listing with cross-reference (`.lst`). Binary output is controlled by the `.STORE` pseudo-op inside the source — no separate linker required for most projects.

Target CPU: set with `.CPU 45GS02` (or `6502`, `65C02`). Case sensitivity: mnemonics and pseudo-ops are case-insensitive; labels are case-sensitive by default (`-i` flag or `.CASE -` to disable).

## Installation

Compile from source with any standard C compiler:
```sh
gcc -o bsa bsa.c
```
macOS M2 binary (`bsa_m2.x`) included. No dependencies.

## Key features

- Full 45GS02 addressing mode and instruction support
- Rich pseudo-ops: `.ORG`, `.STORE`, `.BYTE`, `.WORD`, `.BIGW`, `.QUAD`, `.REAL`, `.FILL`, `.INCLUDE`, `.BSS`, `.CASE`, `#define`, `#ifdef`/`#endif`
- Operators: `<`/`>` (low/high byte), `$`/`%` (hex/binary), `!`/`~` (logical/bitwise negate), `&`/`|`/`^` (bitwise), arithmetic with `[`/`]` grouping
- PETSCII string support: `'hello'^` encodes Commodore PETSCII (OR last byte with $80)
- `.LOAD $0401` prepends a CBM load address to the binary output
- Vim syntax file (`asm.vim`) included

## Architecture

Single source file `bsa.c` — first ~100 lines are self-contained documentation. Pre-built Mac M2 binary `bsa_m2.x`. No build system beyond a C compiler.

## Example usage

```sh
gcc -o bsa bsa.c

# Source file:
#   .CPU 45GS02
#   .ORG $2001
#   .STORE MYPRG,$2001,"myprg.prg"
#   ; ... 45GS02 assembly ...

bsa myprg       # reads myprg.asm, writes myprg.lst and myprg.prg
```

## Maintenance status

33 stars, 7 forks, The Unlicense (public domain), last pushed 2025-03-04, default branch `master`. Actively maintained by Edilbert. The MEGA65/BSA fork tracks this repo with additional commits for MEGA65-specific needs.

## Ecosystem

The MEGA65/BSA fork (github.com/MEGA65/BSA) is the version used in the official MEGA65 workflow. [[dansanderson-bsa-vscode]] provides VS Code IDE support for BSA syntax. [[cc65-cc65]] is the more widely used toolchain for C projects; BSA occupies the niche of simple, linker-free assembly-only projects.
