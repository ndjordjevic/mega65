# MEGA65/m65dbg

## Metadata
- Stars: 13
- Primary language: C
- Default branch: master
- Latest release: none
- License: GNU General Public License v3.0
- Homepage: (none)
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/m65dbg

## Description
An enhanced remote serial debugger/monitor for the mega65 project

## README

# m65dbg
The "m65dbg" tool is a command-line based enhanced remote serial debugger/monitor for the mega65 project. In brief, some of its facilities include:

* Capable of being a symbolic debugger (for code compiled with Ophis, ACME or CC65)
* Disassemble any point of memory (showing original file-listing, if available)
* Print out memory values in byte, word, dword or string form
* Watch such memory values continuously as you debug and step through code
* Save and load chunks of memory between the MEGA65 and your local PC
* Provide a backtrace that you can comfortably move up and down through
* Search through memory for a sequence of bytes or string
* Take petscii screenshots of current screen context (borrowed from m65 tool)
* Remote-typing mode (borrowed from m65 tool)
* FTP access to SD-card (borrowed from mega65\_ftp tool)
* You can also connect m65dbg to the serial-monitor provided by the xemu mega65 emulator

# Latest documentation

Latest detailed documentation can be found here:

* https://docs.google.com/document/d/1cEhHvvc1E47UgSoXvKPpwnf43l20sLPY-y-ZuQ4b_ng

# The raw monitor

The m65dbg app adds enhanced commands on-top of the existing commands provided by the raw monitor.

Documentation for this raw monitor exists for it in the following locations:

* The MEGA65 Compendium: https://mega65.org/docs
* C65GS System Notes
  * https://docs.google.com/document/d/1fmEUg6hDdWRb2tFZ3n4LG7S1mNP04_SUAW5DrE8zRpk/edit#
  * See the "**4.3 Remote Serial Monitor (handy for debugging)**" section
* https://github.com/Ben-401/c65gs/blob/dockit/doc/monitor.md
  * Some extra usage info exists in this page of Ben's fork of the github repo
* Typing "?" within the monitor (via your terminal app) to see a list of slightly outdated commands

The source for the m65dbg app is available here:

* https://github.com/MEGA65/m65dbg

# Video walkthroughs of m65dbg

These videos are highly-recommended watching, in order to get quickly acquainted with the facilities available in the m65dbg tool:

* m65dbg walkthrough
  * https://www.youtube.com/watch?v=2VT8yB3odhg
* m65dbg updates
  * https://www.youtube.com/watch?v=Rumti6AzsKY

# Walkthrough

Here's some written points below:

* Should build fine in Windows+Cygwin and Linux.
  * Take a look at the latest docs to learn of build pre-requisites:
    * https://docs.google.com/document/d/1cEhHvvc1E47UgSoXvKPpwnf43l20sLPY-y-ZuQ4b_ng
* Mac OSX presently doesn't support the 2,000,000 bps serial speed. So as an alternative, you can make m65dbg instead talk to the xemu mega65 emulator via a unix socket.
* Specify your serial port with the "**-l**" (or "**--device**") parameter, E.g., "**m65dbg -l /dev/ttyUSB1**"

Try the following steps:

* **./m65dbg -l /dev/ttyUSB1**
* **r** (to print out current registers)
* **b<addr>** = a raw command to set a hardware breakpoint
* **t1** (to turn trace mode on, a bit like ctrl-c breaking inside gdb)
* **t0** (to turn trace mode off, a bit like doing 'c'/continue in gdb)
* **n** (my 'next'/step-over command, which uses the hardware's step-into command multiple times, can be very slow)
* **s** (my 'step-into' command, which just calls the hardware's step-into)
* **[ENTER]** key will repeat the last command
* **finish** (my 'step-out-of' command, which calls 'n'/next multiple times, can be very slow, depending on how busy the current function is)
* **pb/pw/pd/ps** <addr> = prints byte/word/dword/string values at the given address
* typing "**help**" will give you the list of m65dbg commands, while typing "**?**" will give you the list of raw commands.

## Top-level structure

Flat C source repo — no subdirectories for source. All code at top level:

- `main.c` (8.2 KB) — entry point, argument parsing, main loop
- `commands.c` (177.8 KB) — core: all enhanced debugger commands (symbolic debug, breakpoints, step/next/finish, memory ops, backtrace, watch)
- `commands.h` (4.6 KB)
- `m65.c` (77.1 KB) — m65-tool functions (serial comms, hardware interaction) incorporated from mega65-tools
- `m65.h` (0.9 KB)
- `mega65_ftp.c` (71.0 KB) — FTP-to-SD-card functions incorporated from mega65-tools
- `ftphelper.c` (87.9 KB) / `ftphelper.a65` (2.5 KB) — FTP helper, includes assembly component
- `gs4510.c` (8.2 KB) / `gs4510.h` (0.4 KB) — 45GS02 CPU register structures
- `serial.c` (9.3 KB) / `serial.h` (0.3 KB) — serial port abstraction (Linux/Windows/macOS/Cygwin)
- `screen_shot.c` (26.9 KB) / `screen_shot.h` (0.3 KB) — PETSCII screenshot capture
- `op4502.txt` (5.9 KB) — 45GS02 opcode table for disassembly
- `Makefile` (1.0 KB) — build for Linux/Cygwin/macOS targets
- `m65dbg.zip` (1.6 MB) — pre-built Windows binary
- `LICENSE`, `.gitignore`
