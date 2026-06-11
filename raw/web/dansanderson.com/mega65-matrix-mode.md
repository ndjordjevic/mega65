# Using MEGA65's Matrix Mode

- URL: https://dansanderson.com/lab-notes/mega65-matrix-mode/
- Published: July 31, 2022
- Fetched: 2026-06-11

## Overview

The Matrix Mode debugger: what it is, how to access it (on-device and via serial/JTAG), core commands, and how it differs from the regular monitor.

## What is Matrix Mode?

The MEGA65 has an inner C65-like system surrounded by an outer Hypervisor shell. Matrix Mode runs in the outer layer, allowing:
- Pausing the CPU entirely
- Single-stepping through machine code
- Watching for specific changes to PC, registers, or memory
- Debugging **without modifying program code** (no `brk` statements needed)

## Accessing the Debugger

**On-device**: hold Mega key + Tab while program runs.

**Via serial connection** (2,000,000 baud, 8N1):
- M65Connect (Windows/Mac/Linux) — multi-tool
- PuTTY / HyperTerminal (Windows); Serial / picocom (Mac/Linux)

Note: only one PC app can access the serial port at a time.

## Core Commands

| Command | Action |
|---|---|
| `m [addr]` | Display 16 bytes; repeat to continue |
| `M [addr]` | Display 256 bytes |
| `d [addr]` | Disassemble 1 instruction |
| `D [addr]` | Disassemble 16 instructions |
| `r` | Display all registers + flags (NVEBDIZC) |
| `t1` | Enter trace mode (pauses CPU) |
| `t` / Enter | Execute one instruction |
| `t0` | Resume full speed |
| `tc` | Run continuously + dump registers per instruction |
| `b [addr]` | Set breakpoint; `b` clears it |
| `w [addr]` | Set memory watch (pauses on value change); `w` clears |
| `g [addr]` | Jump execution to address |
| `s [addr] [bytes]` | Set memory (absolute addressing) |
| `S [addr] [bytes]` | Set memory (relative to CPU map) |
| `f [start] [end+1] [val]` | Fill memory region |
| `i1` / `i0` | Disable/enable interrupts |

## Addressing

- 16-bit addresses: access first 64 KB
- 28-bit addresses: access full MEGA65 memory
- Prefix `777` + 16-bit address to interpret within CPU's current memory map

## Custom Tools

Python + PySerial can automate queries and extract game state for terminal display.
