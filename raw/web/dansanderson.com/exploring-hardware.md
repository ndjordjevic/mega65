# Exploring MEGA65 Hardware

- URL: https://dansanderson.com/mega65/exploring-hardware/
- Published: January 16, 2023
- Fetched: 2026-06-11

## Overview

MEGA65 hardware deep dive: FPGA internals, board revision history, supported peripherals, and future hardware projects (MEGAPhone, port expansion board, DIY keyboard).

## Hardware Highlights

- Cherry MX keyswitches in Commodore layout; injection-molded casing.
- Xilinx Artix-7 FPGA (main chip); Altera MAX10 + Lattice chip for keyboard management.
- HDMI, VGA, Ethernet, 2× DE-9 joystick ports, SD card, 3.5" floppy (refurbished ALPS).

## Board Revisions

- R1, R2: not distributed
- R3 (DevKit, 2020): acrylic cases, 100 units
- R3A: retail; 8 core slots; 8 MB Attic RAM
- R4: HDMI back-power fix, enhanced audio, new RTC, bidirectional joystick
- R6 (2024): bidirectional cartridge/joystick, extra SDRAM for alt cores

Early devs used Digilent Nexys A7-100T FPGA board (~$350) — can still run MEGA65 firmware (lacks Attic RAM).

## Peripherals

- Joysticks: vintage Commodore/Atari DE-9; ArcadeR; mouSTer USB adapter
- Mouse: Commodore 1351 (proportional); modern adapters
- Storage: external 1581 via IEC (timing quirks); microSD as primary

## Future Projects

- **MEGAPhone**: NLNet-funded mobile device with MEGA65 tech + cellular; modular design.
- **Port Expansion Board**: component video, Commodore user port, tape port, C1565 floppy connector.
- **DIY Keyboard**: lower-cost design without separate FPGA, available as kit.
