---
type: source
source_url: https://github.com/lgblgblgb/xemu
tags: [emulator, sdl2, commodore-65, mega65-emulation, cross-platform]
related: [mega65.org, wiebow.mega65.com, dansanderson.com]
product: xemu
detail_level: brief
created: 2026-06-10
updated: 2026-06-10
---

Xemu by LGB (Gábor Lénárt) — the SDL2-based multi-machine emulator whose MEGA65 target (`xmega65`) is the de-facto standard MEGA65 emulator and the centerpiece of every cross-development workflow in this wiki. GPL-2.0, actively maintained since 2016.

_All claims below are sourced from ../../raw/github/lgblgblgb-xemu.md unless otherwise noted._

## What it does

Emulates the MEGA65, Commodore 65, Commodore LCD, Enterprise 128, and other 8-bit machines on Linux/Unix/Windows/macOS. The machine list reflects component reuse and the author's interests, not a product strategy.

## Key features

Branch model: `master` (stable, recommended), `next` (newer features — needed for the latest ALL_INTROS), `dev` (bleeding edge). Binaries at github.lgb.hu/xemu. Docs live on the GitHub wiki — the MEGA65 quick-start page is the canonical setup guide. Requires a `mega65.rom` (Filehost member area or the machine's SD card; MakeROM scripts can patch a C65 ROM — see [[mega65.org]]).

## When to use

Day-to-day MEGA65 development and try-before-you-buy. Usage patterns captured elsewhere in this wiki: drag-and-drop PRG/D81, `-prg`/`-prgmode 65` flags, `-hdosvirt`, `-uartmon :4510`, matrix-mode debugger ([[mega65.org]], [[wiebow.mega65.com]], [[dansanderson.com]]).

## Maintenance status

266 stars, pushed May 2026, GPL-2.0; emulator internals deliberately not captured at this detail level — consult the wiki/repo directly for build-from-source.
