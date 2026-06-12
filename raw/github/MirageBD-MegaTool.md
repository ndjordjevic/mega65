# MirageBD/MegaTool

## Metadata
- Stars: 0
- Primary language: C
- Default branch: main
- Latest release: none
- License: none
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MirageBD/MegaTool

## Description
(no description; purpose inferred from source filenames)

## README
No README file present in this repository.

## Top-level structure
Purpose inferred from source filenames:

- file megatool.c / megatool.h — main tool (C, cross-platform host utility)
- file gfx2code.c / gfx2code.h — graphics-to-code converter (converts image files to assembly or C data)
- file imgconvert.c / imgconvert.h — image format converter
- file cruncher.c / cruncher.h — data cruncher/compressor
- file file.c / file.h — file I/O helpers
- file converttoheader.c — converts binary data to C header include files
- file particle.bin / particle.pdn — example particle graphic asset (PDN = Paint.NET format)
- file DecrZero.kickasm, DecrZeroInit.kickasm — KickAssembler linkfiles/linker scripts
- file DecrZero.s, DecrZeroInit.s — assembly stubs
- file Linkfile.DecrZero, Linkfile.DecrZeroInit — linker configuration
- file Makefile — build system
- file compile.bat — Windows build script
- file workspace.code-workspace — VS Code workspace
- dir bin/ — compiled output
- dir .vscode/ — VS Code settings
- dir assets/ — (inferred) graphic assets

Used by RetroCogs in their MEGA65 game development workflow (GameShell65 project). Provides gfx2code for converting artwork into KickAssembler data, imgconvert for format conversion between common image types, and a cruncher for reducing binary size.
