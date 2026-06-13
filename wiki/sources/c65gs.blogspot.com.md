---
type: source
source_url: https://c65gs.blogspot.com/2022/10/mega65-mk-ii-keyboard-pcb-design.html
companion_urls:
  - https://github.com/MEGA65/mega65-kbd-pcb
raw_files:
  - ../../raw/web/c65gs.blogspot.com.md
  - ../../raw/github/MEGA65-mega65-kbd-pcb.md
tags: [keyboard, mk-ii, pcb-design, hardware, i2c, chip-shortage, kicad, paul-gardner-stephen, open-hardware]
related: [MEGA65-mega65-kbd-pcb, MEGA65-mega65-core]
product: c65gs.blogspot.com
detail_level: standard
created: 2026-06-13
updated: 2026-06-13
---

Paul Gardner-Stephen's October 2022 blog post on his C65GS development blog explaining the design decisions behind the MEGA65 MK-II keyboard PCB — specifically why the original Lattice FPGA controller was replaced with six I2C IO expanders. The post is the primary design rationale document for the MK-II keyboard (the current R6 production keyboard), making it an essential companion to the KiCad project files in [[MEGA65-mega65-kbd-pcb]].

_All claims below are sourced from ../../raw/web/c65gs.blogspot.com.md unless otherwise noted._

## What it does

Explains the motivation and engineering decisions behind the MEGA65 MK-II keyboard redesign. Covers: why the Lattice FPGA was dropped (COVID chip shortage); why I2C IO expanders were chosen (availability, cost, simplicity); how NKRO is achieved without diodes; and how backward compatibility with MK-I hardware is maintained via a held-low third line. The accompanying KiCad PCB project files are at https://github.com/mega65/mega65-kbd-pcb.

## Key features

The blog post documents these design properties — cross-referenced with the KiCad files in the companion repo (../../raw/github/MEGA65-mega65-kbd-pcb.md):

- **Chip shortage response ("Chipaggedon"):** the Lattice FPGA used in MK-I became unobtainable; the MK-II uses six I2C IO expander chips at ~AU$3 each, widely available on the open market. (../../raw/github/MEGA65-mega65-kbd-pcb.md)
- **NKRO without diodes:** each key wires directly to a GPIO on an IO expander — no matrix, no per-switch diodes needed. Community members save ~AU$0.20 per switch × 80 keys, roughly offsetting the IO expander cost.
- **I2C at 400 KHz:** enables >1 KHz sampling with <1 ms latency — fast enough for demanding gaming use.
- **MK-I auto-detection:** the third keyboard IO line (formerly CLK/SYNC) is held low on MK-II; MK-I keyboards do not do this. The MEGA65 core uses this signal to auto-detect keyboard model. (../../raw/github/MEGA65-mega65-kbd-pcb.md)
- **DIY-friendly:** Cherry MX clone switches (~AU$40 total), standard through-hole resistors, Würth RGB LEDs — all available without specialty sourcing.

## Architecture

The blog describes the shift from a keyboard-side intelligence model (MK-I: Lattice FPGA runs custom firmware to serialize keystrokes over a 3-wire bus) to a passive IO expander model (MK-II: MEGA65 FPGA core polls IO expanders directly over I2C using 2 of the 3 lines). Six IO expanders daisy-chained via address straps cover the full key count. (../../raw/github/MEGA65-mega65-kbd-pcb.md)

The KiCad project in the companion repo contains the full PCB design: top-level schematic (`mega65-kbd.kicad_sch`), key switch sub-schematic (`keyswitches.kicad_sch`), and PCB layout (`mega65-kbd.kicad_pcb`, 5.5 MB). (../../raw/github/MEGA65-mega65-kbd-pcb.md)

## Installation

The blog post does not include build instructions beyond pointing to the KiCad project. For assembly, see the companion repo's README at [[MEGA65-mega65-kbd-pcb]]: produce gerbers from the KiCad project, source components, and assemble per the board markings. (../../raw/github/MEGA65-mega65-kbd-pcb.md)

## Example usage

This is a design-rationale blog post, not a software project. The actionable output is the KiCad project at `github.com/mega65/mega65-kbd-pcb`; the blog provides the engineering context for why those design choices were made.

## When to use

Read this post when:
- You want to understand the hardware differences between MK-I and MK-II keyboards (relevant if writing core code or firmware that handles both).
- You want to understand the I2C IO expander architecture for MEGA65 keyboard support in [[MEGA65-mega65-core]].
- You're building a replacement keyboard PCB from the KiCad files and want the design intent behind component choices.

## Maintenance status

Single blog post, published October 2022. Blog (c65gs.blogspot.com) is maintained by Paul Gardner-Stephen (MEGA65 co-creator and FPGA lead); current focus is MEGAphone development (NLnet-funded, 2025–2026). No comments or issue tracker on the blog itself; the companion KiCad repo (6 stars) is the ongoing project artifact. (../../raw/github/MEGA65-mega65-kbd-pcb.md)

## Ecosystem

Directly companion to [[MEGA65-mega65-kbd-pcb]] (the KiCad PCB project the post describes). Relevant to [[MEGA65-mega65-core]] (the MEGA65 FPGA core which implements the I2C keyboard driver and auto-detection).
