# c65gs.blogspot.com

## Fetch log
- Inbox URL: https://c65gs.blogspot.com/2022/10/mega65-mk-ii-keyboard-pcb-design.html
- Final URL: https://c65gs.blogspot.com/2022/10/mega65-mk-ii-keyboard-pcb-design.html
- Fetched: 2026-06-13
- Pages: 2
- Mode: standard

## Landing page — https://c65gs.blogspot.com/

Blog: C65GS development blog by Paul Gardner-Stephen (MEGA65 co-creator). Current focus (2025–2026) is MEGAphone — a cellular-capable retro computer device built on the MEGA65 platform, funded by the NLnet Foundation.

Recent posts (landing page, most recent first):
1. MEGAphone Hardware Module Progress Update (2026-01-18) — https://c65gs.blogspot.com/2026/01/megaphone-hardware-module-progress.html
2. MEGAphone Cellular Modem Voice Circuit Control (2026-01-02)
3. MEGAphone Cellular Modem and Power Control Hook-up for R3 Boards (2026-01-01)
4. MEGAphone Cellular Modem Communications: SMS Messaging (2025-12-17)
5. MEGAphone User Interface and Text Messaging Software (2025-12-14)
6. MEGAphone Power Management FPGA and Software Interface (2025-12)

The 2022 MK-II keyboard PCB post is an earlier entry (not visible on current landing page; accessed directly by URL).

## MK-II Keyboard PCB Design — https://c65gs.blogspot.com/2022/10/mega65-mk-ii-keyboard-pcb-design.html

Author: Paul Gardner-Stephen. Published: October 2022.

### Overview

Paul Gardner-Stephen announced a redesigned keyboard PCB for the MEGA65, created to address semiconductor supply chain challenges ("Chipaggedon") affecting the original FPGA-based (Lattice) keyboard design. The post explains the design rationale for replacing the Lattice FPGA controller with six I2C IO expander chips.

### Why the redesign?

The original MK-I keyboard used a Lattice FPGA as the controller. The COVID-era chip shortage made this part unobtainable, requiring a complete redesign. The new design prioritises:
- Using parts available in current chip market conditions
- Easier DIY assembly for community members with FPGA dev boards
- Cost reduction relative to the previous design

### Component Selection

Six I2C-based IO expander chips, each providing 16 I/O lines. Gardner-Stephen: "These chips cost only about AU$3 each in small quantities" and can be daisy-chained via address straps to support the keyboard's full key count.

The design eliminates the need for key switches with internal diodes, reducing per-switch cost by approximately AU$0.20 × 80 keys, which "quite literally just about pay for themselves" relative to the IO expander costs. Cherry MX clone switches at approximately AU$40 for the full set are now usable.

### Technical specs

- I2C protocol at 400 KHz
- Key sampling at >1 KHz with less than 1 ms latency
- Each key wired directly to a GPIO pin (separate wiring, no matrix)
- Unlimited simultaneous key presses (full NKRO)
- Three-wire communication compatible with existing MEGA65 hardware (third line held low for MK-I vs MK-II auto-detection)

### Companion repo

GitHub: https://github.com/mega65/mega65-kbd-pcb (KiCad project files — schematics, PCB layout, gerbers)
