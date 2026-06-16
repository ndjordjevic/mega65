---
type: source
source_url: https://github.com/MEGA65/m65connect
tags: [gui-tool, file-transfer, sd-card, rom-configurator, d81, xojo, cross-platform, remote-interaction]
related: [MEGA65-mega65-tools, dansanderson-homebrew-mega65, mega65.atlassian.net]
product: m65connect
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**M65Connect** is the official cross-platform GUI for MEGA65 remote interaction, written in Xojo (Windows, Mac, Linux). Where [[MEGA65-mega65-tools]] provides CLI tools for file transfer and serial monitoring, M65Connect wraps those capabilities — plus SD card management, ROM configuration, D81 image editing, and remote keyboard — in a graphical interface accessible to users who prefer not to use the command line. It is available as a macOS Homebrew package via [[dansanderson-homebrew-mega65]]. Full documentation lives at [[mega65.atlassian.net]].

_All claims below are sourced from ../../raw/github/MEGA65-m65connect.md unless otherwise noted._

## What it does

Connects to a MEGA65 via LAN or USB JTAG (TE0790-03) and provides:

**File operations:** Send PRG, SID, Bitstream, Hickup, ROM files; modify and send BASIC programs; start/stop PRG autoload; create/apply ROM patch files; drag-and-drop; SD Card Manager for direct SD access; ROM Configurator; D81 image create and manipulate; directory copy (V2.5).

**Command operations:** Reset MEGA65; switch C64/C65 mode; switch graphic mode; take screenshot; connect/disconnect at runtime; remote keyboard; terminal mode for direct serial interaction.

## Installation

Download binaries (Windows, Mac, Linux) from https://files.mega65.org. Mac users can also install via the [[dansanderson-homebrew-mega65]] tap. Project source in `Code/` (Xojo project); `Resources/` folder must exist at `.../Documents/Mega65Resources/Mega65Connect`.

## Key features

- LAN and JTAG/USB connection options
- SD Card Manager: browse, copy, rename, mount D81 images
- ROM Configurator: patch and deploy custom ROMs
- Remote keyboard: type on MEGA65 from PC
- Terminal mode: direct serial interaction without switching tools
- V2.5 (2025-11-09): latest stable; V2.3 added LAN; V2.0 added D81 support

## Architecture

Single Xojo GUI project (`Code/`). Bundles pre-compiled CLI tools from [[MEGA65-mega65-tools]] (`mega65_ftp`, `m65`, etc.) in `Resources/`. The GUI acts as a front-end that calls these tools for actual hardware communication.

## Example usage

1. Connect MEGA65 via LAN or JTAG
2. Open M65Connect → File Operations → Send PRG
3. Use SD Card Manager to mount a D81 and load programs without removing the SD card

## Maintenance status

13 stars, 1 fork, GPL-3.0, last pushed 2026-05-18, default branch `master`. Actively maintained; V2.5 released November 2025. No formal release tags in the GitHub repo — track latest via [[files.mega65.org]].
