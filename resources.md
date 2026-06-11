# MEGA65 Resources

The MEGA65 is a 21st-century realization of the Commodore 65 — a real 8-bit computer running ~40x faster than a C64, with C64 and C65 compatibility, a mechanical keyboard, HD video output, Ethernet, 4 SIDs, and a fully open-source design. Built by MEGA Museum of Electronic Games & Art e.V. and sold through Trenz Electronic.

---

## Official Sites

| Resource | URL |
|---|---|
| Main website | https://mega65.org/ |
| Hardware shop (Trenz Electronic) | https://www.trenz-electronic.de/en/MEGA65-highly-advanced-C64-and-C65-compatible-8-bit-computer/TE0765-07-AK |
| File host (software, ROMs, docs) | https://files.mega65.org/html/main.php |
| Confluence wiki | https://mega65.atlassian.net/wiki/spaces/MEGA65/overview |
| GitHub organization | https://github.com/orgs/MEGA65/repositories |
| Alternative cores | https://cores.mega65.org/ |
| Try the emulator (wiki page) | https://mega65.org/try |

---

## Official Documentation (free PDFs)

All books are built from source and hosted on mega65.org. Download links point to the latest builds.

| Book | Direct link |
|---|---|
| User's Guide | https://mega65.org/user-guide |
| Developer's Guide | https://mega65.org/developer-guide |
| BASIC 65 Reference | https://mega65.org/basic65-ref |
| Chipset Reference (VIC-IV, 45GS02, 45E100) | https://mega65.org/chipset-ref |
| Complete Compendium ("The MEGA65 Book") | https://mega65.org/mega65-book |
| User's Guide (GitHub source) | https://github.com/MEGA65/mega65-user-guide |
| Welcome Guide PDF (Dan Sanderson) | https://files.mega65.org/files/m/mega65welcomeguide_RKhnNO.pdf |

Print-on-demand version of the User's Guide (2nd Edition) is available via Lulu.

---

## Emulator

**Xemu** is the primary cross-platform emulator (Linux / macOS / Windows). You need a `mega65.rom` file — owners can get it from the Filehost member area or the SD card inside the machine.

| Resource | URL |
|---|---|
| Xemu GitHub | https://github.com/lgblgblgb/xemu |
| Xemu wiki — getting started | https://github.com/lgblgblgb/xemu/wiki/Mega65-emulation-how-to-start |
| Xemu install guide (The Oasis BBS) | https://theoasisbbs.com/installing-xemu-emulator-for-mega65/ |
| Wiki: Try the emulator | https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/12648455/Curious+about+the+MEGA65+Want+to+try+the+emulator |

---

## Development Tools

### Assemblers
- **ACME** — native 45GS02 support, popular choice for MEGA65 cross-development
- **Kick Assembler** — a modified build supports the 45GS02 instruction set
- **EasyAsm** — on-device assembler for the MEGA65 by Dan Sanderson: https://github.com/dansanderson/easyasm65

### File Transfer & Utilities
- **M65Connect** — GUI tool for file management over USB/serial: https://github.com/MEGA65/m65connect
- **mega65-tools** (command-line, includes `mega65_ftp` and `etherload`): https://github.com/MEGA65/mega65-tools
- **mega65-symbols** — symbols source generator: https://github.com/dansanderson/mega65-symbols

### Example Code
- **mega65-code-snippets** — meta-repo with example code: https://github.com/MEGA65/mega65-code-snippets
- **Mega65Tutorials (RetroCogs)** — 45GS02 assembly tutorials: https://github.com/RetroCogs/Mega65Tutorials
- **bf-mega65** — Brainfuck interpreter (Dan Sanderson): https://github.com/dansanderson/bf-mega65

---

## Learning Resources

### Dan Sanderson's Hub (highly recommended starting point)
- Main page: https://dansanderson.com/mega65/
- **MEGA65 Welcome Guide** (HTML, PDF): https://dansanderson.com/mega65/welcome/
- Resources page: https://dansanderson.com/mega65/welcome/resources.html
- Joining the community: https://dansanderson.com/mega65/welcome/joining-community.html
- **Cross Development for Fun and Profit** series: https://dansanderson.com/mega65/cross-development/
- Game of Life in assembly (tutorial): https://dansanderson.com/lab-notes/mega65-game-of-life-in-assembly/
- **Dan's MEGA65 Digest** — monthly newsletter and podcast: subscribe at dansanderson.com/mega65/

### RetroCogs Blog & Tutorials
- Blog: https://retrocogs.mega65.com/
- Tutorial list: https://retrocogs.mega65.com/category/tutorials/
- Upcoming tutorials: https://retrocogs.mega65.com/upcoming-tutorials/
- GitHub (45GS02 tutorials): https://github.com/RetroCogs/Mega65Tutorials

