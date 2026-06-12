# RetroCogs/GS65_ShmupExample

## Metadata
- Stars: 0
- Primary language: Assembly
- Default branch: main
- Latest release: none
- License: none
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/RetroCogs/GS65_ShmupExample

## Description
Example Shmup using GameShell65 Framework

## README
Example shoot-em-up (shmup) game built using the GameShell65 framework. Demonstrates how to structure a complete game using GameShell65's RRB/Pixie/DMA-buffered pipeline.

The project has 14 commits and 1 fork. It serves as a practical reference for:
- Player ship and bullet management
- Enemy AI, spawning, and projectiles
- Math routines for game logic
- Background map and camera usage
- IRQ/frame timing per GameShell65 conventions

## Top-level structure
- file startup.asm — entry point
- file Irq.s — IRQ handler
- file Camera.s — camera/scrolling
- file BGMap.s — background map
- file Player.s — player logic
- file Bullets.s — bullet management
- file Enemy.s, EnmBasic.s, EnemyMacros.s — enemy system
- file EnmProjectiles.s, EnmSpawner.s — enemy projectiles and spawning
- file Math.s — math utilities
- file PixieText.s — text rendering
- file GSTitles.s, GSPlay.s, GSCredits.s — game state screens
- file objList_Inline.s — object list
- file makefile — build system
- dir assets/ — graphics/data assets
