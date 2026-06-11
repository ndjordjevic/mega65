# Run a MEGA65 on your Chromebook using Xemu

- URL: https://retrocombs.com/mega65-on-chromeos
- Published: 2022-08-01
- Fetched: 2026-06-11

## Overview

Running the Xemu MEGA65 emulator (xmega65) on ChromeOS via Linux containers, with separate paths for Intel and ARM Chromebooks.

## Key Technical Content

- Identify architecture with Cog system info viewer (Intel vs ARM)
- Enable Linux in ChromeOS Settings; share Downloads folder with the container
- Intel: download `.deb` from Xemu page, double-click to install
- ARM: build full `.deb` with `make deb`, or emulator-only with `make targets/mega65`
- CLI: `git clone`, `make`, `nano`
- Launcher: create a `.desktop` file in `~/.local/share/applications/`
- ROM: right-click → Disks → SD-card → Update files on SD Image
- Formats: `.d81`, `.prg`
- Limitations: sound inconsistencies, no joystick USB support, keyboard mapping differences
