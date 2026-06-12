# lgblgblgb/mega80

## Metadata
- Stars: 2
- Primary language: Assembly
- Default branch: master
- Latest release: none
- License: GNU GPLv2
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/lgblgblgb/mega80

## Description
CP/M on MEGA65 with software emulation of the i8080 CPU (Z80 is planned / WIP)

## README
MEGA/80 runs CP/M v2.2 on the MEGA65 by emulating an i8080 CPU in 65xx assembly, with a custom CBIOS that dispatches CP/M system calls to the native 65xx MEGA65 implementation via HALT opcodes.

**Current state:** i8080 emulation (not Z80). CP/M v2.2 BDOS and CCP from original DR. No real disk access — CP/M disk image copied to MEGA65 Attic RAM on startup; changes are lost on exit. Only basic terminal emulation (CR, LF, BS). D81 disk image available at `dist/bin/mega65.d81`.

**Known limitations:**
- i8080 not perfectly emulated: no half-carry flag, no DAA, potential bugs
- Z80 programs won't work
- No file import/export between CP/M and MEGA65 SD card at runtime
- Terminal emulation very limited; advanced CP/M programs will break

**Plans:** Z80 emulation, improve CP/M disk access (possibly FAT32-based BDOS replacement), better terminal emulation, native BDOS using CPM65.

**Build requirements:** CC65 suite (ca65, ld65, cl65), SjASMPlus v1.20.3+ (Z80/i8080 assembler), Python 3, c1541, cpmtools, GNU make, Linux/Mac UNIX environment.

**Porting notes:** 65816 CPU is a viable porting target (Commander X16 if 65816, Apple IIgs, C64+SuperCPU). Non-65xx platforms require full rewrite.

## Top-level structure
- file main.asm — main MEGA65 entry and coordination
- file cpu.asm / cpu.inc / cpu_tables.inc — i8080 emulator
- file cpu_gen_tables.py — Python script to generate CPU decode tables
- file console.asm / console.inc — terminal/console emulation
- file disk.asm / disk.inc — CP/M disk BIOS layer
- file megagw.asm — MEGA65 gateway (system call bridge)
- file loader.asm — disk image loader to Attic RAM
- file shell.asm — basic shell
- file runme.asm — startup and dispatch
- file fontdata.asm — font data
- file emu.inc / emu.ld — emulator includes and linker config
- file mega65.inc — MEGA65 hardware defines
- file buildinfo.asm — build metadata
- dir cpm/ — CP/M v2.2 BDOS/CCP and CBIOS sources
- dir apps/ — CP/M applications
- dir boot/ — boot sector
- dir dist/ — pre-built D81 disk image (dist/bin/mega65.d81)
- file Makefile, LICENSE, README.md
