---
type: source
source_url: https://github.com/MEGA65/mega65-kbd-pcb
tags: [keyboard, pcb-design, kicad, hardware, i2c, nkro, mk-ii, cherry-mx, open-hardware]
related: [MEGA65-mega65-core, c65gs-mk-ii-keyboard]
product: mega65-kbd-pcb
detail_level: standard
created: 2026-06-13
updated: 2026-06-13
---

The MK-II keyboard PCB design for the MEGA65 — a KiCad open-hardware project that replaces the MK-I design's Lattice FPGA-based controller with six I2C IO expanders, making it buildable from currently available parts and enabling full N-key rollover (NKRO) without per-key diodes. Created by Paul Gardner-Stephen (2022) in response to COVID-era chip shortages ("Chipaggedon") that made the original Lattice part unobtainable. The MK-II keyboard is the current R6 production keyboard.

_All claims below are sourced from ../../raw/github/MEGA65-mega65-kbd-pcb.md unless otherwise noted._

## What it does

Provides the complete KiCad PCB project for the MEGA65 MK-II mechanical keyboard — schematics, PCB layout, footprint library, and component references. The design allows community members to have their own boards manufactured from the gerber/drill files and assemble them with readily available off-the-shelf parts.

## Key features

- **I2C IO expander architecture:** six I2C IO expanders replace the MK-I's Lattice FPGA controller, using only 2 of the 3 available IO lines (SDA/SCL). The third line is tied low, enabling the MEGA65 core to auto-detect keyboard model (MK-I vs MK-II) at boot.
- **Full NKRO:** each key is wired directly to a GPIO pin on an IO expander — no key matrix, no diodes needed. All keys can be pressed simultaneously without rollover issues.
- **Cherry MX compatible:** accepts any Cherry MX or compatible key switch; switches do not need built-in diodes. Two switch positions (CAPSLOCK and SHIFT LOCK) expect LED-fitted switches.
- **RGB LEDs:** 4× Würth RGB LEDs (part 156120M173000), two per side, for CAPSLOCK and SHIFT LOCK indicator lighting; 330 Ω (LED) and 130 Ω (RGB) through-hole resistors.
- **10-pin connector:** 2×5 2.54mm male pin header for the keyboard cable; optional 4-pin GPIO header not currently used.
- **Hand-solderable SMD:** surface-mount chips are sized for hand soldering with bridge-and-wick technique.

## Architecture

The keyboard connects to the MEGA65 mainboard through a 10-pin header. The MK-I used CLK/SYNC, OUT, and IN for a custom serial protocol driven by a Lattice FPGA on the keyboard itself. The MK-II eliminates the keyboard-side FPGA entirely: the MEGA65 FPGA core communicates directly with the IO expanders over I2C using two lines, while the third (previously CLK/SYNC) is held low as an auto-detection signal. The KiCad project files are the primary deliverable: `mega65-kbd.kicad_sch` (top-level schematic), `keyswitches.kicad_sch` (key switch sub-sheet), and `mega65-kbd.kicad_pcb` (PCB layout, 5.5 MB).

## Installation

To build a MK-II keyboard:

1. Export gerber and drill files from the KiCad project; send to a PCB manufacturer.
2. Source components: 78 Cherry MX (or compatible) switches, 4 Würth RGB LEDs (156120M173000), 2× 330 Ω and 12× 130 Ω through-hole resistors, 10-pin header.
3. Assemble: SMD chips on the front (MEGA65 logo side); key switches inserted from the back. The two LED switch positions are marked on the PCB.
4. Source or print MEGA65 keycaps; add spacers for correct set-back in the MEGA65 top-case (exact dimensions TBD — README notes the project is new and assembly details will be updated after first build).
5. A metal stabilizer plate is optional if using PCB-mount switches.

## Example usage

The repository is a KiCad hardware project, not a software tool — there is no code to run. To use it, open `mega65-kbd.kicad_pro` in KiCad, review the schematics, and generate manufacturing outputs (File → Fabrication Outputs → Gerbers).

## Maintenance status

6 stars, 3 forks. License: CC-BY-SA 4.0 (Paul Gardner-Stephen, 2022). Open Hardware Certification applied for. Default branch: `master`. No formal releases; last pushed 2024-03-29. The repo uses a `library/` git submodule for KiCad library assets. No documentation beyond the README.
