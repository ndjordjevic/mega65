# Racing the Beam

- URL: https://dansanderson.com/mega65/racing-the-beam/
- Published: May 31, 2024
- Fetched: 2026-06-11

## Overview

Precisely timed programs using raster interrupts on the MEGA65: IRQ/NMI handling, disabling the KERNAL, custom interrupt handlers, and a practical SID music playback example.

## Timing Devices

1. **CPU**: 40.5 MHz; 1–6 cycles per instruction typically.
2. **VIC chip**: raster beam position in $D011 (bit 7) and $D012 (lower 8 bits); PAL = 312 lines at 50 Hz; NTSC = 262 lines at 60 Hz.
3. **CIA chip**: 1 MHz countdown timers; up to 65,535 pulses.

## Interrupts

- **IRQ**: can be disabled via `sei`; re-enabled with `cli`.
- **NMI**: cannot be disabled; triggered by Restore key, CIA #2 timers, RS-232.
- CPU completes current instruction, pushes PC + flags to stack, jumps to handler at $FFFE–$FFFF (IRQ) or $FFFA–$FFFB (NMI).

## Setting Up Custom Handlers (disabling KERNAL)

```assembly
lda #0
tax : tay : taz
map          ; disable IRQs and update MAP register

lda #<irq_handler
sta $fffe
lda #>irq_handler
sta $ffff

lda #0
sta $d01a    ; disable VIC IRQs
lda #$7f
sta $dc0d    ; disable CIA1 IRQs
sta $dd0d    ; disable CIA2 IRQs

eom          ; re-enable IRQs
```

## Raster Interrupts

```assembly
lda #200
sta $d012        ; raster line
lda $d011
and #$7f
sta $d011
lda #$01
sta $d01a        ; enable raster IRQ
```

Handler structure: preserve registers (pha/phx/phy/phz), acknowledge via `$d019`, do work, restore, `rti`.

## VIC-IV Extensions

Horizontal raster position interrupts: set bit 6 of $D07A, write X position to $D050–$D051, enable via bit 4 of $D01A.

## Performance Note

At 40.5 MHz the MEGA65 has ~2,600 cycles per raster line — far more than C64's 64 cycles.

## Example: SID Music Playback (BASIC)

```basic
10 BLOAD "FROGGER.SID",P($4F84)
20 SYS $5000
30 BORDER 0
40 VSYNC 100
50 BORDER 1
60 SYS $59F0
70 GOTO 30
```
