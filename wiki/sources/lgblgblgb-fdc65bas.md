---
type: source
source_url: https://github.com/lgblgblgb/fdc65bas
tags: [basic65, fdc, direct-io, floppy, poke-peek, hardware-registers, learning-example]
related: [lgblgblgb-xemu, lgblgblgb-mega65-utils]
product: fdc65bas
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**fdc65bas** is LGB's experimental BASIC65 program for reading floppy disk sectors directly via POKE/PEEK to FDC (Floppy Disk Controller) registers, bypassing the MEGA65 DOS. It is primarily a learning exercise demonstrating that BASIC65 can perform low-level hardware I/O without assembly code.

_All claims below are sourced from ../../raw/github/lgblgblgb-fdc65bas.md unless otherwise noted._

## What it does

Two sub-projects: `read-demo/` — a sector read demonstration with hex dump (`fdc.prg`; `fdc.d81` is a test disk); `imager/` — an attempt at a simple MS-DOS floppy imager written in BASIC65. The FDC register interface is accessed entirely through POKE and PEEK, documenting the controller's register layout for BASIC programmers.

## Maintenance status

1 star, 0 forks, GPL-3.0, last pushed 2025-01-31. Explicitly experimental, written as a personal learning exercise. Useful primarily as a reference for how to access FDC registers from BASIC65.
