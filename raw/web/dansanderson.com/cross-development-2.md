# Cross Development for Fun and Profit, part 2

- URL: https://dansanderson.com/mega65/cross-development-2/
- Published: July 15, 2023
- Fetched: 2026-06-11

## Overview

Compiled languages for MEGA65 development — C via llvm-mos and Rust via rust-mos. (Part 1 covered assembler choices and Xemu workflow.)

## C Programming with llvm-mos

```
./llvm-mos/bin/mos-mega65-clang -Wall -Os -o hello.prg hello.c
```

```c
#include <stdio.h>
int main() {
  puts("IT'S A C PROGRAM!\n");
}
```

Programs start at address `$2001`. Memory layout:
- Program code + heap (growing up)
- Stack (growing down from $CFFF)
- I/O registers at $D000–$DFFF
- KERNAL ROM at $E000–$FFFF

### Important Limitations

- No `float` or `double` types
- Limited C standard library
- Returning from `main()` may cause display artifacts
- Character values use ASCII, not PETSCII
- Direct memory access requires careful pointer dereferencing

### Alternatives

cc65, KickC, Calypsi (covered in Calypsi-part-1 article).

## Rust Programming

Tools: **rust-mos** (compiler), **mos-hardware** (MEGA65 register library), **mos-hardware-template** (project template).

Community discussion in MEGA65 Discord. Still an evolving area.

## Hardware Note (R4 mainboard)

R4 includes HDMI back-power fix, enhanced audio, new Real-Time Clock, bidirectional joystick ports.
