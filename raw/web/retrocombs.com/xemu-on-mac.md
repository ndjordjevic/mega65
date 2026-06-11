# Run a MEGA65 on your Mac using Xemu

- URL: https://retrocombs.com/xemu-on-mac
- Published: 2021-08-31
- Fetched: 2026-06-11

## Overview

Install and configure the Xemu emulator (xmega65) on macOS: setup, Mac keyboard mappings, and loading/running software.

## Key Technical Content

- Install: download Xemu DMG, drag `xmega65.app` to Applications
- ROM: right-click → SD-card → Update files on SD image → load `MEGA65.ROM`
- Mac key mappings: FN+→ for END/RUN-STOP; FN+← for HOME; F1 toggles 40/80 columns
- Function keys: F3 DIR, F8 monitor, F9 exit, F10 reset, F11 fullscreen
- Loading: default `.d81` mount; drag-and-drop `.d81`; drag-and-drop `.PRG` to run
- Config path: `~/Library/Application Support/xemu-lgb/mega65/`
- `GO64` (confirm Y) for C64 mode
- Commands: `DSAVE`/`DLOAD`, `HEADER` (format), `DIR`
