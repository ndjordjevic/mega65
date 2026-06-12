# MEGA65/mega65-examples

## Metadata
- Stars: 13
- Primary language: Assembly
- Default branch: main
- Latest release: none
- License: MIT License
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/mega65-examples

## Description
A gathering point for community created software examples for the MEGA65.

## README
Official community example collection for the MEGA65. Goal: demonstrate every aspect of MEGA65 capabilities with buildable, documented source code examples. Each example has its own directory and build instructions.

**Organization:** Examples organized by language/toolchain:
- `asm/` — assembly examples (sub-dirs by topic: audio_dma, comic_border, load_save_d81, raster_bars, ...)
- `c/` — C language examples
- `cpp/` — C++ examples
- `rust/` — Rust examples
- `template/` — template for new contributions (includes required README.md and info.json)

**Contributing:** Fork repo → create directory (lowercase, underscores) → add files including `README.md` and `info.json` → submit pull request.

Linked from the official mega65.org documentation.

## Docs
asm/ sub-directories (partial listing):
- audio_dma/ — DMA audio playback example
- comic_border/ — comic-style border effect
- load_save_d81/ — loading/saving from D81 disk images
- raster_bars/ — raster interrupt colour bars

## Top-level structure
- dir asm/ — assembly examples (organized by topic)
- dir c/ — C language examples
- dir cpp/ — C++ examples
- dir rust/ — Rust examples
- dir template/ — template for new contributions
- dir .github/ — pull request and CI configuration
- file README.md, LICENSE, .gitignore
- file .clang-format, .editorconfig
