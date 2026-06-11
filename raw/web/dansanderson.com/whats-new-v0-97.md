# What's New in v0.97

- URL: https://dansanderson.com/mega65/whats-new-v0-97/
- Published: March 25, 2025
- Fetched: 2026-06-11

## Overview

v0.97 feature overview and community testing invitation. Significant release after 14 months of v0.96.

## New User Features

- D64 disk mounting from Freezer and via `MOUNT` command
- Disk noise toggle in Configuration
- Up to 10 alternate ROMs on SD card (numbered 0–9)
- `DIR` command: pattern matching + pause functionality
- `TYPE` command: pause flag

## BASIC 65 Enhancements

- **Binary literals**: `%1010` syntax
- New functions: `DECBIN()`, `STRBIN$()` for binary conversion
- **5-button joystick support** via `JOY()`
- Enhanced `RPALETTE()` with system palette access
- Improved sprite support with high-resolution registers
- **Raw mode for `BSAVE`** (matching `BLOAD` raw functionality)
- Unsigned 16-bit range for extended bitwise operations

## Developer Features

- DMA addresses spanning megabyte boundaries
- **Audio DMA IRQ triggers** for sample buffering
- Core selection menu support for cartridge protocol
- Serial debugger interrupt handling improvements
- New KERNAL routines: `SAVEFL`, `GETIO`, `GETLFS`, `KEYLOCKS`, `ADDKEY`

## Hardware Support

- DIY keyboard support for R4–R6 boards
- Wukong A100T V2 platform compatibility

## Testing Links

- Core builds: builder.mega65.org
- Beta ROM: files.mega65.org?id=mega65-rom-beta
- Bug reports: GitHub mega65-core/issues or mega65-rom-public/issues
