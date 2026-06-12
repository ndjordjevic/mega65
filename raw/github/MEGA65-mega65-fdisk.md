# MEGA65/mega65-fdisk

## Metadata
- Stars: 12
- Primary language: C
- Default branch: development
- Latest release: v0.35 (for mega65-core 0.97, 2025-04-14)
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/mega65-fdisk

## Description
FDISK+Format Utility for MEGA65

## README
mega65-fdisk is the FDISK and format utility for MEGA65 SD cards. It partitions and formats SD cards for MEGA65 use.

**Prerequisites:**
- libpng12-dev (for pngprepare): `sudo apt install libpng12-dev`
- CC65 toolchain (bundled as submodule `./cc65` or use local: `make USE_LOCAL_CC65=1`)
- mega65-libc checked out at the same directory level as mega65-fdisk

**Building:** `make` (builds cc65 submodule then fdisk) or `make USE_LOCAL_CC65=1` (uses locally installed CC65).

**CI:** Use `make USE_LOCAL_CC65=1` to skip submodule CC65 build in CI environments.

**Note:** mega65-freezemenu was started by forking this project, sharing the FAT32, HAL, and screen layers.

## Top-level structure
- file fdisk.c — main FDISK logic
- file fdisk_fat32.c/.h — FAT32 implementation
- file fdisk_hal.h, fdisk_hal_mega65.c, fdisk_hal_unix.c — hardware abstraction layer
- file fdisk_screen.c/.h — screen/UI layer
- file charset.s — PETSCII charset data
- file asciih.c, ascii00-ff.png — ASCII/PETSCII reference table generator
- file pngprepare.c — PNG preprocessing for screen assets
- file memory.cfg — memory layout configuration
- file dirtymock.h — unit test mocking header
- dir gtest/ — Google Test unit tests
- file Makefile, .gitmodules — build and CC65 submodule
- dir .github/ — CI workflow
