---
type: source
source_url: https://github.com/MEGA65/open-roms
tags: [open-source-rom, c64-kernal, c65-rom, reverse-engineering, clean-room, ophis, assembly, mega65-core]
related: [MEGA65-mega65-core, MEGA65-mega65-user-guide]
product: open-roms
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**open-roms** creates copyright-clean replacement ROMs for the C64, C65, and MEGA65 — the flagship open-source project enabling free distribution of a fully functional MEGA65 without requiring original Commodore firmware. With 292 stars it is the most widely known MEGA65-related GitHub project. It is tightly coupled to [[MEGA65-mega65-core]]: the core build process uses open-roms for the included ROM image.

_All claims below are sourced from ../../raw/github/MEGA65-open-roms.md unless otherwise noted._

## What it does

Implements Commodore 64/65 ROM functionality (KERNAL + BASIC) from scratch using only secondary sources — books, public documentation, forum posts — never the original ROM binaries. The clean-room approach is enforced by a `similarity` tool that flags any byte-sequence match above 2 bytes to the original ROMs and requires an explanation.

Current working features (from STATUS.md):
- KERNAL: keyboard scanning (ghost-key resistant, C128 keys, joystick cursor), JiffyDOS/DolphinDOS support, DOS wedge, improved LOAD, high-performance garbage collector
- BASIC: strings work; integer/float variables and expressions still missing
- Extra: turbo tape load (as device 7), 51199 bytes free (to $CFFF), multi-SID silence on cold/warm start, warm-start BRK address display
- C64 and C128 keyboard: DONE; MEGA65: WIP

Missing: BASIC commands (most), RS-232, full tape save/verify, NMI incomplete.

## Installation

Pre-built ROM images in `bin/`. To compile: install Ophis assembler, then `make`. Configuration options in `CONFIG.md` (e.g. enable/disable turbo tape, DOS wedge, JiffyDOS).

## Key features

- Legally unencumbered: every routine documented with secondary-source justification
- `similarity` tool validates no byte-for-byte copying from original ROMs
- Extended BASIC features (see `doc/Extended-BASIC.md`): turbo tape, improved LIST, extra commands
- Deterministic routine ordering (alphabetical by filename) removes creative expression from the implementation
- Interoperability tests prove each ROM entry point is functionally required

## Architecture

`src/` — one `.s` file per routine (e.g. `3200.jsr_basic.s`, alphabetical order). `tools/similarity` — byte-sequence checker. `testsuite/` — interoperability tests with call-graph capture. `strings/` — constant tables. `doc/` — Extended-BASIC.md and Development.md. Ophis assembler; routines placed at fixed addresses via `*=` directives.

## Example usage

```sh
# Compile the ROMs
make

# Use a specific config
cp CONFIG.md.template CONFIG.md   # edit features
make
```

Deploy the resulting ROM files to MEGA65 SD card or use with Xemu.

## Maintenance status

292 stars, 20 forks, custom open-source license (see COPYING, LICENSE), last pushed 2026-05-16. Active development but BASIC completeness is the long-running bottleneck. Releases not formally tagged — consume from master HEAD or use the ROM bundled with the latest core release.
