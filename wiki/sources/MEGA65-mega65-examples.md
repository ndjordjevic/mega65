---
type: source
source_url: https://github.com/MEGA65/mega65-examples
tags: [example-code, community, assembly, c-language, rust, cpp, multi-topic, official]
related: [RetroCogs-Mega65Tutorials, MEGA65-mega65-code-snippets, mega65.org]
product: mega65-examples
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**mega65-examples** is the official community example repository for the MEGA65 — a curated collection of source code examples demonstrating every aspect of MEGA65 capabilities, organized by language and topic with per-example build instructions. It is linked from the official [[mega65.org]] documentation. Where [[RetroCogs-Mega65Tutorials]] focuses on 45GS02 assembly deep-dives and [[MEGA65-mega65-code-snippets]] is a meta-repo of referenced snippets, mega65-examples is the canonical place for self-contained, buildable, multi-language examples.

_All claims below are sourced from ../../raw/github/MEGA65-mega65-examples.md unless otherwise noted._

## What it does

Hosts per-topic example directories organized by language:

- **asm/** — assembly examples (audio_dma, comic_border, load_save_d81, raster_bars, and more)
- **c/** — CC65/LLVM-MOS C examples
- **cpp/** — C++ examples
- **rust/** — Rust examples (unusual for an 8-bit platform; demonstrates llvm-mos-based Rust)
- **template/** — template with required `README.md` and `info.json` for new contributions

Each example is self-contained with its own directory and build instructions.

## Installation

Clone the repo; enter any example directory and follow its README. Most assembly examples use ca65/cc65 or KickAssembler; C examples use CC65 or LLVM-MOS.

## Key features

- Community-contributed, officially maintained
- Multi-language: assembly, C, C++, Rust
- Per-example `info.json` for tooling integration
- Linked from [[mega65.org]] documentation
- PR-based contribution workflow

## Architecture

Flat structure: `asm/<example>/`, `c/<example>/`, `cpp/<example>/`, `rust/<example>/`. Each example has its own Makefile/build system. `.clang-format` and `.editorconfig` for C/C++ style consistency.

## Example usage

```sh
cd asm/raster_bars
make          # produces a PRG
# transfer to MEGA65 via mega65_ftp or M65Connect
```

## Maintenance status

13 stars, 5 forks, MIT license, last pushed 2024-08-27, default branch `main`. Actively accepting PRs. Community-driven — quantity and topic coverage grows with each contribution.
