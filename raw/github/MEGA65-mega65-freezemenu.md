# MEGA65/mega65-freezemenu

## Metadata
- Stars: 8
- Primary language: C
- Default branch: development
- Latest release: v0.4.0 (2025-05-01)
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/mega65-freezemenu

## Description
Freeze Menu Program for the MEGA65

## README
The MEGA65 Freeze Menu provides the FREEZER.M65 freeze/restore system and a suite of integrated utilities. These files must be installed in the root directory of the MEGA65's SD card for normal operation. The core build process packages them automatically with each release.

**FREEZER.M65** (main program, invoked by holding RESTORE):
- Freeze/restore machine state to SD card slots
- Mount disk images, swap programs
- Toggle hardware behaviour
- Change disk unit numbers
- F14: restore character set (CHARSET.M65 or MEGA65.ROM)

**MEGAINFO.M65:** Displays hardware info — model, core, HYPPO, ROM, essential file versions, RTC status. Required for bug reports.

**MONITOR.M65:** Inspect frozen memory contents.

**AUDIOMIX.M65:** Audio mixer controls.

**SPRITED.M65:** Simple sprite editor for frozen memory.

**ROMLOAD.M65:** Replace ROM in frozen memory; load *.CHR files into chargen WOM.

**MAKEDISK.M65:** Create empty disk images (called from drive selector).

**BANNER.M65:** Boot banner displayed on startup.

**Versions:** Always use the freeze menu that matches the installed core (they are tightly coupled). The SD Card Essentials package bundled with each core release is the canonical source.

**Build:** `make` or `make USE_LOCAL_CC65=1`. Requires: libpng12-dev (for pngprepare), CC65 toolchain (bundled as submodule or local). Build environment: linux; see builder-docker/megabuild Docker container.

**History:** Forked from mega65-fdisk, which supplied many of the routines needed.

## Top-level structure
- file freezer.c / freezer.h / freezer_common.c / freezer_common.h — main freeze/restore logic
- file megainfo.c, monitor.c, audiomix.c, romload.c, sprited.c, makedisk.c — sub-utilities
- file freeze_diskchooser.c, freeze_megainfo.c, freeze_monitor.c, etc. — freeze-mode UI
- file fdisk_fat32.c/.h, fdisk_hal*.c/.h, fdisk_screen*.c/.h, fdisk_memory.c/.h — FAT32/screen/memory layers
- file frozen_memory.c, charset.s, helper.h/.s, infohelper.h/.s — support
- file gitversion.sh — embeds git hash in build
- file Makefile, .gitmodules — build and submodules
- dir assets/ — graphics (thumbnails, icons)
- dir tools/ — helper tools
- dir .github/ — CI
