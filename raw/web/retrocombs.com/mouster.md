# Use the Retrohax.net mouSTer on the MEGA65

- URL: https://retrocombs.com/mouster
- Published: 2021-03-20
- Fetched: 2026-06-11

## Overview

Connecting a mouSTer (USB HID → DB9 adapter) to a MEGA65 Dev Kit — worked after a firmware upgrade, enabling USB mouse support across retro environments.

## Key Technical Content

- Device: mouSTer USB HID adapter (Atari/Amiga/Commodore 1351 emulation)
- Firmware: v3.11.1962; update via USB drive with a `.fw` file
- Config: `.ini` on USB drive sets button mapping, auto-fire, emulation mode
- Modes: Atari, Amiga, C1351 (needs a real SID chip)
- Tested in Yaped32 (C65 mode), Art Studio 1351 (C64 mode), GEOS 65
- Settings: microstep/DPI divider (default 10), heartbeat LED, pull-up resistors
