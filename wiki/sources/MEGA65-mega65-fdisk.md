---
type: source
source_url: https://github.com/MEGA65/mega65-fdisk
tags: [fdisk, sd-card, format, fat32, cc65, mega65-libc, system-utility]
related: [MEGA65-mega65-libc, MEGA65-mega65-freezemenu, cc65-cc65]
product: mega65-fdisk
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**mega65-fdisk** is the FDISK and format utility for MEGA65 SD cards. It partitions and formats SD cards in the layout the MEGA65 hypervisor expects. [[MEGA65-mega65-freezemenu]] was forked from this project and shares its FAT32, HAL, and screen code layers. [[MEGA65-mega65-libc]] is a required build dependency checked out at the same directory level.

_All claims below are sourced from ../../raw/github/MEGA65-mega65-fdisk.md unless otherwise noted._

## What it does

Provides the SD card preparation utility (`fdisk.c`) for MEGA65. Partitions the SD card and formats it with the FAT32 structure the MEGA65 hypervisor expects. Used during initial MEGA65 setup or when replacing/repairing an SD card.

## Installation

Requires: libpng12-dev (`sudo apt install libpng12-dev`), CC65 (bundled as `./cc65` submodule or local), mega65-libc checked out at the same directory level.

```sh
make                    # builds cc65 submodule + fdisk
make USE_LOCAL_CC65=1   # skips cc65 submodule build (CI)
```

## Key features

- FAT32 partition creation and formatting
- Hardware abstraction: `fdisk_hal_mega65.c` (MEGA65) and `fdisk_hal_unix.c` (host PC testing)
- Screen UI (`fdisk_screen.c`) with PETSCII output
- PNG-based screen asset preparation (`pngprepare.c`)
- Google Test unit tests (`gtest/`) for the FAT32 layer

## Architecture

`fdisk.c` — main FDISK logic; `fdisk_fat32.c` — FAT32 implementation (shared with freeze menu); `fdisk_hal*.c` — platform HAL; `fdisk_screen.c` — display; `charset.s` — PETSCII charset data. Makefile bundles CC65 as a submodule for reproducible builds.

## Maintenance status

12 stars, 9 forks, GPL-3.0, latest release v0.35 (for mega65-core 0.97, 2025-04-14), default branch `development`. Actively maintained; versioned alongside the MEGA65 core releases.
