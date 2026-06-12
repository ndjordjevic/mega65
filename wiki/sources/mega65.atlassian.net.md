---
type: source
source_url: https://mega65.atlassian.net/wiki/spaces/MEGA65/overview
tags: [confluence-wiki, community-documentation, basic-65-howtos, release-notes, compatible-hardware, tutorials, m65connect, system-development]
related: [mega65.org, wiebow.mega65.com, MEGA65-mega65-core, MEGA65-mega65-rom-public]
product: mega65-wiki
detail_level: standard
created: 2026-06-10
updated: 2026-06-12
---

The official **MEGA65 Confluence wiki** — community-collaborative documentation space with nine top-level sections covering newcomer onboarding, BASIC 65 how-tos, cross-development tools, compatible hardware, FPGA/system internals, and release notes. Write access via Discord (admins: gardners, deft, dddaaann, lydon); anonymous access shows structure and loads most pages fine individually. Full page index in `../../raw/web/mega65.atlassian.net/space-structure.md`.

_All claims below are sourced from ../../raw/web/mega65.atlassian.net/ unless otherwise noted._

_Page URLs follow the pattern `https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/{id}`. Structure captured via REST API 2026-06-12._

## Sections

| Section | URL | What it covers | Pages |
|---|---|---|---|
| Introduction | [/21856261](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21856261/Introduction) | Newcomer onboarding: Documentation Landing Page (PDF links + key resources), emulator quick-start | 2 |
| MEGA≡VISION | [/36732962](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/36732962/MEGA+VISION) | Community project-showcase event; event recap, technical prep notes, presentation ideas | 3 |
| M65Connect | [/48365569](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48365569/M65Connect) | PC↔MEGA65 bridge app (Windows/Mac/Linux): terminal, SD card manager, remote keyboard, GUI docs | 8 |
| BASIC 65 How-tos | [/21790721](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21790721/BASIC+65+How-tos) | Short practical recipes: Sprite Editor walkthrough, retrieving sprite data from BANK4 | 2 |
| Tutorials / Documents / Utils | [/2129921](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/2129921/Tutorials+Documents+Utils) | Main technical hub: system setup, flashing, cross-dev tools, VIC-IV/DMA/memory internals, release verification | 27 |
| Compatible Hardware | [/15204364](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/15204364/Compatible+Hardware) | Community-tested monitors, SD cards, keyboards (Nexys4), HDMI splitters, video capture, accessories | 7 |
| System Development | [/21823561](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21823561/System+Development) | FPGA/VHDL/hardware internals for core contributors: UART monitor, QSPI, HYPPO, viciv.vhdl | 16 |
| Old wiki contents | [/1835053](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/1835053/Old+wiki+contents) | Empty — migrated dokuwiki content redistributed to other sections | 0 |
| MEGA65 Releases | [/folder/724860932](https://mega65.atlassian.net/wiki/spaces/MEGA65/folder/724860932) | Canonical release notes: 0.97.2 R6A bugfix (Feb 2026), 0.97 10th Anniversary (Feb 2026) | 2 |

---

## Introduction (2 pages)

| Page | Description |
|---|---|
| ['Documentation' - Landing Page](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21331992) | Hub linking all official PDFs (User's Guide, BASIC 65 Ref, Developer Guide, Chipset Ref, Compendium) — starting point for spec lookups |
| [Curious about the MEGA65? Want to try the emulator?](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/12648455) | Newcomer quick-start: what the MEGA65 is, how to install and run Xemu without hardware |

## MEGA≡VISION (3 pages)

| Page | Description |
|---|---|
| [MEGA≡VISION #1](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/31948801) | Recap of the first community showcase event: project submissions and presentations |
| [MEGAVISION technical preparations](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/35258369) | Technical setup notes for hosting/presenting at a MEGA≡VISION event |
| [Upcoming Presentation Ideas](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/36667407) | Crowdsourced list of potential topics for future MEGA≡VISION events |

## M65Connect (8 pages)

Desktop app for connecting a PC to the MEGA65 over USB/serial. Covers the full app reference.

| Page | Description |
|---|---|
| [Requirements](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48693566) | System requirements for installing and running M65Connect |
| [Connect PC to MEGA65](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48824339) | How to establish the USB/serial connection between the PC and MEGA65 |
| [GUI](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48791557) | Overview of the M65Connect graphical interface layout |
| [Functions](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48791570) | Reference for M65Connect's available functions and commands |
| [Terminal](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48660493) | Using M65Connect's serial terminal to interact with the MEGA65 |
| [Remote keyboard](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48791589) | Typing on the MEGA65 from a PC keyboard via M65Connect |
| [SD Card Manager](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48693601) | Browsing, copying, and managing files on the MEGA65's SD card from the PC |
| [Settings](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/48693612) | Configuration options for M65Connect (port, baud rate, preferences) |

## BASIC 65 How-tos (2 pages)

| Page | Description |
|---|---|
| [Dabbling with sprites in BASIC and the Sprite Editor](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/11763713) | Beginner walk-through of defining and animating BASIC 65 sprites using the built-in Sprite Editor |
| [How to retrieve sprite data from BANK4?](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21889040) | Explains how sprite data stored in BANK4 RAM can be accessed from BASIC 65 |

## Tutorials / Documents / Utils (27 pages)

The main technical content hub. Covers system setup, ROM/SD maintenance, cross-dev tools, VIC-IV/DMA internals, and release verification.

| Page | Description |
|---|---|
| [Basic System Setup](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/15302687) | First-time MEGA65 setup: SD card formatting, ROM flashing, initial configuration |
| [What should I update?](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/4554753) | Decision guide for which components (ROM, core, bitstream) need updating and when |
| [Visual Guide to Flashing Slot 0 without JTAG](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/83689488) | Illustrated step-by-step guide to flashing the core via MEGAFLASH (no JTAG programmer needed) |
| [MEGAFLASH Testing](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/177209351) | Community testing notes for the MEGAFLASH core-flashing tool (updated Jan 2026) |
| [Bitstream and Corefile Know-How](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/86638602) | Explains the difference between .bit (JTAG) and .cor (MEGAFLASH) files and how core slots work |
| [Dumping and restoring sd-card contents](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/6258696) | How to back up and restore the full SD card image using standard tools |
| [Tips on formatting floppy disks](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/21233665) | Formatting .D81 disk images for use with the MEGA65's virtual or physical drive |
| [Diff'ing .D81 files](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/2981895) | How to compare two .D81 disk image files to spot differences between releases or backups |
| [Default color palette](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/4685825) | Documents the MEGA65's default VIC-IV color palette values |
| [Transitioning programs to use ROM 920373](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/5603329) | Migration guide for programs that broke when the ROM updated to version 920373 |
| [BASIC 65 Keyword Abbreviations](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/22609921) | Quick-reference table of BASIC 65 keyword abbreviations (single-keystroke entry shortcuts) |
| [Using petcat for cross-developing BASIC programs](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/27492353) | How to write BASIC 65 on a PC using petcat to convert plain text → tokenized PRG file |
| [remote typing on the MEGA65](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/26902533) | Techniques for sending keystrokes to the MEGA65 remotely (via mega65_ftp or similar) |
| [Ethernet tools (mega65_ftp and etherload)](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/29327361) | How to use mega65_ftp (file transfer) and etherload (direct PRG injection) over Ethernet |
| [VIC Registers, Memory Map, DMA, Audio DMA](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/27590657) | Community reference for key VIC-IV registers, the memory map, and DMA/audio-DMA usage |
| [Memory Mapping](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/33259521) | How MEGA65 memory banking, the MAP instruction, and address spaces work |
| [DMA Insights](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/49807361) | Deep-dive into the F018/F018A DMA controller: modes, options, and gotchas |
| [FCM Insights and Experimentation](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/28344336) | Practical notes on Full-Colour Mode (FCM) character and sprite display |
| [Kernel Jump Table](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/6619137) | Community-documented KERNAL ROM jump table entries for calling OS routines from assembly |
| [MEGA65 System Startup Flow](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/158924822) | Documents the boot sequence from power-on through HYPPO to the BASIC 65 prompt |
| [Super simple Protovision-compatible Joystick Expander](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/7012353) | DIY hardware design for adding a second joystick port using the Protovision protocol |
| [Libraries](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/316866561) | Index of community libraries available for MEGA65 development |
| [Eleven Walkthrough](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/34209812) | Walkthrough and notes for the original MEGA65 game "Eleven" |
| [MegaWAT!?](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/35979266) | Documentation for MegaWAT, a community utility tool |
| [Release verification 0.97](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/346882049) | Community testing checklist and results for the 0.97 10th Anniversary release |
| [Release verification 0.96](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/82313234) | Community testing checklist and results for the 0.96 R6 hardware batch |
| [Release verification 0.95](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/8716289) | Testing instructions and tips for verifying a 0.95 batch #2 unit |

## Compatible Hardware (7 pages)

| Page | Description |
|---|---|
| [Monitors](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/4292609) | Community-tested monitors with HDMI compatibility notes (resolution, refresh rate, DVI mode) |
| [HDMI Splitters to resolve HDMI backpower issue](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/22806529) | Recommended HDMI splitters that fix the backpower/noise issue on some monitors |
| [Video capture adaptors](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/23920641) | Tested HDMI capture cards for recording MEGA65 output on a PC |
| [Keyboards that work with Nexys4 boards](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/1802278) | USB keyboards confirmed to work with the Nexys4 FPGA dev-board MEGA65 port |
| [SD-cards](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/41287681) | Tested SD cards: brands, capacities, formatting requirements, known incompatibilities |
| [VONETS WiFi-Ethernet Bridge adaptor](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/24576037) | How to use a VONETS WiFi-Ethernet bridge to give the MEGA65 wireless network access |
| [Community Accessories](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/24182805) | Index of community-made accessories: cases, keyboard overlays, cartridge adapters, etc. |

## System Development (16 pages)

FPGA/VHDL/hardware-level documentation for contributors to the MEGA65 core.

| Page | Description |
|---|---|
| [MEGA65 Development Guidelines](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/209518696) | Coding standards and workflow for contributing to the MEGA65 FPGA core and firmware |
| [UART Monitor Studies](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/3178497) | Research notes on the built-in UART monitor (debug interface over serial) |
| [Deciphering Uart Monitor's register details](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/32899174) | Detailed breakdown of UART monitor register read/write commands and responses |
| ["viciv.vhdl" studies](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/30539781) | Community analysis of the VIC-IV VHDL source to understand rendering internals |
| [HYPPO mode programs](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/34111489) | How to write programs that run in HYPPO (hypervisor) mode on the 45GS02 |
| [System Partition details](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/166985770) | Documents the SD card system partition: slot layout, FDISK header, reserved sectors |
| [QSPI Flash Information](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/33128465) | Reference for the QSPI flash chip (capacity, sectors, erase timing) used in R3/R6 hardware |
| [QSPI issue](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/6029313) | Documents a known QSPI flash reliability issue and workaround |
| [Magic pokes into the config sector (via mega65_ftp)](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/22380545) | How to modify the MEGA65 config sector using mega65_ftp for low-level settings |
| [bit2core arguments](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/22872067) | Command-line reference for bit2core (converts .bit bitstream to .cor core file) |
| [JTAG/Serial drivers under Windows](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/27197441) | Installing JTAG and USB-serial drivers on Windows for MEGA65 development |
| [Creating libusb / libpng .deb packages](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/11304961) | How to build .deb packages for libusb and libpng needed by MEGA65 tools on Debian/Ubuntu |
| [Old Slot 0 Flashing process (pre Release 0.96)](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/30932993) | Legacy JTAG flashing process for slot 0 (superseded by MEGAFLASH in 0.96+) |
| [New keyboard scanner (v0.96 feature candidate)](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/44204033) | Design notes for the improved keyboard scanning logic added in the 0.96 release |
| [MEGA65 Style Cartridge (Work in Progress)](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/36962324) | Hardware design notes for creating a MEGA65-compatible cartridge |
| [hyppotest](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/5373953) | Test framework and notes for testing HYPPO (the MEGA65 hypervisor) |

## MEGA65 Releases (2 pages)

Canonical release notes — complement [[MEGA65-mega65-rom-public]] for ROM-specific changes.

| Page | Date | Description |
|---|---|---|
| [Release 0.97.2 - Bugfix Release for the MEGA65 R6A board revision](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/725614593) | Feb 2026 | Patch release targeting R6A hardware issues; full bug/fix summary |
| [Release 0.97 - 10th Anniversary Edition](https://mega65.atlassian.net/wiki/spaces/MEGA65/pages/725024771) | Feb 2026 | Major release celebrating 10 years; complete feature notes and known issues |

---

## When to use

- **First setup**: Basic System Setup → What should I update? → Visual Guide to Flashing
- **Cross-development**: Ethernet tools, petcat, remote typing, Memory Mapping (complement [[wiebow.mega65.com]])
- **Hardware compatibility**: Compatible Hardware section — monitors, SD cards, HDMI splitters
- **VIC-IV / DMA internals**: VIC Registers page, FCM Insights, DMA Insights, Memory Mapping
- **Release notes**: Releases folder here + [[MEGA65-mega65-rom-public]] for ROM CHANGELOG
- **FPGA internals**: System Development section + [[MEGA65-mega65-core]]
- Fetch individual pages directly by URL — anonymous Confluence space-level rendering is unreliable

## Ecosystem

Complements [[mega65.org]] (official site + PDF books) and [[MEGA65-mega65-user-guide]] (greppable spec). The Ethernet tools and petcat pages overlap with [[wiebow.mega65.com]] and [[dansanderson.com]]. Release notes pair with [[MEGA65-mega65-rom-public]] (ROM CHANGELOG).
