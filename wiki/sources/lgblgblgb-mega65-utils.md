---
type: source
source_url: https://github.com/lgblgblgb/mega65-utils
tags: [utilities, sd-card, file-manager, hardware-info, ethernet, cross-platform, wip]
related: [MEGA65-mega65-tools, lgblgblgb-xemu, lgblgblgb-fdc65bas, lgblgblgb-mega80]
product: mega65-utils
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**mega65-utils** is LGB's collection of MEGA65-related utilities — both native (running on the MEGA65) and cross-platform host tools. It complements [[MEGA65-mega65-tools]] (which focuses on transfer, flash, and the serial monitor) with a broader toolkit: hardware info display, an SD card file commander, an Ethernet monitor, and experimental CP/M integration. Status is explicitly WIP.

_All claims below are sourced from ../../raw/github/lgblgblgb-mega65-utils.md unless otherwise noted._

## What it does

A set of loosely related sub-projects:

- **megainfo** — native MEGA65 tool displaying hardware info (model, version details). Similar in purpose to MEGAINFO.M65 from the freeze menu.
- **m65c** — cross-platform SD card and file commander (C + assembly). Lists and copies files on the MEGA65 SD card via Ethernet or serial. Includes FAT32 implementation.
- **navigator** — file browser/navigator for the MEGA65 (details sparse in README).
- **eth-tool** — early Ethernet/UDP monitor tool for network diagnostics.
- **c65izer** — C65 compatibility utility (undocumented; purpose inferred from name).
- **cpm** — CP/M experiments separate from lgblgblgb/mega80.
- **tests** — test programs.

## Installation

Requires: CA65 (CC65 suite, with 65CE02/4510 support), GNU Make, Python, standard UNIX utilities. Xemu recommended for testing (`xemu-mega65` in PATH).

## Key features

- FAT32 implementation for SD card access (`fat32.c` in m65c/)
- Cross-platform file commander (Linux/Mac/Windows native variants)
- Ethernet-based access to MEGA65 SD card from host PC
- Native on-device hardware info display

## Architecture

One sub-directory per utility; each has its own Makefile. Common pattern: assembly (CA65) for native MEGA65 code, C for host-side tools.

## Example usage

Use `megainfo` to capture hardware details for a bug report. Use `m65c` to copy files between a host PC and the MEGA65 SD card without physically removing the card.

## Maintenance status

6 stars, 1 fork, GPL-3.0, last pushed 2022-06-28. Dormant — no recent commits. Described by the author as experimental. Partly superseded by the official [[MEGA65-mega65-tools]] (`mega65_ftp`, `m65`) for most practical use cases.
