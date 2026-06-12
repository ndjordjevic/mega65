---
type: source
source_url: https://github.com/MirageBD/MegaTool
tags: [graphics-conversion, cruncher, cross-tool, gfx2code, kickassembler, game-dev-workflow]
related: [RetroCogs-GameShell65]
product: megatool
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**MegaTool** is a C-based cross-platform host utility used by [[RetroCogs-GameShell65]] and similar MEGA65 game projects for graphics conversion and binary compression. The repository has no README, so purpose is inferred from source filenames: `gfx2code` converts image files to assembler or C data arrays, `imgconvert` handles image format conversion, and `cruncher` compresses binaries to save MEGA65 memory.

_All claims below are sourced from ../../raw/github/MirageBD-MegaTool.md unless otherwise noted._

## What it does

A suite of host-side C utilities for preparing MEGA65 game assets:
- **gfx2code** — converts image files (e.g. PNG) to KickAssembler or C data arrays ready to include in assembly projects
- **imgconvert** — converts between common image formats (input/output processing before gfx2code)
- **cruncher** — lossless data compressor for reducing binary size on disk and in memory
- **converttoheader** — converts binary data to C header (`#include`-able byte arrays)
- KickAssembler linkfiles (`DecrZero.kickasm`, `DecrZeroInit.kickasm`) and assembly stubs are included, suggesting integration with KickAssembler projects

## Installation

Build from source with `make` (UNIX) or `compile.bat` (Windows). Written in standard C.

## Key features

- Graphics pipeline: image → imgconvert → gfx2code → assembly data
- Binary compression reduces disk image and memory footprint
- Paint.NET `.pdn` format support for the example particle graphic (`particle.pdn`)
- VS Code workspace (`workspace.code-workspace`) for cross-OS development

## Architecture

Flat C project, one `.c`/`.h` pair per tool. `megatool.c` appears to be the main entry point that dispatches to the sub-tools.

## Example usage

Used in the RetroCogs game workflow: convert artwork with gfx2code → include generated data in `.s` files → crunch the output binary for distribution on a D81 disk image.

## Maintenance status

0 stars, 1 fork, no license, no README, last pushed 2025-12-07. Niche utility maintained by MirageBD for their own game development.
