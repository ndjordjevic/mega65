# MEGA65/m65connect

## Metadata
- Stars: 13
- Primary language: Xojo
- Default branch: master
- Latest release: none (latest V2.5 released 2025-11-09 via files.mega65.org)
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/m65connect

## Description
Cross-Platform Remote Interaction Tool for the MEGA65

## README
M65Connect is a GUI tool written in Xojo for Windows, Mac, and Linux to interact with a MEGA65 over USB (JTAG TE0790-03) or LAN.

**File operations:**
- Send PRG, SID, Bitstream, Hickup, ROM files
- Modify and send BASIC programs
- Start/Stop PRG Autoload
- Create and apply ROM patch files
- Drag & Drop for supported file types
- SD Card Manager: access the internal SD card
- ROM Configurator: customise ROMs
- D81 image support: create and manipulate D81 images
- Directory copy support (V2.5)

**Command operations:**
- Reset MEGA65; switch to C64 or C65 mode
- Switch graphic mode
- Take screenshot
- Connect/disconnect at runtime
- Remote keyboard (type on MEGA65 from PC)
- Terminal mode for direct serial interaction

**Hardware requirements:** MEGA65 (prototype, DevKit, or final), connected via LAN cable or JTAG TE0790-03.

**Downloads:** https://files.mega65.org (Windows, Mac, Linux builds)

**Manual:** https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48365569/M65Connect

**Changelog highlights:**
- V2.5 (2025-11-09): Directory copy, proper window closing, latest CLI tools
- V2.4 (2025-05-10): DIR support, LAN stability
- V2.3 (2024-02-18): LAN support
- V2.2 (2023-07-05): Local SD Card support
- V2.0 (2022-07-18): D81 image support
- V1.0 (2020-08-23): Initial release

**Project setup:** Code/ folder is the Xojo project; Resources/ folder holds external dependencies (expected at `.../Documents/Mega65Resources/Mega65Connect`).

## Top-level structure
- dir Code/ — Xojo project source
- dir Resources/ — external tools and assets (mega65_ftp, m65, etc.)
- file Info.plist — macOS app metadata
- file README.md, LICENSE, .gitignore
