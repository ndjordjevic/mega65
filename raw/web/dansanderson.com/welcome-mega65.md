# Welcome to the MEGA65

- URL: https://dansanderson.com/lab-notes/welcome-mega65/
- Published: June 12, 2022
- Fetched: 2026-06-11

## Overview

Dan Sanderson's first MEGA65 article: what the machine is, how it works, compatibility modes, documentation, and community resources.

## Hardware Summary

- Cherry MX keyswitches in Commodore layout; PETSCII symbols + RUN/STOP + RESTORE + 14 function keys
- 3.5" floppy with refurbished ALPS mechanism
- Xilinx Artix-7 FPGA emulates C65 hardware with enhancements
- Primary storage via microSD card (D81 disk image files)
- OS loads from SD card (licensed original C65 code + bug fixes + new features)

## Operating Modes

- **MEGA65 mode**: boots to BASIC 65 prompt
- **C64 mode**: `GO64` command; limited compatibility (MEGA65 CPU doesn't fully implement 6510 quirks)
- **C64 Core**: fuller C64 compatibility at the expense of MEGA65 features

## Documentation

- Official MEGA65 User's Guide included with machine
- Dan created supplementary Welcome Guide for early batch recipients
- Batch #2 preorders: €666.66 (~$815 USD with shipping)

## Budget Alternatives

- Digilent Nexys A7-100T FPGA board (~$299) — runs MEGA65 firmware
- Xemu emulator — free, runs on PC/Mac/Linux

## Community

~2,400 expected users by end of 2022. Dan contributes features to the ROM.
