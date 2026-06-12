---
type: source
source_url: https://github.com/RetroCogs/GameShell65
tags: [game-framework, kickassembler, rrb, pixies, dma, game-states, 45gs02, mega65-game-dev]
related: [RetroCogs-Mega65Tutorials, RetroCogs-GS65_ShmupExample, MirageBD-MegaTool, retrocogs.mega65.com]
product: gameshell65
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**GameShell65** is RetroCogs' KickAssembler game framework for the MEGA65, built around heavy use of the Raster Rewrite Buffer (RRB). It provides a complete game-loop skeleton with double-buffered DMA rendering, Pixie-based sprites, GameState management, and a layered background system — making it the most structured MEGA65 game-development starting point available on GitHub. [[RetroCogs-GS65_ShmupExample]] is its companion demo game. The underlying tutorials that explain the technical concepts live at [[retrocogs.mega65.com]] and [[RetroCogs-Mega65Tutorials]].

_All claims below are sourced from ../../raw/github/RetroCogs-GameShell65.md unless otherwise noted._

## What it does

Provides a frame-synchronized game loop: wait for the bottom-of-frame IRQ, DMA-buffer the current frame to hardware, then prepare the next frame. This pipeline delivers clean, tear-free animation with RRB layers. GameState modules (`GSTitles.s`, `GSPlay.s`, `GSCredits.s`) encapsulate title screen, gameplay, and credits logic.

## Key features

- RRB-heavy rendering with DMA frame buffering
- Pixie system for sprite-like objects (`PixieText.s`, `pixieReadme.md`)
- Camera and scrolling support (`Camera.s`)
- Background map system (`BGMap.s`)
- GameState pattern for screen transitions
- KickAssembler build with Makefile

## Architecture

Entry at `startup.asm`; `Irq.s` handles frame synchronization; game-state modules are separate `.s` files. Assets in `assets/`, shared definitions in `includes/`.

## Maintenance status

2 stars, 2 forks, no license, last pushed 2026-04-21. Actively maintained by RetroCogs. README has placeholder sections (layers, Pixies detail is in `pixieReadme.md`).
