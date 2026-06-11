# Every Pixel a Color

- URL: https://dansanderson.com/mega65/every-pixel-a-color/
- Published: November 29, 2025
- Fetched: 2026-06-11

## Overview

Deep dive into Full Color Mode (FCM) and Nibble Color Mode (NCM) on the VIC-IV, plus a Python-based image conversion workflow.

## Full Color Mode (FCM)

- Each pixel uses one byte (direct palette access 0–255); $00 = background, $FF = foreground.
- Each character requires 64 bytes; 80×25 screen needs 125 KB of character graphics.
- Screen memory stores absolute addresses (not screen codes) divided by 64. Max address: $7FFC0.
- **FCLRLO** (bit 1 of $D054): enables FCM for screen codes 0–255.
- **FCLRHI** (bit 2 of $D054): enables FCM for screen codes 256+.

### Enabling FCM

```
100 SETBIT $D054,0       : REM Enable CHR16
110 WPOKE $D058,160      : REM LINESTEP = 80*2
120 WPOKE $D060,$0000 : WPOKE $D062,$05  : REM SCRNPTR = $5.0000
130 SETBIT $D054,2       : REM Set FCLRHI
```

## Nibble Color Mode (NCM)

- 4 bits per pixel → 16 colors per character; characters expand to 16 pixels wide.
- Per-character feature (bit 3 of color RAM).
- Mixes with monochrome and FCM characters on the same screen.
- Color = upper 4 color RAM bits + 4-bit pixel data = final palette index.

## Image Conversion Workflow

Tool: **Aseprite** (or free LibreSprite). Export indexed-color PNG; use PyPNG to convert:

```python
import png
reader = png.Reader(filename='Sprite-0001-export.png')
width, height, pixels, metadata = reader.read()
# metadata['palette'] = RGB tuples; pixels = palette indices
```

Full conversion script packs 8×8 blocks of pixel data into FCM character format. Palette bytes need nibble-swap before writing to $D100-$D3FF.

## BASIC FCM Loader Pattern

```
SETBIT $D031,5           : REM 8-bit color memory (ATTR)
SETBIT $D054,0           : REM CHR16
WPOKE $D058,160          : REM LINESTEP
BLOAD "MPDATA.DAT",R,P($40000)
BLOAD "MPPAL.DAT",R,P($1E000)
FOR I=0 TO 767:POKE $D100+I,PEEK($1E000+I):NEXT I
FOR I=0 TO 1919 : WPOKE $5F060+I*2,$1000+I : NEXT I
```
