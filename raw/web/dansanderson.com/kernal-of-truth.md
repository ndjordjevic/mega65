# KERNAL of Truth

- URL: https://dansanderson.com/mega65/kernal-of-truth/
- Published: June 17, 2024
- Fetched: 2026-06-11

## Overview

The MEGA65 KERNAL: its role, how to use it from assembly, memory mapping rules for extensions, and a practical desktop clock project built as a custom IRQ extension.

## KERNAL Concepts

- **KERNAL subroutines**: call fixed jump table addresses (e.g., $FFD2 for BSOUT/chrout).
- **Jump Table**: subroutines use indirection, allowing KERNAL relocation across versions.
- **IRQ Handler**: KERNAL installs an IRQ handler for cursor blinking and BASIC animations.
- **Vectors**: KERNAL allows replacing vector table addresses to chain custom routines.

## Memory Mapping

- **BASIC Map**: most addresses point to bank 3 (OS code).
- **SYS Map**: activates when running machine code; maps only KERNAL to $E000–$FFFF.
- **"Vector routines must live within $1600 to $1EFF"** to remain accessible from both maps when returning to BASIC.

## Desktop Clock Project

A custom IRQ routine displaying the current time in the screen corner:
- Assembles at $1600
- Reads Real-Time Clock hardware registers at $0FFD7110
- Uses Binary Coded Decimal (BCD) conversion for time display
- Installs as a vector routine chaining to the original KERNAL IRQ
- Load: `BLOAD "CLOCK"`, start: `SYS $1600`
