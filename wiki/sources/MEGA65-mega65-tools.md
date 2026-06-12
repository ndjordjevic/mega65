---
type: source
source_url: https://github.com/MEGA65/mega65-tools
tags: [m65-cli, mega65-ftp, etherload, coretool, romdiff, cross-platform-build, hardware-deployment]
related: [wiebow.mega65.com, dansanderson.com, MEGA65-mega65-code-snippets, MEGA65-m65dbg, dansanderson-homebrew-mega65, lgblgblgb-mega65-utils, MEGA65-m65connect]
product: mega65-tools
detail_level: standard
created: 2026-06-10
updated: 2026-06-12
---

The official MEGA65 command-line tool suite (C, actively developed — pushed June 2026): everything needed to talk to real hardware from a PC. These are the binaries behind the deployment workflows in [[wiebow.mega65.com]] and [[dansanderson.com]].

_All claims below are sourced from ../../raw/github/MEGA65-mega65-tools.md unless otherwise noted._

## What it does

- `m65` — "swiss army knife" for automated actions on MEGA65 hardware (JTAG/serial)
- `mega65_ftp` — put/get files to/from the SD card
- `etherload` (BETA) — Ethernet communication; requires a development core
- `coretool` — work with core container files (replaces deprecated `bit2core`/`bit2mcs`)
- `romdiff` — create and apply RDF ROM patches
- `m65dbg` (macOS target listed) — debugger over serial

## Installation

Pre-built binaries on Filehost for Linux/Windows/macOS in both development (`m65tools-<os>-dev`) and release (`m65tools-<os>`) flavors — most users should download rather than build.

## Key features

Build system supports Linux (`make all`, long apt dependency list incl. cc65, libusb, cairo), Windows cross-build from Linux (`make WIN_CROSS_BUILD=1 allwin` with mingw-w64 + conan) or native msys2/Git-Bash, and macOS (`brew install conan cmake; make allmac`, per-tool targets like `make bin/etherload.osx`). Known mingw quirk: `libusb.h` include path needs `libusb-1.0/` prefix. gtest-based unit tests via `make test`.

## Example usage

From [[wiebow.mega65.com]]: `mega65_ftp -e -c "put file.d81" -c "quit"` then `etherload -5 -m file.d81 -r main.prg`.

## Maintenance status

37 stars / 34 forks, very active (June 2026), default branch `development`; releases cut from release-* branches to Filehost. No declared license.

## Ecosystem

GUI wrapper: M65Connect (github.com/MEGA65/m65connect). Listed as the core team toolchain in [[MEGA65-mega65-code-snippets]].
