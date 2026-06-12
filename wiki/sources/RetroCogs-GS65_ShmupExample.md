---
type: source
source_url: https://github.com/RetroCogs/GS65_ShmupExample
tags: [game-example, shmup, kickassembler, rrb, pixies, gameshell65, 45gs02]
related: [RetroCogs-GameShell65, RetroCogs-Mega65Tutorials]
product: gs65-shmupexample
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**GS65_ShmupExample** is a complete shoot-em-up game example for the MEGA65 built on the [[RetroCogs-GameShell65]] framework. It demonstrates how GameShell65's RRB/Pixie/DMA-buffered pipeline scales to a real game with player ships, bullets, enemies, spawning, and math routines.

_All claims below are sourced from ../../raw/github/RetroCogs-GS65_ShmupExample.md unless otherwise noted._

## What it does

Implements a full shmup: player input and movement (`Player.s`), bullet management (`Bullets.s`), enemy AI with macros and basic AI states (`Enemy.s`, `EnmBasic.s`, `EnemyMacros.s`), enemy projectiles and spawners (`EnmProjectiles.s`, `EnmSpawner.s`), math utilities (`Math.s`), background and camera (`BGMap.s`, `Camera.s`), and title/play/credits game states. Demonstrates the complete GameShell65 game loop in practice.

## Architecture

Follows the GameShell65 module layout: `startup.asm` entry, `Irq.s` frame sync, per-feature `.s` files, `assets/` for graphics data, `makefile` for KickAssembler build.

## Maintenance status

0 stars, 1 fork, no license, 14 commits, last pushed 2026-04-06. Small repo by design — its value is as a working reference for GameShell65 game structure.
