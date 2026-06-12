---
type: source
source_url: https://github.com/dansanderson/mega65-pcfonts
tags: [tall-character-mode, pc-fonts, tcr-files, font-conversion, d81-images, python-scripts]
related: [MEGA65-mega65-user-guide, dansanderson.com]
product: mega65-pcfonts
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**mega65-pcfonts** is a compact MEGA65 asset repo that turns 43 old-school PC fonts into ready-to-use TCR files for the machine's Tall ChaRacter mode. It is useful both as a font archive and as a reproducible example of how to package alternate character sets into a D81 image for MEGA65 use.

_All claims below are sourced from ../../raw/github/dansanderson-mega65-pcfonts.md unless otherwise noted._

## What it does

Provides a curated archive of 8x16 PC fonts converted to MEGA65 TCR format, plus a browsable `PCFONTS.D81` disk image and loose `.tcr` files for manual SD-card use. The archive is based on the Oldschool PC Font Resource and keeps the fonts in a form the MEGA65 can load directly into character-generator memory.

## Installation

The quickest path is to copy `PCFONTS.D81` to an SD card, mount it, and boot the included browser with `MOUNT "PCFONTS.D81"` followed by `RUN "*"`. For direct use in a program, load the desired `.TCR` file into `$FF7E000`, optionally clear `PALEMU` bit 5 at `$D054`, and set TCR mode with bit 4 in `CHARY16` at `$D07A`.

## Key features

- 43 converted 8x16 PC fonts from the Oldschool PC Font Resource
- Both 128-character and 256-character TCR variants for each font
- A packaged `PCFONTS.D81` browser/demo for on-machine font selection
- Loose TCR files for copying straight to SD card
- A conversion script that reorders original `.FON` files into MEGA65-friendly screen-code layouts

## Architecture

The repo is mostly generated assets plus a small packaging toolchain. `fontotcr.py` converts 8x16, 256-character `.FON` files into both 128-char and 256-char TCR outputs. `makedisk.py` assembles the `PCFONTS.D81` image, `pcfonts.bas` is the demo/browser, `tcr/` holds the generated font files, and `files.json`/`tcrpaths.py` support the packaging and naming flow.

## Example usage

```basic
10 BLOAD "MYFONT.TCR",P($FF7E000)
20 CLRBIT $D054,5
30 SETBIT $D07A,4
```

On the machine itself, the included browser lets you switch fonts without writing code: mount `PCFONTS.D81`, run the demo, and browse to a TCR file with the Freezer file picker.

## Maintenance status

3 stars, 0 forks, default branch `main`, no tagged releases, no declared license, and last pushed 2025-02-14. It is a small, purpose-built archive rather than an actively evolving framework; the README explicitly treats `fontotcr.py` as a handy conversion script, not a polished supported tool.
