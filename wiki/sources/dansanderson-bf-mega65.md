---
type: source
source_url: https://github.com/dansanderson/bf-mega65
tags: [45gs02-assembly, example-program, brainf*ck, interpreter, d81-disk-image, acme-assembler]
related: [dansanderson-easyasm65, RetroCogs-Mega65Tutorials, dansanderson.com]
product: bf-mega65
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**bf-mega65** (bf65) is Dan Sanderson's Brainf\*ck interpreter for the MEGA65, written in 45GS02 assembly. It is mainly a teaching example: a compact, self-contained program that shows real-world use of the 45GS02 relocatable base page register and MEGA65 BASIC/assembly interoperability — a complement to the richer tutorial content in [[dansanderson.com]] and [[RetroCogs-Mega65Tutorials]].

_All claims below are sourced from ../../raw/github/dansanderson-bf-mega65.md unless otherwise noted._

## What it does

Interprets Brainf\*ck programs embedded inside a MEGA65 BASIC listing. Load with `BANK 0:BLOAD "bf65":SYS $1800`. The interpreter scans the BASIC listing from the top, skipping all non-BF characters; BASIC flow control (`RUN`) coexists with BF code because the BF interpreter launches via `SYS` and returns when the program ends. Input memory: $8500 (up to 256 bytes). Output: PETSCII to screen. Data array: $8800–$FFFF (30 KB). A ready-to-run D81 disk image is included.

## Installation

Assemble with ACME (`acme bf65.asm`). Convert example `.bas` files with `petcat -w65`. Cannot be assembled with [[dansanderson-easyasm65]] (uses macros).

## Key features

- 45GS02-specific: uses relocatable base page register ($1600); accommodates MEGA65 BASIC's `<<`/`>>` tokenization
- Ready-to-run D81 disk image with the interpreter and example programs
- Example programs: 2+5 addition, hello world, ROT13

## Architecture

Single-file ACME assembly program (`bf65.asm`). Uses MEGA65 ROM routine for output. Disk image built with `makedisk.py` + `d64` Python library.

## Maintenance status

3 stars, 0 forks, GPL-3.0, last pushed 2023-06-30. Stable teaching example; no planned updates.
