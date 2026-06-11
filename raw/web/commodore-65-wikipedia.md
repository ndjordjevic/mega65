# Commodore 65 — Wikipedia

- URL: https://en.wikipedia.org/wiki/Commodore_65
- Fetched: 2026-06-11
- Note: encyclopedia background on the C65 (C64DX) prototype — the machine the MEGA65 recreates.

## Overview

The Commodore 65 (a.k.a. **C64DX**) was a prototype developed by Commodore Business Machines in **1990–1991** as an enhanced, backward-compatible successor to the C64, reaching toward Amiga-level capabilities. It was cancelled before release; the MEGA65 is its modern FPGA recreation.

## Hardware specifications

**CPU**
- **CSG 4510 R3** (a 65CE02 derivative with integrated CIAs, UART, memory mapper)
- Clock **3.54 MHz** (vs C64's ~1 MHz); 1 MB addressable space

**Memory**
- **128 KB** RAM standard, expandable to **8 MB** max; **128 KB** ROM
- Dual 8-bit memory banks (64 KB each) → 7.2 MB/s video bandwidth

**Graphics — VIC-III (CSG 4567 R5)**
- Palette of **4,096** colors (256 on-screen)
- Modes: 320×200×256, 640×200×16, 640×400×16, 1280×200×4, 1280×400×4
- All VIC-II modes, bitplanes, genlock sync, integrated DMA/blitter

**Audio**
- **Two CSG 8580R5 SID** chips (C64 had one); stereo with independent L/R

**Storage**
- Internal 3.5" DSDD floppy (**880 KB**); C1581-compatible; supports external 1541/1571/1581

**I/O**
- 77-key keyboard with inverted-T cursor block
- 2 control ports (DE9M), 50-pin expansion, CBM-488 bus (6-pin DIN), 24-pin user port, stereo RCA, RGBA video (DE9F), RF/composite, external floppy (mini-DIN-8), RAM expansion

**OS:** Commodore **BASIC 10.0** (far beyond C64's BASIC 2.0)

## History

- Conceived **1990** by engineer **Fred Bowen** and others; decision finalized end of 1990.
- Cancelled in **1991** by Commodore chairman Irving Gould — diminishing C64 sales, Nintendo's market dominance, and internal sales-vs-engineering conflict.
- On Commodore International's **1994** liquidation, an estimated **50–2,000** prototype units reached the open market.

## Relationship to C64 / C128

A direct evolutionary step from the C64 with full backward compatibility and big jumps in speed, BASIC, graphics, and audio. The **C128** (1985, 1–2 MHz) was the last 8-bit Commodore actually released before the C65's cancellation.

## MEGA65 connection

Announced **2015** by the Museum of Electronic Games & Art (m-e-g-a.org); recreates C65 hardware in FPGA with modern connectors (HDMI, microSD, LAN). Milestones: 100 dev kits by end-2020; 400-unit batches sold out May 2022 and May 2023; readily available without batch limits as of Oct 2024.
