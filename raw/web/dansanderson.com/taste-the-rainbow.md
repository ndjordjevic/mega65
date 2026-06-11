# Taste the Rainbow

- URL: https://dansanderson.com/mega65/taste-the-rainbow/
- Published: July 6, 2025
- Fetched: 2026-06-11

## Overview

Covers custom colors and character graphics: defining custom palette entries, custom character images (CHARDEF), Extended Background Color Mode (ECM), and Low-res Multicolor Character Mode (MCM).

## Custom Colors

```
PALETTE COLOR 22,0,7,0
BACKGROUND 22
```

Palette registers: $D100–$D1FF (red), $D200–$D2FF (green), $D300–$D3FF (blue). 256 entries; text initially accesses only 32.

**Four Palette Banks**: VIC-IV supports 4 separate 256-entry palette banks; text and sprites can use different banks simultaneously (2-bit selection at $D070).

## Custom Character Sets

Character sets: 256 8×8 images = 2,048 bytes. Built-in PETSCII at ROM $2.D000. The VIC-IV character set buffer at $FF7.E000–$FF7.EFFF allows direct modification:

```
CHARDEF 65,$0C,$1C,$18,$FF,$18,$3C,$66,$C3
BLOAD "FONTNAME.64C",P($FF7E000)
```

## Extended Background Color Mode (ECM)

- 4 background colors per character; sacrifices upper 2 screen code bits (limits to first 64 chars)
- Enable: `SETBIT $D011,6`
- Background colors: $D021 (primary), $D022, $D023, $D024

```
SETBIT $D011,6
POKE $D022,0 : POKE $D023,2 : POKE $D024,4
```

## Low-res Multicolor Character Mode (MCM)

- 4 colors per character; pixels double in width; bit-pair encoding:
  - %00 = background, %01 = $D022, %10 = $D023, %11 = foreground
- Enable: `SETBIT $D016,4`
- Limits foreground to first 8 palette entries; can mix hi-res and lo-res chars on same screen
