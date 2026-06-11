# Fun with PETSCII!

- URL: https://dansanderson.com/mega65/petscii-codes/
- Published: April 12, 2023
- Fetched: 2026-06-11

## Overview

PETSCII history, character sets, control codes, text formatting, cursor positioning, and function key customization on the MEGA65.

## PETSCII Fundamentals

- 256 code values; two character sets: mixed-case (text mode) and uppercase+graphics (default).
- Toggle with Mega+Shift.
- Screen code = position in character set; Shift+A → screen code 65; reverse mode (Ctrl+9) adds 128.

## Historical Evolution

1977 PET set used thin glyphs; C64 redesign for television legibility eliminated several PET glyphs. CHARDEF can restore them on MEGA65.

## Control Codes

```
PRINT "IT'S "+CHR$(28)+"VERY"+CHR$(5)+" COOL"
```

Control codes manage colors, text styles (underline, reverse, flashing), cursor movement.

## Text Formatting

- Underline: Ctrl+B; Flashing: Ctrl+O; Reverse: Ctrl+R.
- 32-color palette via Ctrl+D and Ctrl+A.

## Cursor Positioning

```
CURSOR col,row   : REM BASIC 65 dedicated command
```

## Function Keys

16 programmable function keys (F1–F14, Help, Run/Stop); `KEY SAVE` / `KEY LOAD` for disk persistence.

## Cross-Development

`petcat` uses curly-bracket syntax for unusual chars: `{red}`, `{clr}`, `{CBM-@}`. See MEGA65 Wiki for full syntax reference.

## References

- MEGA65 User's Guide Appendix B for PETSCII reference
- petcat syntax documentation (VICE project)
