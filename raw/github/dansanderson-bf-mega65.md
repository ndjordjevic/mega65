# dansanderson/bf-mega65

## Metadata
- Stars: 3
- Primary language: Assembly
- Default branch: main
- Latest release: none
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/dansanderson/bf-mega65

## Description
A Brainf*ck interpreter for the MEGA65

## README
bf65 is an interpreter for the Brainf*ck programming language written for the MEGA65, in 45GS02 assembly language. A ready-to-run D81 disk image (bf65.d81) is provided.

**BF language:** 8 instructions (`>`, `<`, `+`, `-`, `.`, `,`, `[`, `]`) manipulating a byte array. Input from memory at $8500 (up to 256 bytes). Output to screen. Data array $8800–$FFFF (30 KB).

**Usage:** Write BF code in numbered BASIC lines. Any numbered line beginning with a BF character is BF code; other lines are BASIC. Load and invoke with `BANK 0:BLOAD "bf65":SYS $1800`. BF65 ignores BASIC tokens and non-BF characters on BF lines.

**MEGA65 specifics:** Uses 45GS02 relocatable base page register ($1600 as base page). BASIC start assumed at $2001. MEGA65 BASIC `<<`/`>>` operators handled specially in the lexer.

**Building:** Written for the ACME assembler. `acme bf65.asm` → bf65.prg (load address $1800). Example listings in petcat format; convert with `petcat -w65 -o <out.prg> -- <file.bas>`. Disk image built with makedisk.py + d64 Python library.

**Standards compliance:** EOF handled as no-op (data cell unchanged). Data cursor out-of-range exits with error. Byte values wrap at 0/255. PETSCII output (ASCII programs may show wrong case).

## Top-level structure
- file bf65.asm — main 45GS02 assembler source (ACME format)
- file bf65.d81 — ready-to-run D81 disk image
- file bf65_unittests.asm — sloppy test code
- file makedisk.py — disk image builder (requires d64 Python library)
- file files.json — disk image manifest
- file 2-plus-5.bas, hello.bas, rot13.bas — example BF programs in petcat format
- file 2-plus-5-out.bas — example with output display
- file typeme.txt — text
- file LICENSE, .gitignore
