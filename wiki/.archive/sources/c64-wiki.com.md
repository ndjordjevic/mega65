---
type: source
source_url: https://www.c64-wiki.com/wiki/mega65
tags: [hardware-specs, gs4510, vic-iv, dmagic, hyper-ram, commodore-65-history]
related: [mega65.org]
product: c64-wiki-mega65
detail_level: brief
created: 2026-06-10
updated: 2026-06-10
---

The C64-Wiki encyclopedia article on the MEGA65 — a compact third-party hardware-spec sheet placing the machine in Commodore lineage. Flagged on-wiki as a stub and partially dated (e.g. "devkit form planned for 2020", VFAT32 "coming soon"), but its spec table is the densest single summary of the hardware among this wiki's sources.

_All claims below are sourced from ../../raw/web/c64-wiki.com.md unless otherwise noted._

## What it does

Describes the MEGA65 as a 100% open-source implementation of the never-released Commodore 65, by MEGA e.V., released 2021 at 666.66€ net, with C64 mode compatibility comparable to a C128 in C64 mode.

## Key features

- **CPU**: GS4510 — enhanced 4502, single-core, switchable 1 / 2 / 3.5 / 40.5 MHz, in-order, non-pipelined, no cache; 32-bit ZP-indirect and far-JSR/JMP/RTS operations, 28-bit address space, hypervisor traps, virtual memory. Benchmarks: Synthmark64 44.5x a C64; Bouldermark 29,970 vs C64's 313.
- **DMA**: C65 DMAgic-compatible — fills 40MB/s, copies 20MB/s, swaps 10MB/s.
- **Video**: VIC-IV, no framebuffer, native 720×576; supports all documented VIC-II modes and VIC-III modes; independent H/V hardware scaling down to 60×38; separate 256-color palettes for sprites/bitplanes/characters (up to 1,024 colors on screen); 12-bit VGA (4,096 colors), HDMI planned at 23-bit; text-mode extensions include proportional-width characters and super-extended background color mode.
- **Sound**: quad soft-SIDs + dual 8-bit DACs. **RAM**: 384KB fast RAM + 32KB color RAM visible to VIC-IV, 8MB Hyper RAM ("Attic RAM").
- **Media/IO**: D81 images from SD (300–3000 KB/s vs ~20 KB/s native floppy speed), real 3.5" floppy, VGA + HDMI + Ethernet + JTAG/USB debug, expansion port, C64-compatible disk-drive interface, two 9-pin joystick ports.
- **OS**: MEGA-OS hypervisor with integrated freezer/task switcher and VFAT32 driver; BASIC 10 or BASIC 65; GEOS; Contiki.
- **FPGA**: Xilinx Artix-7 100T (Nexys4DDR, MEGA65 PCB, TE0725) — Spartan-based boards cannot run the core.
- **Books**: lists the five official guides with page counts (Book 1069, Developer 267, User 260, BASIC 65 Ref 285, Chipset Ref 188 — at the time of writing).

## When to use

Quick hardware-spec lookups and historical context. Cross-check anything time-sensitive against [[mega65.org]] and the Confluence release notes — the article is a stub with stale corners.
