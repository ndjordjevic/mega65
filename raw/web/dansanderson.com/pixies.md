# Pixie Power

- URL: https://dansanderson.com/mega65/pixies/
- Published: April 22, 2026
- Fetched: 2026-06-11

## Overview

Explores advanced graphics on the MEGA65: positioning layered game objects at arbitrary pixel coordinates using the Raster Rewrite Buffer (RRB). The technique, called "pixies," enables software-managed sprite-like effects (soft sprites) rather than hardware sprite features.

## Key Concepts

**Pixies Defined**: Soft sprites positioned independently through RRB manipulation — GOTOX instructions position them at arbitrary X coordinates; character data Y offset (−7 to +7) and row masking handle vertical positioning.

**Horizontal Positioning**: GOTOX instructions specify pixel positions, enabling smooth animation across the screen.

**Vertical Positioning**:
1. Character Data Y Offset: shifts which pixel row the VIC reads.
2. Row Masking: hides/shows individual pixel rows within a character row to eliminate artifacts.

## Technical Implementation

```
REM ROW 0:
O=0*42*2+40
WPOKE $50000+O,     $7000 : REM GOTOX SCREEN MEMORY
WPOKE $FF80000+O,   $F898 : REM GOTOX COLOR MEMORY
```

## Featured Projects

- **Dark Reaper**: 3D maze game with dynamic lighting.
- **DOS/65**: CP/M-compatible OS port.
- **MegaPC**: 8086 emulator for MS-DOS programs.
- **MegaSweeper65**: Minesweeper recreation.

## Resources

Downloads: `tactical.d81` disk image with BASIC display demos, assembly language source, GameShell65 framework documentation.
