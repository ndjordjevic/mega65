# Roguecraft DX; Introducing the Raster Rewrite Buffer

- URL: https://dansanderson.com/mega65/raster-rewrite-buffer/
- Published: March 14, 2026
- Fetched: 2026-06-11

## Overview

Celebrates the release of *Roguecraft DX* by Badger Punch Games and introduces the VIC-IV's Raster Rewrite Buffer (RRB) — a feature enabling characters to be drawn atop other characters at arbitrary pixel positions.

## NCM Setup Example

```
CLRBIT $D05D,7 : REM Disable HOTREG
POKE $D04C,80  : REM Ensure TEXTXPOS is 80
CLRBIT $D031,5 : REM Disable ATTR
CLRBIT $D031,7 : REM Select 40-column mode
SETBIT $D054,0 : REM Enable SEAM (CHR16)
SETBIT $D054,2 : REM Enable FCLRHI
WPOKE $D058,40 : REM LINESTEP = 40
POKE $D05E,20  : REM CHRCOUNT = 20
```

## The Raster Rewrite Buffer Explained

**GOTOX**: A non-character instruction (identified by bit 4 of color memory byte 0) allowing:
- Horizontal repositioning via 10-bit pixel coordinate in screen bytes 0–1
- Transparency control: color byte 0 bit 7 enables transparent rendering of $0-valued pixels

### Practical Implementation (soldier atop flowers)

```
WPOKE $50002,$0000  : REM GOTOX SCREEN MEMORY
WPOKE $FF80002,$0090 : REM GOTOX COLOR: enable transparency
WPOKE $50004,$116E  : REM RED SOLDIER
WPOKE $FF80004,$C008
```

### Layering Strategies

1. Full stacks per position — simplest but requires recalculation for changes
2. Padded layers — uses memory liberally but simplifies addressing
3. Hybrid — background layer + dynamic foreground draw lists

### Memory and Performance

- **CHRCOUNT**: max chars + GOTOX per row (10-bit register)
- **LINESTEP**: bytes reserved per row; must be ≥ CHRCOUNT × 2 for SEAM modes
- Approximately 11 layers possible before rendering issues appear

### RRB Cycle Budget (V400 + DBLRR for 200px resolution)

```
SETBIT $D031,3   : REM Set V400
POKE $D05B,0     : REM Reset CHRYSCL
SETBIT $D051,6   : REM Enable DBLRR
POKE $D04E,102   : REM Adjust TEXTYPOS
```

### Essential Technical Details

- **Hot Registers**: Disable with `CLRBIT $D05D,7` for VIC-IV programs; reset TEXTXPOS ($D04C) to 80.
- **Text Attribute Disable**: `CLRBIT $D031,5` — frees color memory bits 4–7 for NCM sub-palette.
- **Right Border Termination**: Draw list must end with a GOTOX at the right border + dummy character.
- **Real hardware vs Xemu**: Edge cases differ — test on both. Use `$D60F.5` (REALHW) to distinguish.
