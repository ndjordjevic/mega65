# Patch the Original Commodore 65 ROM for the MEGA65, Xemu, Dev Kit, or Nexys4

- URL: https://retrocombs.com/patch-c65-rom
- Published: 2021-12-17
- Fetched: 2026-06-11

## Overview

Obtain the original C65 ROM, patch it with MEGA65 improvements, and deploy across Xemu and FPGA hardware — a working alternative to the incomplete open-source ROM.

## Key Technical Content

- ROM file: `910828.BIN` (original C65 ROM, 1991-10-01)
- Tool: M65Connect (Mac/Linux/Windows)
- Patch file: "C65 ROM diff files" from MEGA65 FileHost
- Process: point-and-click in M65Connect — select source ROM + diff, save as `MEGA65.ROM`
- Deploy — Xemu: right-click → Disks | SD-card | Update files on SD image; FPGA: rename to `MEGA65.ROM`, copy to SD card
- Tested on Xemu, Nexys4, Dev Kit; works with modern demos and C64 mode
