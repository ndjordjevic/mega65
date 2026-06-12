# lgblgblgb/c64-sfx-cartridge-player

## Metadata
- Stars: 18
- Primary language: Assembly
- Default branch: master
- Latest release: none
- License: GNU GPLv3
- Homepage: https://github.com/lgblgblgb/c64-sfx-cartridge-player/wiki
- Fetched: 2026-06-12
- Final URL: https://github.com/lgblgblgb/c64-sfx-cartridge-player

## Description
Commodore 64 (or MEGA65) "AdLib" player (for DOSBOX DRO files) using SFX Sound Expander Cartridge or similar

## README
An OPL2/AdLib DRO file player for the C64 (with SFX Sound Expander cartridge) and MEGA65 (with direct OPL register access). Plays DOSBOX DRO files — recorded OPL2 music from DOS games.

**Target platforms:**
- Real C64: requires SFX Sound Expander cartridge with YM3812 (OPL2) chip
- C64 emulation: VICE with SFX Sound Expander + OPL2 emulation enabled; `make vice`
- Real MEGA65: uses direct OPL register mapping (bypasses SFX cartridge); must load in C64 mode; `make mega65` (transfers via USB/m65 tool). Note: as of writing, real MEGA65 had OPL3 implementation problems — no sound. Project also serves as an OPL hardware test for MEGA65.
- MEGA65 emulation: Xemu/MEGA65; `make xemu`

**Build:** `make` (UNIX, CC65 + GNU make). DRO file is embedded in the binary at compile time — no on-the-fly loading. Included test DRO: StarPort BBS intro from Future Crew, recorded in DOSBOX.

**MEGA65 issue:** https://github.com/MEGA65/mega65-core/issues/232 (OPL3 hardware bug).

(C)2011,2020-2021 LGB, GNU GPL v2 or v3.

## Top-level structure
- file c64_play.a65 — main player (CA65 assembly)
- file Makefile — build and test targets
- file ld.cfg — linker configuration
- file imf2dro.c — IMF to DRO format converter
- file test.dro — test DRO file (StarPort BBS intro)
- dir prg-files/ — ready-to-use PRG binaries
- file reference_emulated_sounding.mp3 — reference audio
- file README.md, LICENSE, .gitattributes, .gitignore
- dir .github/ — GitHub Actions
