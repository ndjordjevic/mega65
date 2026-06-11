# A Rorschach Test on Fire

- URL: https://dansanderson.com/mega65/rorschach-test-on-fire/
- Published: March 14, 2023
- Fetched: 2026-06-11

## Overview

Covers new ROM features (80×50 text mode, extended CHARDEF, enhanced mouse/monitor), plus a complete Mandelbrot Set renderer in BASIC 65.

## ROM Updates (at time of issue)

### 80×50 Text Mode

```
PRINT CHR$(27)+"5"+CHR$(147)
```

Or press Esc then "5" interactively.

### Enhanced Mouse Support

`MOUSE ON` now provides a default arrow sprite without custom cursor images; first 7 sprites have simple default patterns.

### Extended CHARDEF

Now supports all 512 screen codes (0–511) instead of just 256.

### Monitor: BRK Improvement

Monitor now properly tracks PC after `BRK`; programs can resume with `G` command. Run/Stop+Restore opens the Monitor.

## Mandelbrot Set in BASIC 65 (80×50 mode)

Complex number iteration:
```
170 ZX=ZX*ZX-ZY*ZY+X
180 ZY=2*ZX*ZY+Y
190 A=SQR(ZX*ZX+ZY*ZY)  : REM divergence test
```

Colors pixels by iteration count. Full program in article.

## Foenix FNX1591 Floppy Drive

New 3.5" double-density drive compatible with MEGA65 and Commodore 1581; updatable firmware; dual IEC connectors. Pre-orders at $275 USD (estimated April 2023 delivery).
