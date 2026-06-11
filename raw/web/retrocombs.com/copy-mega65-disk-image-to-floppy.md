# Copy a MEGA65 .D81 disk image to a 3.5" floppy disk

- URL: https://retrocombs.com/copy-mega65-disk-image-to-floppy
- Published: 2022-08-19
- Fetched: 2026-06-11

## Overview

Tutorial for transferring a `.D81` disk image from SD card onto a physical 3.5" floppy using the MEGA65's internal drive.

## Key Technical Content

- Hardware: 3.5" floppy, SD card, MEGA65 floppy bay
- Commands:
  - `MOUNT` — mount floppy to drive 8
  - `DIR U12` — list SD card contents
  - `MOUNT <FILENAME>,U9` — mount disk image to drive 9
  - `BACKUP U9 TO U8` — copy image to physical floppy
  - `DIR` — verify floppy contents
- Unit/drive scheme: 8 = floppy, 9 = mounted image; copying is slow
