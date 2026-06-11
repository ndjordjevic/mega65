# Install the MEGA65 Emulator on the Clockwork uConsole

- URL: https://retrocombs.com/mega65-uconsole
- Published: 2023-10-14
- Fetched: 2026-06-11

## Overview

Build and run the Xemu MEGA65 emulator on a Clockwork uConsole to make a portable MEGA65 handheld. Argues for official bare-metal support ahead of the MEGAphone.

## Key Technical Content

- Hardware: Clockwork uConsole, Raspberry Pi CM4 (Pi 3+ class)
- Prereqs: assemble device, Raspbian SD card, run system updates
- Packages: `git build-essential libsdl2-dev libgtk-3-dev libreadline-dev`
- Build: clone Xemu repo, `make`; emulators land in `build/bin`; MEGA65 target at `targets/mega65/`
- Run: `build/bin/xmega65.native`
- ROM: download latest stable ROM, update via emulator's Disks/SD-card menu
- Formats: `.d81` images, BASIC 65 development
