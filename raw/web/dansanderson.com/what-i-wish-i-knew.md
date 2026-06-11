# What I Wish I Knew About Machine Language

- URL: https://dansanderson.com/mega65/what-i-wish-i-knew/
- Published: February 14, 2023
- Fetched: 2026-06-11

## Overview

An accessible introduction to machine language on the MEGA65 for beginners: bits/bytes/hex, the 45GS02 CPU architecture, instructions and addressing modes, and using the built-in monitor.

## Addressing the Computer

```
POKE $D020,$04  : REM border color via register
PRINT HEX$(53280)  : REM decimal to hex conversion
```

I/O registers occupy $D000–$DFFF.

## Bits, Bytes, Hex

- 1 bit = 0 or 1; 8 bits = 1 byte (0–255)
- Hex digit = 4 bits; 2 hex digits = 1 byte
- MEGA65 uses 28-bit addressing (vs C64's 16-bit)

## CPU Architecture (45GS02)

- 4 general-purpose registers: A (accumulator), X, Y, Z
- Program counter (PC), stack pointer (SP), status flags (NVEBDIZC)
- Base page: 256 bytes of fast-access memory at $0000

## Key Instructions

```assembly
LDA $1900   ; load accumulator from address
LDX #$FF    ; load X with immediate value
STA $D020   ; store accumulator to address
ADC #$1A    ; add to accumulator
AND $C901   ; bitwise AND
BNE $180C   ; branch if not equal
JMP $18FF   ; jump to address
JSR $1900   ; jump to subroutine (RTS returns)
PHA / PLA   ; stack push/pull
TXA         ; transfer X to A
```

## Machine Language Monitor

```
MONITOR         ; enter from BASIC
M1800           ; display memory at $1800
A 1800 INC $D020  ; assemble instruction
D 1800          ; disassemble
J 1800          ; call subroutine
X               ; exit to BASIC
```

Direct POKE approach:
```
POKE $1800,$EE : POKE $1801,$20 : POKE $1802,$D0 : POKE $1803,$60
SYS $1800
```
= `INC $D020 / RTS`

## Mega Assembler

On-device assembler with labels:
```
BORDER=$D020
  *=$1800
START
  INC BORDER
  JMP START
```

## Learning Resources

- MEGA65 Chipset Reference: full 45GS02 instruction set
- *Machine Language for Beginners* — Richard Mansfield (Archive.org)
- *Machine Language for the Commodore 64* — Jim Butterfield (Archive.org)
