# Calypsi C, part 1

- URL: https://dansanderson.com/mega65/calypsi-part-1/
- Published: May 25, 2026
- Fetched: 2026-06-11

## Overview

This article introduces the Calypsi C cross-compiler for developing programs in the C language on the MEGA65 computer. Sanderson explains why C complements assembly language for larger projects, guides readers through installation and basic compilation, and demonstrates practical examples of hardware access and multi-file project organization.

## Key Sections

### Calypsi Toolchain Setup

Step-by-step installation for macOS, Linux, and Windows. macOS users must override system security to install unsigned binaries. Calypsi compiles to object files, then links them using configuration like `mega65-plain.scm`.

### Compilation Walkthrough

```c
#include <stdio.h>
int main() {
  printf("HELLO WORLD!\n");
  return 0;
}
```

### PETSCII and Character Encoding

Use `--string-literals=shifted-petscii` compiler flag and mode-switching codes like `\x0e` for lowercase text.

### Standard Library and Hardware Access

```c
void main() {
  volatile char *border = (char *)0xd020;
  *border = 5;
}
```

The `mega65.h` header provides named register structures (VICIV, CIA, SID) for cleaner hardware manipulation.

### Data Types

- `char`: 8-bit, `int`: 16-bit, `long`: 32-bit, `long long`: 64-bit
- Use `stdint.h` types (`uint8_t`, etc.) for clarity and portability.

### Project Organization

Each `.c` source file compiles independently to `.o` object files; functions require declarations in `.h` header files when used across modules. GNU Make automates the build via Makefile.

### Examining Generated Code

The `--list-file` flag produces `.lst` files showing generated assembly for optimization.

## News & Related Projects

- **Elite for MEGA65**: 1984 space trading game now playable on MEGA65.
- **M65Compiler**: A competing cross-compiler specializing in upper memory access.

## Learning Resources

- *The C Programming Language, 2nd edition* (Kernighan & Ritchie, 1988)
- *C Programming: A Modern Approach, 2nd edition* (K.N. King, 2008)
- Free: Harvard CS50, *The C Book*, *Beej's Guide to C Programming*
