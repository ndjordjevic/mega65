# Edilbert/BSA

## Metadata
- Stars: 33
- Primary language: C
- Default branch: master
- Latest release: none
- License: The Unlicense
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/Edilbert/BSA

## Description
Bit Shifter's Cross Assembler for 6502, 65C02 and 45GS02 CPU

## README
BSA (Bit Shift Assembler) is a cross-assembler for 6502, 65C02, and 45GS02 CPUs, written in portable C. The MEGA65 fork (at github.com/MEGA65/BSA) is the version used in MEGA65 development. Pre-built binary for Mac M2 included; Windows/Linux compile from source.

**Installation:** Compile with any standard C compiler: `gcc -o bsa bsa.c`. Single source file.

**Running:** `bsa hello` reads `hello.asm`, writes `hello.lst` (listing + cross-reference). Binary output controlled by `.STORE` pseudo-op.

**Case sensitivity:** 6502 mnemonics and pseudo-ops are case-insensitive. Labels and constants are case-sensitive by default; `-i` flag or `.CASE -` directive disables sensitivity.

**Key pseudo-ops:**
- `.CPU 45GS02` / `.ORG $E000` / `* = $E000` — CPU target and program counter
- `.LOAD $0401` — prepend CBM load address
- `.STORE BASIC_ROM,$2000,"basic.rom"` — write binary image file
- `.BYTE`, `.BHEX`, `.WORD`, `.BIGW`, `.QUAD`, `.REAL`, `.REAL4` — data definition
- `.FILL N ($EA)` — fill memory; `.INCLUDE "filename"` — include file
- `.BSS 2` / `& = $033A` — BSS segment and pointer
- `#define` / `#ifdef` / `#endif` — conditional assembly (via Edilbert extension)

**Addressing modes:** Full 45GS02 mode set (immediate, zero-page, absolute, indirect, stack-relative, etc.)

**Operators:** `<`/`>` (low/high byte), `[`/`]`/`(`/`)` (grouping), `+`, `-`, `*` (also PC), `/`, `$`/`%` (hex/binary), `!`, `~`, `&`, `|`, `^`.

**Vim syntax file:** `asm.vim` included.

## Top-level structure
- file bsa.c — complete assembler (single-file C; first ~100 lines are documentation/instructions)
- file bsa_m2.x — pre-built macOS M2 binary
- file asm.vim — Vim syntax highlighting
- file README.md, LICENSE (Unlicense)
