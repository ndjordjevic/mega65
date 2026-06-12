---
type: source
source_url: https://github.com/lgblgblgb/mega80
tags: [cpm, i8080-emulation, z80, retro-os, 65xx-assembly, mega65-platform-experiment]
related: [lgblgblgb-xemu, lgblgblgb-mega65-utils]
product: mega80
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**mega80** (MEGA/80) is LGB's experiment running CP/M v2.2 on the MEGA65 by emulating an Intel i8080 CPU in 65xx assembly language, with a custom CBIOS that bridges CP/M system calls to native MEGA65 hardware. It is a platform curiosity rather than a production tool — valuable as a demonstration that the MEGA65 is fast enough to run a software CPU emulator and a classic operating system in real time.

_All claims below are sourced from ../../raw/github/lgblgblgb-mega80.md unless otherwise noted._

## What it does

Boots CP/M v2.2 (original DR BDOS and CCP) on the MEGA65. An i8080 emulator written in 65xx assembly interprets i8080 opcodes; HALT opcodes trap to the CBIOS, which dispatches CP/M system calls to MEGA65-native implementations. The CP/M disk image is copied to MEGA65 Attic RAM on startup (changes lost on exit). A ready-to-run D81 disk image is in `dist/bin/mega65.d81`.

## Installation

Download `dist/bin/mega65.d81` and boot from it on a MEGA65 (or Xemu). Build from source requires: CC65, SjASMPlus v1.20.3+, Python 3, c1541, cpmtools, GNU make, UNIX.

## Key features

- i8080 CPU emulation in 65xx assembly (HALT opcode = CBIOS syscall trap)
- CP/M v2.2 BDOS + CCP (original DR code)
- Basic terminal emulation (CR, LF, BS)
- Ready-to-run D81 disk image

## Architecture

`cpu.asm` — i8080 emulator; `cpu_gen_tables.py` generates CPU decode tables; `megagw.asm` — MEGA65 gateway; `disk.asm` — CP/M disk BIOS backed by Attic RAM; `console.asm` — terminal; `main.asm` — entry and coordination. CP/M components in `cpm/`.

## Example usage

Boot from `mega65.d81` — CP/M command prompt should appear. Existing CP/M 2.2 software (written for i8080, not Z80) should run if it does not rely on features with emulation gaps (no half-carry, no DAA).

## Maintenance status

2 stars, 1 fork, GPL-2.0, last pushed 2024-10-21. Explicitly described as chaotic (revived from 2017 code). Z80 emulation planned; i8080 bugs not prioritized. No file import/export between CP/M and MEGA65 SD card at runtime.
