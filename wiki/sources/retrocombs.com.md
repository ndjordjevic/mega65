---
type: source
source_url: https://retrocombs.com/mega65
tags: [users-guide-series, getting-started, xemu, fpga-build, nexys4, rom-patching, basic-65, c64-mode, mega65-tools, keyboard, mouse, sd-card, livestreams]
related: [mega65.org, dansanderson.com, files.mega65.org, lgblgblgb-xemu]
product: retrocombs
detail_level: standard
created: 2026-06-10
updated: 2026-06-11
---

Steven Combs' (retroCombs) MEGA65 site — the most beginner-friendly, hands-on corner of the ecosystem. Where [[dansanderson.com]] goes deep on programming internals, retroCombs covers **getting started and living with the machine**: setup, configuration, emulator install on every platform, building a MEGA65 on an FPGA dev board, ROM patching, BASIC 65 conversions, and accessory guides. The centerpiece is his **User's Guide Series** (a video + blog walkthrough of the official manual, chapter by chapter). This wiki indexes his **32 original blog posts** plus the two site sections; the broad external link directory on his resource page is summarized below and overlaps `resources.md`.

**How to use this page:** the tables are an index — each row links to a raw page under `../../raw/web/retrocombs.com/`. Those raw pages are **condensed summaries**, not full copies. For the complete article (every step and screenshot), open the `- URL:` at the top of the raw page. Answer chain: this index → raw summary → original URL.

_All claims below are sourced from ../../raw/web/retrocombs.com/ unless otherwise noted._

---

## Site sections (not blog posts)

| File | URL | Summary |
|---|---|---|
| [resource-page.md](../../raw/web/retrocombs.com/resource-page.md) | /mega65 | The "all things MEGA65" link hub: his content + a curated external link directory (Essentials, Cores, Tools, Gear, etc.). Mostly pointers — overlaps `resources.md`, [[mega65.org]], [[files.mega65.org]] |
| [users-guide-series.md](../../raw/web/retrocombs.com/users-guide-series.md) | /mega65-users-guide | Index of the User's Guide Series: 10 planned topics, chapters 1–5 published |

---

## Blog posts (all 32, newest first — matches the index at /mega65-blog)

