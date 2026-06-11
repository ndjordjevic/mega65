# robotfindskitten, part 3

- URL: https://dansanderson.com/mega65/robot-finds-kitten-3/
- Published: December 14, 2023
- Fetched: 2026-06-11

## Overview

Completes the assembly language robotfindskitten: keyboard input, hardware random number, timing, duplicate prevention, data organization, and full implementations in both BASIC and assembly.

## Keyboard Input

```assembly
jsr $FFE4   ; getin — A = PETSCII key, or 0 if none pressed
```

Latest ROM implements a hardware typing event queue for improved accuracy.

## Hardware Random Number

```assembly
-   bit random_ready    ; $D7FE bit 7 = ready flag
    bmi -
    lda random          ; $D7EF = random byte (0–255)
    ; A is a random number
```

For non-power-of-two ranges, re-roll to ensure even distribution.

## Timing

- CIA chip time-of-day: $DC08 (tenths of seconds)
- VIC raster counter: $D012 / $D011 — frame-precise but varies PAL (312 lines) vs NTSC (263 lines); 81% of users prefer PAL

## Duplicate Prevention

Parallel arrays: screen codes, description addresses, x/y coordinates. Custom routine checks for duplicates before accepting a placement:

```assembly
is_unique_byte:
    ; Y,Z = start of byte set; X = last item index
    ; Returns: Carry Set if not unique
    cpx #0
    beq @is_unique
    ...
```

## Data Organization

Null-terminated strings in program memory, with a 16-bit address lookup table. Python script generates the assembly from a text file:

```python
# generates:
# nki_table: !16 i0,i1,...
# i0: !pet "description",0
```

## Downloads

- `rfk-bas.prg`: complete BASIC implementation
- `rfk-asm.prg`: complete assembly implementation (Acme assembler source)
