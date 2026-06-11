# MEGA65 User's Guide Chapter 5 — Upgrading

- URL: https://retrocombs.com/mega65-ug-5
- Published: 2024-08-28
- Fetched: 2026-06-11

## Overview

How to upgrade and manage cores, ROMs, and system files: the core selection menu, flashing cores to slots, installing alternate cores/ROMs, and the boot process.

## Key Technical Content

- Three upgrade components: Core (FPGA config), ROM (OS/BASIC), system software
- Version check: Information Utility via Freezer menu (hold RESTORE ~1s, then HELP)
- Files: download from files.mega65.org after redeeming owner code
- Core Selection Menu: hold NO SCROLL during power-on; slots 0–7
- Upgrading cores: copy `.cor` to microSD root; Slot Editor (CTRL + slot number); flash with F8
- Multiple ROMs: name `MEGA65x.ROM` (x = 0–7); boot one by holding number key 0–7 at startup
- Core flags via Slot Editor: default core, cartridge behavior, C64/C128 compatibility
- Erase slots: F4 in Slot Editor; slots 1–7 replaceable (0 reserved)
- Boot: HYPPO hypervisor manages core loading, ROM selection, FPGA init
