---
type: source
source_url: https://github.com/MEGA65/mega65-libc
tags: [c-library, cc65, llvm-mos, fat32, file-io, cross-development, cmake, mega65-api]
related: [cc65-cc65, MEGA65-mega65-fdisk, MEGA65-mega65-freezemenu, MEGA65-mega65-weeip]
product: mega65-libc
detail_level: standard
created: 2026-06-12
updated: 2026-06-12
---

**mega65-libc** is the official C library for MEGA65, providing hardware-specific APIs on top of the [[cc65-cc65]] toolchain and (alternatively) Clang/LLVM-MOS. It is a dependency of [[MEGA65-mega65-fdisk]] and [[MEGA65-mega65-freezemenu]], and the natural starting point for any new CC65 or LLVM-MOS C project targeting the MEGA65.

_All claims below are sourced from ../../raw/github/MEGA65-mega65-libc.md unless otherwise noted._

## What it does

Provides C-language APIs for MEGA65 hardware: FAT32 file I/O, POSIX-like directory access, and MEGA65-specific I/O in `include/mega65/`. The library bridges the gap between the CC65 standard C runtime and the MEGA65's hypervisor-based filesystem.

Key APIs (FAT32):
```c
void closeall(void);
unsigned char open(char *filename);
void close(unsigned char fd);
unsigned short read512(unsigned char fd, unsigned char *buffer);
```
Directory: `m65_dirent` struct; POSIX-like `opendir`, `readdir`. Constraint: only one file or directory can be open at a time; always call `closeall()` before opening.

## Installation

**CC65:** `export USE_LOCAL_CC65=1; make -f Makefile_cc65`. Include `.c` and `.s` files from `src/` directly in CC65 projects.

**LLVM-MOS:** `cmake -DCMAKE_PREFIX_PATH=$HOME/llvm-mos -B build && cd build && make [install]`.

**CPM.cmake:** `CPMAddPackage(NAME mega65libc GITHUB_REPOSITORY mega65/mega65-libc GIT_TAG development)`.

## Key features

- Supports both CC65 and Clang/LLVM-MOS toolchains
- FAT32 file and directory access via MEGA65 hypervisor
- MEGA65-specific hardware headers in `include/mega65/`
- Doxygen API docs (`make doc`); LaTeX output for MEGA65 User Guide (`make guide`)
- Pre-commit hooks with clang-format; GitHub Actions CI

## Architecture

`src/` — C and assembly sources (`.c` and `.s` pairs for CC65, `.c` only for LLVM-MOS). `include/mega65/` — MEGA65-specific headers. `cmake/` — CMake package config for `find_package(mega65libc)`. `tests/` — automated tests (runnable with Xemu in PATH).

## Example usage

CC65 project: add `src/fileio.c`, `src/fileio.s`, and `include/` path to your Makefile. Include `<mega65/fileio.h>`. Call `closeall()` before any `open()` call.

LLVM-MOS CMake project: add `find_package(mega65libc REQUIRED)` and `target_link_libraries(main mega65libc::mega65libc)`.

## Maintenance status

31 stars, 22 forks, mixed license (see LICENSE), default branch `development`, latest release v0.3.0 (2023-07-20). Actively maintained; `development` branch is the working branch.

## Ecosystem

The standard C runtime layer for all MEGA65 C projects. [[MEGA65-mega65-fdisk]] and [[MEGA65-mega65-freezemenu]] both depend on it. [[cc65-cc65]] provides the compiler; [[MEGA65-mega65-weeip]] (TCP/IP stack) also builds on CC65 and could integrate with mega65-libc.