| Date | Article | Summary |
|---|---|---|
| 2024-08-28 | [mega65-ug-5.md](../../raw/web/retrocombs.com/mega65-ug-5.md) | **User's Guide Ch5 — Upgrading:** cores/ROMs/system files, Core Selection Menu, `.cor` flashing, Slot Editor, multiple `MEGA65x.ROM`, HYPPO boot |
| 2024-06-01 | [mega65-ug-4.md](../../raw/web/retrocombs.com/mega65-ug-4.md) | **User's Guide Ch4 — Configuring:** Configuration Utility (ALT+power), Input/Chipset/Video/Audio/Network pages, two SD slots, SD Card Utility |
| 2024-05-20 | [mega65-ug-3.md](../../raw/web/retrocombs.com/mega65-ug-3.md) | **User's Guide Ch3 — Getting Started:** keyboard, screen editor, input methods, `FONT`, Freezer menu, `GO64`/C64 core |
| 2024-03-31 | [mega65-ug-2.md](../../raw/web/retrocombs.com/mega65-ug-2.md) | **User's Guide Ch2 — Setup:** unboxing to first boot, ports, RTC battery, onboarding config keys, video modes |
| 2024-03-12 | [mega65-ug-1.md](../../raw/web/retrocombs.com/mega65-ug-1.md) | **User's Guide Ch1 — Introduction:** what the MEGA65 is, accessories, the documentation set, community |
| 2023-10-14 | [mega65-uconsole.md](../../raw/web/retrocombs.com/mega65-uconsole.md) | Build Xemu on a Clockwork uConsole (Pi CM4) for a portable handheld; package list + `make targets/mega65` |
| 2023-04-23 | [mega65-primer.md](../../raw/web/retrocombs.com/mega65-primer.md) | A ~14-min BASIC 65 video primer (with Gürçe); `TEMPO`/`PLAY`, Xemu, CBM prg Studio |
| 2022-11-19 | [xanadu-bas-demo.md](../../raw/web/retrocombs.com/xanadu-bas-demo.md) | BAS group's Syntax 2022 demo — first MEGA65 demoparty entry to showcase VIC-IV; asm + BASIC |
| 2022-10-02 | [mega65-laptop.md](../../raw/web/retrocombs.com/mega65-laptop.md) | Portable dev setup: ThinkPad + C64 key labels + Xemu + Google Drive sync to hardware via USB-TTL |
| 2022-08-19 | [copy-mega65-disk-image-to-floppy.md](../../raw/web/retrocombs.com/copy-mega65-disk-image-to-floppy.md) | Copy a `.D81` to a physical 3.5" floppy: `MOUNT`, `DIR U12`, `BACKUP U9 TO U8` |
| 2022-08-13 | [hibernated1.md](../../raw/web/retrocombs.com/hibernated1.md) | Playing Hibernated 1 (Z-machine interactive fiction); nautical commands, color config, `MOUNT`/`BOOT` |
| 2022-08-01 | [mega65-on-chromeos.md](../../raw/web/retrocombs.com/mega65-on-chromeos.md) | Xemu on ChromeOS via Linux containers; Intel `.deb` vs ARM `make deb`, `.desktop` launcher |
| 2022-07-01 | [master-mega65-keyboard-addendum.md](../../raw/web/retrocombs.com/master-mega65-keyboard-addendum.md) | Keyboard addendum: `MEGA65#.ROM` booting, `SHIFT+RETURN`, `HELP` error find, `KEY` reprogramming, `NEW RESTORE` recovery |
| 2022-06-04 | [mega65-usb-ttl.md](../../raw/web/retrocombs.com/mega65-usb-ttl.md) | Cheap DSD USB-TTL serial link to a Mac (set **3.3V!**); `m65`/`mega65_ftp` over `/dev/USB` |
| 2022-05-28 | [master-mega65-keyboard.md](../../raw/web/retrocombs.com/master-mega65-keyboard.md) | Full keyboard guide: command keys, CTRL color codes, F1–F16, escape sequences, 32-color palette |
| 2022-04-23 | [c64-on-mega65-livestream3.md](../../raw/web/retrocombs.com/c64-on-mega65-livestream3.md) | C64 demos from the onboarding SD card, part III; 13 demos with `LOAD` commands; CSDB references |
| 2022-03-28 | [basic65-sub-track-update.md](../../raw/web/retrocombs.com/basic65-sub-track-update.md) | Submarine-tracker update; the "Combs Flag" circle parameter (4 = start at 270°), `LINE`/`SPEED`/`SLEEP` |
| 2022-03-19 | [c64-on-mega65-livestream2.md](../../raw/web/retrocombs.com/c64-on-mega65-livestream2.md) | C64 games/demos part II; `LOAD`, `SYS 2064`, 4-player Multiplayer Interface |
| 2022-03-07 | [sub-track-sys.md](../../raw/web/retrocombs.com/sub-track-sys.md) | Converting a C128 submarine-tracking BASIC program to BASIC 65; v7 vs BASIC 65 graphics differences |
| 2022-02-23 | [c64-on-mega65-livestream.md](../../raw/web/retrocombs.com/c64-on-mega65-livestream.md) | C64 demos/games part I; SID music, onboarding SD card C64 disk image |
| 2022-02-17 | [ten-mega65-vs-mac.md](../../raw/web/retrocombs.com/ten-mega65-vs-mac.md) | Playful MEGA65-vs-M1 list; immediate-mode BASIC, `FAST`/`SPEED`, `EDIT`, ports, core slots, RGB LEDs |
| 2022-01-03 | [mega65-core-testing-livestream.md](../../raw/web/retrocombs.com/mega65-core-testing-livestream.md) | Faster core flasher (90s vs 10–15min); `LIST P`, `DIR W`, `SYS 58552` C64→MEGA65 |
| 2021-12-26 | [mega65-xmas-eve.md](../../raw/web/retrocombs.com/mega65-xmas-eve.md) | Christmas Eve stream; box art + onboarding SD card preview; Ethernet BBS; Poopie BASIC game |
| 2021-12-17 | [patch-c65-rom.md](../../raw/web/retrocombs.com/patch-c65-rom.md) | Patch the original C65 ROM (`910828.BIN`) with M65Connect → `MEGA65.ROM`; deploy to Xemu/Nexys4/DevKit |
| 2021-11-09 | [mega65-nexys4.md](../../raw/web/retrocombs.com/mega65-nexys4.md) | Build a MEGA65 on a Nexys4/A7 FPGA (~$270); microSD prep, key mappings, Matrix Debugger |
| 2021-10-25 | [mega65-nexys4-livestream.md](../../raw/web/retrocombs.com/mega65-nexys4-livestream.md) | Livestream of the Nexys A7 bitstream install; keyboard-compatibility troubleshooting with devs |
| 2021-08-31 | [xemu-on-mac.md](../../raw/web/retrocombs.com/xemu-on-mac.md) | Install Xemu on macOS; Mac key mappings, ROM update, drag-and-drop `.d81`/`.PRG`, `GO64` |
| 2021-08-28 | [mega65-tools.md](../../raw/web/retrocombs.com/mega65-tools.md) | Build mega65-tools on Intel/M1 Macs; Homebrew `libusb-compat`, `gh repo clone`, `m65`/`mega65_ftp` |
| 2021-07-26 | [mega65-3.md](../../raw/web/retrocombs.com/mega65-3.md) | "Ten cool things"; hardware/CPU/memory rundown, cores, MEGAphone |
| 2021-03-20 | [mouster.md](../../raw/web/retrocombs.com/mouster.md) | mouSTer USB→DB9 mouse adapter; firmware `.fw` update, `.ini` config, C1351 mode needs real SID |
| 2021-02-04 | [mega65-2.md](../../raw/web/retrocombs.com/mega65-2.md) | Updating a Dev Kit: SD files, Kernal ROM, core bitstream, M65Connect; `.cor` flashing, SD format |
| 2020-12-01 | [mega65-1.md](../../raw/web/retrocombs.com/mega65-1.md) | The first post — DevKit unboxing/assembly; acrylic case, GEOS, Freezer, ~40× a C64 |

---

## External link directory (on the resource page)

The resource page also curates non-retroCombs links — Official Information, Essentials, Cores, Technical Documents, Tools, Community, Gear — almost all pointing to [[mega65.org]], [[files.mega65.org]], GitHub, or shops. These are cataloged in `resources.md` and captured in [resource-page.md](../../raw/web/retrocombs.com/resource-page.md); they are not given individual raw pages. Note its "alternative cores" link is the older sy2002.github.io/m65cores list — the current catalog is cores.mega65.org.

## When to use

For onboarding and operational how-tos: first setup, configuration, running Xemu on your OS, building a MEGA65 on an FPGA board, patching the C65 ROM, or a guided video walkthrough of the official User's Guide. For programming depth (assembly, VIC-IV internals, KERNAL), prefer [[dansanderson.com]].

## Ecosystem

Links into every major hub: [[mega65.org]], [[files.mega65.org]], [[lgblgblgb-xemu]] (Xemu), [[dansanderson.com]] (Digest), MEGA65 GitHub, Discord, Forum64, Reddit, and accessory shops (Trenz, COMMAND, mouSTer, Tank Mouse).
