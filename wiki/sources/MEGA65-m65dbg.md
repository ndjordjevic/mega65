---
type: source
source_url: https://github.com/MEGA65/m65dbg
tags: [debugger, serial-monitor, symbolic-debugging, breakpoints, 45gs02, step-through, ophis, acme, cc65, cross-development]
related: [MEGA65-mega65-tools, lgblgblgb-xemu, wiebow.mega65.com, dansanderson-dis65]
product: m65dbg
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**m65dbg** is the MEGA65 project's enhanced serial debugger — a command-line tool that layers symbolic debugging, breakpoints, step-through execution, memory watch, and disassembly on top of the machine's built-in raw monitor. Where [[MEGA65-mega65-tools]] handles file transfer and hardware interaction, m65dbg handles the debug session. It can connect to real hardware via serial (2 Mbps) or to [[lgblgblgb-xemu]] via Unix socket, making it usable on all three OSes without hardware.

_All claims below are sourced from ../../raw/github/MEGA65-m65dbg.md unless otherwise noted._

## What it does

Provides a GDB-like debug experience over the MEGA65's serial monitor port:

- **Symbolic debugging** — load symbol maps from Ophis, ACME, or CC65; disassemble with original source-file lines shown alongside
- **Breakpoints** — hardware breakpoints (`b<addr>`); trace mode (`t1`/`t0`) as a break/continue equivalent
- **Step commands** — `s` (step into), `n` (step over, slow — implemented via repeated hardware step-into), `finish` (step out)
- **Memory inspection** — `pb`/`pw`/`pd`/`ps` for byte/word/dword/string values; continuous watch; memory save/load between PC and MEGA65; memory search
- **Backtrace** — navigable call stack
- **PETSCII screenshots** — screen capture (from `m65` tool)
- **Remote typing** — inject keystrokes (from `m65` tool)
- **FTP to SD card** — file transfer (from `mega65_ftp` tool)

## Installation

Build from source on Linux or Windows+Cygwin (Makefile); pre-built Windows binary in `m65dbg.zip`. macOS serial at 2 Mbps is unsupported — use xemu socket mode instead. Full build prerequisites in the Google Docs guide linked from README.

Connect: `m65dbg -l /dev/ttyUSB1` (serial) or via xemu's `-uartmon :4510` socket.

## Key features

`commands.c` (178 KB) carries the full debugger implementation. The codebase incorporates large chunks from [[MEGA65-mega65-tools]]: `m65.c` for serial/hardware interaction, `mega65_ftp.c` for SD-card FTP. The 45GS02 disassembler uses `op4502.txt` (opcode table) and `gs4510.c` (CPU register structures). `serial.c` abstracts the port across Linux/Windows (Cygwin)/macOS.

Two video walkthroughs exist (linked in README) covering the full feature set — recommended viewing before first use.

## Architecture

Flat single-level C repo. m65dbg wraps the MEGA65's low-level raw monitor (documented in the Compendium and C65GS System Notes) with an enhanced command layer. The enhanced commands (`help`) sit above the raw monitor commands (`?`). Serial comms and hardware interaction code is shared with `mega65-tools`.

## Example usage

```
m65dbg -l /dev/ttyUSB1   # connect to hardware
r                         # print registers
b$1234                    # set hardware breakpoint at address $1234
t1                        # trace mode on (like break/pause)
s                         # step into
n                         # step over (slow)
pb $d020                  # print byte at $D020 (border colour register)
finish                    # step out of current routine
```

## Maintenance status

13 stars, 18 forks, GPL-3.0, last pushed Oct 2025, default branch `master`. No formal releases — consume from HEAD. Build docs in an external Google Doc (URL in README).

## Ecosystem

Sits alongside [[MEGA65-mega65-tools]] in every serious development setup — tools for transfer/flash, m65dbg for source-level debugging. Connects to [[lgblgblgb-xemu]] via socket on macOS. The wiebow cross-dev pipeline ([[wiebow.mega65.com]]) uses the built-in Matrix Mode Monitor for quick debugging; m65dbg is the step up when symbolic source-level tracing is needed.
