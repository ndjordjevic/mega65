---
type: source
source_url: https://wiebow.mega65.com/2023/12/31/cross-development-for-the-mega65/
tags: [cross-development, kick-assembler-45gs02, etherload, mega65-ftp, c1541-d81, xemu, matrix-mode-debugger, build-automation]
related: [dansanderson.com, retrocogs.mega65.com, mega65.atlassian.net, RetroCogs-Mega65Tutorials, MEGA65-mega65-tools, lgblgblgb-xemu]
product: wiebow
detail_level: standard
created: 2026-06-10
updated: 2026-06-10
---

Wiebo de Wit's end-to-end cross-development setup guide (Dec 2023): a complete, working Linux toolchain that assembles 45GS02 code with the Kick Assembler 65CE02 fork, builds a D81 disk image, and deploys to both Xemu and a real MEGA65 over Ethernet — all from one `make.sh` triggered by Ctrl-B in the editor, with a verified 3.3-second edit-build-run loop. The most copy-pasteable build pipeline among this wiki's sources; complements the broader tool survey in [[dansanderson.com]].

_All claims below are sourced from ../../raw/web/wiebow.mega65.com.md unless otherwise noted._

## What it does

Documents every ingredient of a MEGA65 assembly cross-dev environment: assembler, editor with syntax highlighting, disk-image tool, emulator, hardware deployment, and debugger — then automates them in a single shell script.

## Key features

- **Assembler**: Kick Assembler requires Jesper Gravgaard's modified build (`KickAss65CE02-x.y.jar`, gitlab.com/jespergravgaard/kickassembler65ce02) for the 45GS02 instruction set; needs Java. Source files start with the directive `.cpu _45gs02`.
- **Disk images**: Kick can only emit D64 (not mountable on MEGA65), so `c1541` from VICE creates and fills D81s: `c1541 -format "disk,0" d81 out.d81` then `-attach … -write main.prg main`.
- **Deployment, two paths**: serial JTAG-over-USB (Linux: user must be in the dialout group) or — the author's choice, "the way forward" — direct Ethernet using `mega65_ftp -e` (copy D81 to SD card) and `etherload -5 -m disk.d81 -r main.prg` (`-5` forces the post-load reboot; omitting it hangs the machine). Linux needs IPv6 link-local enabled on the interface; re-activate the connection after power-cycling the MEGA65.
- **Emulator run**: `xemu-xmega65 -besure -prgmode 65 -prg main.prg`.
- **Editor integration**: Sublime Text with a 45GS02 syntax file (github.com/wiebow/M65_KickAsm_Macros) and a build system that just calls `./make.sh`.
- **BASIC-stub pattern in Kick syntax**: the test program hand-assembles a `BANK 0:SYS <addr>` BASIC line at $2001 (`.word`/`.byte`/`.text toIntString(start)`) with code at $2011 — the same launcher idiom Dan Sanderson shows for Acme.
- **Debugging**: the Matrix Mode Monitor (MEGA+TAB on hardware; Xemu right-click → Debug → Matrix mode) inspects/modifies memory, shows CPU registers, sets breakpoints; commands documented in MEGA65 Book Appendix K.

## Architecture and concepts

The pipeline is a classic toolchain: KickAss65CE02 → PRG → c1541 → D81 → (Xemu | mega65_ftp + etherload). Project layout: `~/development/mega65/tools/` plus one folder per project, each with its own `make.sh`.

## Main APIs

Tool invocations worth memorizing: `java -jar KickAss65CE02.jar -vicesymbols -showmem main.asm -odir ./bin`; `mega65_ftp -e -c "put file.d81" -c "quit"`; `etherload -5 -m file.d81 -r main.prg`. Ethernet tooling setup is documented on the official Confluence page "Ethernet tools mega65_ftp and etherload".

## When to use

Follow this when standing up your own build pipeline — especially for the Ethernet-deployment specifics (IPv6 link-local, the `-5` reboot flag) that aren't spelled out elsewhere. Windows users: dirmaster and M65Connect for disk-image management.

## Ecosystem

References the Kick fork on GitLab, magic64knight.com, and the official Confluence Ethernet-tools page. Hosted on the community mega65.com subdomain family alongside [[retrocogs.mega65.com]].
