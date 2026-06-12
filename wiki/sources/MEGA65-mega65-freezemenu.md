---
type: source
source_url: https://github.com/MEGA65/mega65-freezemenu
tags: [freeze-menu, sd-card, system-utilities, megainfo, monitor, rom-loader, cc65, freezer]
related: [MEGA65-mega65-fdisk, MEGA65-mega65-libc, MEGA65-mega65-core]
product: mega65-freezemenu
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**mega65-freezemenu** provides the MEGA65's essential system utilities — the files that must be present on the SD card for the machine to function normally. The core program is **FREEZER.M65**, invoked by holding RESTORE, which manages freeze/restore slots, disk mounting, and launches the companion utilities. The project was forked from [[MEGA65-mega65-fdisk]], sharing its FAT32 and hardware abstraction layers.

_All claims below are sourced from ../../raw/github/MEGA65-mega65-freezemenu.md unless otherwise noted._

## What it does

**FREEZER.M65** — main freeze menu (hold RESTORE): freeze/restore machine state to SD slots; mount disk images; toggle hardware behavior; change disk unit numbers; F14 restores character set.

**MEGAINFO.M65** — displays hardware info: model, core version, HYPPO version, ROM version, essential file versions, RTC status. Required for bug reports.

**MONITOR.M65** — inspect frozen memory contents.

**AUDIOMIX.M65** — audio mixer controls.

**SPRITED.M65** — sprite editor for frozen memory.

**ROMLOAD.M65** — replace ROM in frozen memory; load `.CHR` files into chargen WOM.

**MAKEDISK.M65** — create empty disk images from within the freeze menu.

**BANNER.M65** — boot banner on startup.

## Installation

Always use the freeze menu version bundled with your installed core (SD Card Essentials package). Mismatched versions may cause problems since FREEZER.M65 depends on core-provided functions.

Build from source: `make` or `make USE_LOCAL_CC65=1`. Requires libpng12-dev, CC65. See the builder-docker/megabuild Docker container for a known-good Linux build environment.

## Key features

- Freeze/restore complete machine state to numbered SD card slots
- Integrated disk image chooser and D81 mounting
- Hardware state toggles (CPU speed, DMA, etc.)
- Bug-report-ready hardware info display
- Raster-based thumbnail frames for freeze slots

## Architecture

Multiple C files, one per utility, linked by shared FAT32 (`fdisk_fat32.c`), HAL (`fdisk_hal*.c`), screen (`fdisk_screen*.c`), and memory (`fdisk_memory.c`) layers — inherited from mega65-fdisk. `freezer.c` orchestrates the main menu; each sub-utility (`megainfo.c`, `monitor.c`, etc.) is a separate compilation unit.

## Example usage

Hold RESTORE on a running MEGA65 → FREEZER.M65 launches. Select a slot → press F to freeze. Return to frozen state → select slot → press R to restore. Use the `N` shortcut to mount a D81 disk image without fully entering the freeze menu.

## Maintenance status

8 stars, 14 forks, GPL-3.0, latest release v0.4.0 (2025-05-01), default branch `development`. The official core build automatically packages the latest freeze menu with each core release.
