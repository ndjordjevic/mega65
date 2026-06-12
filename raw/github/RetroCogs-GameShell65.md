# RetroCogs/GameShell65

## Metadata
- Stars: 2
- Primary language: Assembly
- Default branch: main
- Latest release: none
- License: none
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/RetroCogs/GameShell65

## Description
Game Shell for making Mega65 games in kickasm

## README
GameShell65 is a full KickAssM sample engine for the MEGA65, focused on heavy RRB (Raster Rewrite Buffer) usage. It provides a structured game framework with:

**Frame Layout:** Waits for bottom IRQ, then DMA-buffers the frame. Once complete, the next frame is prepared. This gives a clean double-buffered rendering pipeline.

**Layers:** RRB-based layered rendering (documentation placeholder in README).

**Pixies:** Sprite-like objects using MEGA65's Pixie system (documentation placeholder; see pixieReadme.md in repo).

**GameStates:** Support for screen management — title screen, gameplay, hi-score, etc. Each state is a separate module.

Structure:
- startup.asm — boot entry point
- Irq.s — IRQ handler and frame synchronization
- Camera.s — camera/scrolling logic
- BGMap.s — background map handling
- PixieText.s — text rendering using Pixies
- GameShell65.code-workspace — VS Code workspace
- makefile — build system
- includes/ — shared include files
- assets/ — graphics and data assets
- build/ — compiled output
- install/ — deployment utilities

Built with KickAssembler. Companion example: GS65_ShmupExample.

## Top-level structure
- file startup.asm — entry point
- file Irq.s — IRQ/frame sync
- file Camera.s — camera
- file BGMap.s — background map
- file PixieText.s — text via Pixies
- file GSPlay.s, GSTitles.s, GSCredits.s — game state modules
- file pixieReadme.md — Pixie system documentation
- dir includes/ — shared includes
- dir assets/ — graphics/data
- dir build/ — output
- dir install/ — deployment
- file makefile
