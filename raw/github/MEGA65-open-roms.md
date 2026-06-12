# MEGA65/open-roms

## Metadata
- Stars: 292
- Primary language: Assembly
- Default branch: master
- Latest release: none (pre-built images in bin/)
- License: Other (custom open-source; see LICENSE and COPYING)
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/open-roms

## Description
A project to create unencumbered open-source ROMs for use on selected retro computers

## README
Open ROMs creates copyright-clean replacement ROMs for retro computers — initially the C64 and C65, to enable free distribution with the MEGA65. The project exists explicitly to respect intellectual property rights; ROMs are reverse-engineered using only secondary sources (books, public documentation), never by reading the original ROM binaries.

**Key documents:** STATUS.md (feature status), CONFIG.md (compilation options), doc/Extended-BASIC.md, doc/Development.md, CREDITS.md.

**Legal approach:** Clean-room reverse engineering. Each routine is justified by secondary sources (e.g. "Mapping the C64"). A `similarity` tool checks for byte-sequence matches to original ROMs and requires an explanation for each hit above 2 bytes.

**Method:**
1. Start from 6502 reset/IRQ/NMI vectors only
2. Stub the C64 KERNAL jump table from public API docs
3. Implement routines in deterministic alphabetical order (no creative ordering)
4. Use secondary sources only (books, forum posts, public disassembly commentary)
5. Justify interoperability of each routine with test programs that prove the calling address is required

**Current status (from STATUS.md):**
- BASIC: strings work; integer/float variables and expressions still missing
- KERNAL: keyboard scanning improved (ghost-key resistant, C128 keys, joystick cursor); JiffyDOS/DolphinDOS; DOS wedge; improved LOAD; high-performance GC
- New features: turbo tape load, 51199 bytes free (up to $CFFF), multi-SID silence, extra BASIC extensions (see doc/Extended-BASIC.md)
- Missing: full tape (VERIFY/SAVE/seq files), most BASIC commands, RS-232, NMI incomplete

**Hardware support:** C64 keyboard (DONE), C128 keyboard (DONE). MEGA65: work in progress.

**Pre-built binaries:** bin/ directory.

## Top-level structure
- dir src/ — assembly sources, one routine per file
- dir doc/ — Extended-BASIC.md, Development.md, screenshots
- dir bin/ — pre-built ROM images
- dir tools/ — similarity checker and build helpers
- dir testsuite/ — interoperability test programs
- dir strings/ — string constant tables
- dir assets/ — screenshots
- dir 3rdparty/ — third-party dependencies
- file STATUS.md — per-feature implementation status
- file CONFIG.md — compilation configuration options
- file README.md, LICENSE, CREDITS.md, CONTRIBUTORS.md
- file Makefile — build system (Ophis assembler)