### retroCombs (Spencer Byrd)
- Resource page: https://retrocombs.com/mega65
- User's Guide Chapter 1 walkthrough: https://retrocombs.com/mega65-ug-1
- YouTube User's Guide series: https://www.youtube.com/playlist?list=PLRVBh2hjFTomDGwIT7uPMJv4zH9JAUSVG

### Wiebow's Blog
- Cross development guide: https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/
- Blog: https://wiebow.mega65.com/

### Paul Gardner-Stephen's Developer Blog
- C65GS blog: https://c65gs.blogspot.com/ (historical development notes from the lead engineer)

### Lyonsden Blog
- User's Guide 2nd Edition review: https://lyonsden.net/mega65-users-guide-2nd-edition/

### AmigaLove Quick Start
- https://www.amigalove.com/viewtopic.php?p=14805

---

## YouTube Channels & Playlists

| Channel / Playlist | URL |
|---|---|
| Official MEGA65 channel | https://www.youtube.com/@MEGA65retro |
| Official beginner playlist | https://www.youtube.com/playlist?list=PLPehmjqZolWArdt53pl1QyJurZDu3oJKy |
| retroCombs channel | https://www.youtube.com/channel/UCjdKGdIl5leQfhJZiHUYFbQ |
| retroCombs User's Guide series | https://www.youtube.com/playlist?list=PLRVBh2hjFTomDGwIT7uPMJv4zH9JAUSVG |

---

## Community

| Platform | URL / Info |
|---|---|
| **Discord** (main real-time community, 2000+ members) | https://discord.gg/5DNvESf — also https://discord.com/invite/5DNvESf |
| **Forum64** (official support forum, searchable) | https://www.forum64.de — needs separate registration |
| **Reddit** | r/mega65 |
| **Facebook** fan club | https://www.facebook.com/groups/178458645027/ |
| **Mastodon bot** (@mega65files) | announces new Filehost uploads |

> **Discord tip:** After joining, type `!register` in `#mega65` to register your device and get the owner role.

---

## Software & Games

- **MEGA65 Filehost** — primary repository for games, demos, utilities, ROMs: https://files.mega65.org/html/main.php
- New 2024 MEGA65s ship with 191 software titles across three intro disk menus
- Plays thousands of C64 games via the built-in C64 compatibility mode
- **Alternative FPGA cores**: C64 (with IEC, cartridge, REU), Galaga, Game Boy/GBC, ZX Spectrum (ZX Uno), and more at https://cores.mega65.org/

---

## Hardware Reference

| Topic | Detail |
|---|---|
| CPU | 45GS02 (extended MOS 65CE02 branch), ~40x C64 speed |
| Video | VIC-IV, HD output |
| Audio | 4× SID chips |
| Memory | Extended RAM beyond C64/C65 |
| Storage | Dual SD card slots, VFAT32 |
| Connectivity | Ethernet (45E100 chip), USB, IEC |
| OS | MEGA-OS hypervisor + BASIC 65 + freezer |
| FPGA board | Trenz TE0765 (Xilinx Artix-7) |
| Models | R3/R3A (injection-molded + mechanical keyboard), R6 (2024) |
| DevKit | Pre-production version (100 units) |
| Alt hardware | Nexys A7 FPGA board can also run the MEGA65 core |

---

## Key GitHub Repositories

| Repo | Description |
|---|---|
| https://github.com/MEGA65/mega65-core | Main FPGA core |
| https://github.com/MEGA65/mega65-user-guide | User's Guide source (LaTeX) |
| https://github.com/MEGA65/mega65-rom-public | ROM changelog and public releases |
| https://github.com/MEGA65/mega65-tools | Command-line dev tools |
| https://github.com/MEGA65/mega65-code-snippets | Example code meta-repo |
| https://github.com/MEGA65/m65connect | GUI file manager |
| https://github.com/lgblgblgb/xemu | Xemu emulator |
| https://github.com/RetroCogs/Mega65Tutorials | 45GS02 assembly tutorials |
| https://github.com/dansanderson/easyasm65 | On-device assembler |
| https://github.com/dansanderson/mega65-symbols | Symbols generator |

---

## Merchandise & Accessories

- **Trenz Electronic shop** — official hardware source
- **COMMAND Webshop** — apparel and accessories
- **Zazzle** — 45GS02 CPU reference mousepads and posters (via Dan Sanderson's store)

---

## C64-Wiki Entry

Background reference comparing MEGA65 to the Commodore 65: https://www.c64-wiki.com/wiki/mega65
