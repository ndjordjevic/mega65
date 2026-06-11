# Bitmap Bonanza!

- URL: https://dansanderson.com/mega65/bitmap-bonanza/
- Published: May 14, 2023
- Fetched: 2026-06-11

## Overview

VIC-III bitplane graphics mode on the MEGA65 and BASIC 65's 31 drawing commands. Also covers IFF-ILBM image format, known bugs in MEGA65's `SAVEIFF`, and workarounds using NetPBM and ImageMagick.

## BASIC 65 Bitmap Graphics

Supported resolutions: 320×200 or 640×400 px; color depth 1–8 bits.

```
10 SCREEN 320,200,2   : REM open 320x200, 4-color screen
20 PEN 1
30 LINE 25,25,295,175  : REM draw diagonal line
40 GETKEY A$
50 SCREEN CLOSE
```

Other commands: `DOT`, `BOX`, `CIRCLE`, `ELLIPSE`, `POLYGON`; `SAVEIFF` / `LOADIFF` for IFF-ILBM.

## IFF-ILBM Format Issues

`SAVEIFF` has bugs: FORM chunk size incorrectly includes its header; aspect ratio defaults to 0:0. These cause some tools to fail.

## Image Conversion Workarounds

```
ilbmtoppm line-example.iff >line-example.ppm
magick convert line-example.ppm line-example.png
```

Preparing modern images for MEGA65:
```
magick convert photo.jpg -resize 320x200\! +dither -colors 256 -depth 8 photo.ppm
ppmtoilbm -maxplanes 8 photo.ppm >photo.iff
```

## Notable Tools

- **IFF MegaShow65** by Nobato: slideshow for browsing IFF images, auto-detects resolution and depth.
