# lgblgblgb/mega65-utils

## Metadata
- Stars: 6
- Primary language: C
- Default branch: master
- Latest release: none
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/lgblgblgb/mega65-utils

## Description
Various Mega65-related utilities/software, work in progress

## README
A collection of Mega-65 related utilities and software by LGB (Gábor Lénárt), both native (running on MEGA65 directly) and cross-platform host tools. Experimental/WIP quality; 6 stars.

**Requirements:** CA65 assembler (CC65 suite, up-to-date with 65CE02/4510 support), Linux/UNIX with GNU Make, Python, standard utilities. Xemu (as `xemu-mega65`) recommended for quick testing.

**Sub-projects:**

- `megainfo/` — Native MEGA65 utility to display hardware info (model, versions, etc.). Analogous to the MEGAINFO.M65 utility that ships with freeze menu.
- `m65c/` — Cross-platform SD card and file commander (C + assembly). Lists, copies, and manages files on the MEGA65 SD card via Ethernet/serial. Includes fat32.c, m65c.h, platform-specific mains.
- `navigator/` — (undocumented; likely a file browser/navigator for MEGA65)
- `eth-tool/` — Early Ethernet/network monitor utility using UDP; experimental.
- `c65izer/` — (undocumented; likely a C65-compatibility tool)
- `cpm/` — CP/M-related experiments (separate from lgblgblgb/mega80)
- `mcpi/` — (undocumented)
- `tests/` — Test programs

**Status:** Work in progress. Not production-ready. Complements the official MEGA65-mega65-tools (which focuses on transfer/flash/monitor) with a broader utility toolkit.

## Top-level structure
- dir megainfo/ — hardware info display tool (native MEGA65)
- dir m65c/ — cross-platform SD card commander
- dir navigator/ — file navigator
- dir eth-tool/ — Ethernet/UDP monitor tool
- dir c65izer/ — C65 compatibility utility
- dir cpm/ — CP/M experiments
- dir mcpi/ — undocumented sub-project
- dir tests/ — test programs
- file README.md, LICENSE, Makefile, .gitattributes, .gitignore
