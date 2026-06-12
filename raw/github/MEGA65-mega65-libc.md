# MEGA65/mega65-libc

## Metadata
- Stars: 31
- Primary language: C
- Default branch: development
- Latest release: v0.3.0 (2023-07-20)
- License: Other (mixed — see LICENSE)
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/MEGA65/mega65-libc

## Description
Simple C library for the MEGA65

## README
mega65-libc is the official C library for MEGA65, supporting both CC65 and Clang/LLVM-MOS toolchains.

**CC65 usage:** Include the `.c` and `.s` files from `src/` you need. Build: `export USE_LOCAL_CC65=1; make -f Makefile_cc65`.

**LLVM-MOS usage:** CMake-based. Install llvm-mos-sdk, then `cmake -DCMAKE_PREFIX_PATH=$HOME/llvm-mos -B build; cd build; make [install] [test]`. CPM.cmake: `CPMAddPackage(NAME mega65libc GITHUB_REPOSITORY mega65/mega65-libc GIT_TAG development)`.

**API highlights:**

FAT32 file access:
```c
void closeall(void);
unsigned char open(char *filename);
void close(unsigned char fd);
unsigned short read512(unsigned char fd, unsigned char *buffer);
```
POSIX-like directory access (m65_dirent). Note: only one file/dir can be safely open at once; call `closeall()` before opening.

**Documentation:** Requires doxygen. `make doc` (in CMake build) → HTML/LaTeX/XML. For MEGA65 User Guide integration: `make guide` → LaTeX API files.

**include/ structure:** `include/mega65/` — MEGA65-specific headers (hardware, I/O, FAT32, etc.)

**Contributing:** Pre-commit hooks for clang-format. `pip install pre-commit && pre-commit install`.

**CI:** GitHub Actions CMake workflow.

## Top-level structure
- dir src/ — C and assembly source files for CC65 and LLVM-MOS
- dir include/ — C headers (include/mega65/ for MEGA65-specific APIs)
- dir cmake/ — CMake package configuration
- dir doc/ — Doxygen output and LaTeX for user guide
- dir tests/ — automated tests
- file Makefile — CC65 build
- file Makefile_cc65 — explicit CC65 makefile
- file CMakeLists.txt — LLVM-MOS CMake build
- file .clang-format, .pre-commit-config.yaml, .editorconfig
- file README.md, LICENSE
- dir .github/ — CI workflow
