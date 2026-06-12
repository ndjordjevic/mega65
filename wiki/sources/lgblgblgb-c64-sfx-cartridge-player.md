---
type: source
source_url: https://github.com/lgblgblgb/c64-sfx-cartridge-player
tags: [opl2-audio, adlib, dro-format, sfx-cartridge, ym3812, audio-hardware, mega65-testing]
related: [lgblgblgb-xemu, lgblgblgb-megacyc]
product: c64-sfx-cartridge-player
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**c64-sfx-cartridge-player** is LGB's OPL2/AdLib DRO file player for the Commodore 64 and MEGA65. On the C64 it targets the SFX Sound Expander cartridge with a YM3812 chip; on the MEGA65 it accesses OPL registers directly via memory-mapped I/O. It doubles as a MEGA65 OPL hardware test — real MEGA65 hardware had an OPL3 implementation bug at time of writing that caused no audio output (issue #232 in mega65-core).

_All claims below are sourced from ../../raw/github/lgblgblgb-c64-sfx-cartridge-player.md unless otherwise noted._

## What it does

Plays DOSBOX DRO files (recorded OPL2 music from DOS games), with the DRO file embedded in the binary at compile time. The included test DRO is the StarPort BBS intro from Future Crew. `make mega65` transfers and starts the PRG on real MEGA65 via USB/m65 tool. `make xemu` runs in [[lgblgblgb-xemu]]. `make vice` runs in VICE with SFX cartridge emulation.

## Key features

- DRO playback via OPL2 register writes
- Separate code paths for C64 (SFX cartridge I/O) and MEGA65 (direct register access)
- `imf2dro.c` — IMF-to-DRO format converter
- Pre-built PRG binaries in `prg-files/`

## Maintenance status

18 stars, 1 fork, GPL-3.0, last pushed 2024-10-20. Active but narrow scope. Useful primarily as a MEGA65 OPL hardware test until the hardware bug is resolved.
