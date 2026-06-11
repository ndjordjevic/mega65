# Adding a Feature to the MEGA65

- URL: https://dansanderson.com/lab-notes/adding-a-feature-to-mega65/
- Published: June 17, 2022
- Fetched: 2026-06-11

## Overview

Walkthrough of adding a real feature to the MEGA65 ROM: ESC+Home restores cursor position after an accidental Home keypress. Demonstrates ROM development workflow, assembly optimization for code size, and fixing a pre-existing C65 bug.

## The Problem

Accidental Home key presses move cursor to (0,0); MEGA65 has existing cursor memory (ESC+↑ saves, ESC+← restores) but no auto-save on Home.

## Implementation

ROM source: 6 large MOS 6502 assembly files. Located existing cursor memory routines (4 bytes: column/line for screen and logical coordinates).

**Space constraint**: new code exceeded available space between sections. Fixed by rewriting save/restore routines with register offsets to share code paths:

```assembly
save_home_position      ; save cursor position for home
    ldx #(save_home_cursor_column-save_cursor_column)
    ldy tblx
    jmp save_position_continued
save_position           ; save current cursor position
    ldx #0
save_position_continued
    lda lsxp
    sta save_input_line,x
```

## Additional Fixes

- **Prevention of multiple saves**: skip save if cursor is already at (0,0).
- **Window coordinate bug fix**: existing ESC+↑ stored raw screen coordinates instead of window-relative coordinates — fixed as a side effect of the rewrite.
- **Known edge case**: ESC+Home followed immediately by Home may trigger the window escape sequence (Home Home); accepted as acceptable trade-off.

## Result

Feature accepted into MEGA65 ROM v920362. Shows the ROM contribution process: find space, optimize for size, fix adjacent bugs, submit.
