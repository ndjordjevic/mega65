# The VIC-IV Screen Layout

- URL: https://retrocogs.mega65.com/2022/09/20/the-vic-iv-screen-layout/
- Published: 2022-09-20
- Fetched: 2026-06-11
- Companion code: github.com/RetroCogs/Mega65Tutorials — `tutorial_1_screens.asm`

With the addition of the VIC-IV, the Mega65 is not limited to a fixed sized screen anymore, the application can set the screen to any size up to 720 x 576 on PAL and 720 x 480 on NTSC.

The display is made up of two components, the border around the edges and the characters that make up the screen.

Laying out the screen really just comes down to figuring out how many visible characters you want (depends on the H&V scaling modes) and then calculating how much border is needed. The author keeps the screen centered and bases all calculations off the horizontal and vertical center values.

## CHRCOUNT, DISPROWS and LINESTEP

The screen is made up with characters; in normal character mode each character takes up one byte (so an 80-column line takes 80 bytes). Once you know the size of your screen:

- **CHRCOUNT** = the number of characters in a row that the VIC-IV draws. _Note: there is currently a bug in the VHDL that makes values for CHRCOUNT > 255 not valid._
- **DISPROWS** = the number of rows the VIC-IV should draw.
- **LINESTEP** = the number of bytes to advance when moving to the next row. Handy when you want a screen area larger than the displayed characters (used in the scrolling tutorial).

## Horizontal scaling modes: H640 vs H320

On boot the Mega65 is in H640 mode (80 characters wide). To get the equivalent of 40-column mode, disable bit 7 of **$D031** to enable H320.

The catch: the layout registers (TEXTXPOS, SDBDRWDLSB) are measured in H640 units, so in H320 mode each 8-pixel-wide character is 16 pixels in the hardware registers — move one H320 pixel left = move two register pixels.

## Horizontal positioning

- **SDBDRWDLSB&MSB H640** ($D05C,D) = pixel location where the left border ends; the border is symmetrical (same left and right) in H640 units.
- **TEXTXPOS H640** = pixel location of the left edge of the screen, in H640 units.

```
PixelsWide H640 = (NumCharacters * 8) * (H320 ? 2 : 1)
LeftEdge   H640 = 400 - (PixelsWide H640 / 2)     // horizontal center is at 400
TEXTXPOS   H640 = LeftEdge H640
SDBDRWD    H640 = LeftEdge H640
```

## Vertical scaling modes: V400 vs V200

On boot the Mega65 is in V200 mode (25 rows). Enable bit 3 of **$D031** for V400 (50 rows; hard to read on a CRT). Layout registers (TEXTYPOS, TBDRPOS, BBDRPOS) are measured in V400 units — in V200 mode each 8-pixel-high character is 16 register pixels.

## Vertical positioning

- **TBDRPOS V400** = where the top border ends.
- **BBDRPOS V400** = where the bottom border starts.
- **TEXTYPOS V400** = top edge of the screen.

```
PixelsHigh V400 = (NumRows * 8) * (V200 ? 2 : 1)
TopEdge    V400 = 304 - (PixelsHigh V400 / 2)     // PAL vertical center is at 304
BotEdge    V400 = 304 + (PixelsHigh V400 / 2)
TEXTYPOS   V400 = TopEdge V400
TBDRPOS    V400 = TopEdge V400
BBDRPOS    V400 = BotEdge V400
```

(PAL and NTSC have different line counts, so the vertical center differs — this example assumes PAL.)

The next tutorial uses the technique of shifting TEXTXPOS/TEXTYPOS to freely scroll the screen in very few instructions. The author treats these posts as a living document, kept up to date as a reference.
