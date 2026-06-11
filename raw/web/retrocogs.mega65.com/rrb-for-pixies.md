# VIC-IV graphics, using RRB for pixies

- URL: https://retrocogs.mega65.com/2025/08/14/vic-iv-graphics-using-rrb-for-pixies/
- Published: 2025-08-14
- Fetched: 2026-06-11

## Raster Rewrite Buffer

The Raster Rewrite Buffer is a new Mega65 feature — think of it as a **2048-pixel-wide single-line buffer**. It lets a program overlay extra characters on top of already-drawn ones, used for multiple background layers or software sprites (**pixies**).

Within a screen row you can arbitrarily reset the horizontal drawing position by inserting a special **GOTOX char** (bit 4 of color RAM byte 0). With SEAM, each character is two bytes in screen RAM and color RAM. The example below draws GOTOX 0 → background NCM chars → GOTOX 54 → one NCM char (the sprite) → end-of-line GOTOX. This structure repeats for every screen row.

```
SCREEN_DATA:
{
    .var choffs  = (16384) / 64          // Character data at 16384
    .var choffs2 = (16384 + 64) / 64     // Character data at 16384 + 64

    .for(var r = 0;r < LOGICAL_NUM_ROWS;r++)
    {
        // GOTOX position
        .byte $00,$00
        // Row of characters
        .for(var c = 0;c < CHARS_WIDE;c++)
        {
            .var choffs = (16384) / 64
            .byte <choffs,>choffs        // Char index
        }
        // Draw a pixie — GOTOX position
        .byte 54,0
        { .byte <choffs2,>choffs2 }      // Char index
        // End of line — GOTOX position
        .byte <320,(>320)&3
        .byte <0,>0                      // Char index 0
    }
}

COLOR_DATA:
{
    .for(var r = 0;r < LOGICAL_NUM_ROWS;r++)
    {
        // GOTOX marker — byte0 bit4 = GOTOX marker
        .byte $10,0
        // Row of characters — byte0 bit3 = NCM, byte1 = color 255 index
        .for(var c = 0;c < CHARS_WIDE;c++) { .byte $08,$ff }
        // Pixie — byte0 bit7 = Transparent, bit4 = GOTOX marker
        .byte $90,$00
        .byte $08,$ff                    // NCM, color 255
        // End of line — byte0 bit4 = GOTOX marker
        .byte $10,$00
        .byte $00,$ff
    }
}
```

The RRB write position can be reset as many times as needed; after writing all chars for a line you must add an end-of-line (GOTOX screenWidth, char) pair so the whole line is drawn. Make the back-most layer opaque and overlay characters transparent (bit 7 of color RAM byte 0).

## Character data layout

Both FCM and NCM characters are 64 bytes (8 bytes per line). Think of memory as one tall column of characters — line 0 of char 2 is right after line 7 of char 1. Screen data refers to the character **Index** = char mem / 64, so always align character memory to a 64-byte boundary.

## Handling Y offsets

To place pixies at arbitrary vertical positions, use the SEAM Y-offset features of RRB:

- **fcm_yoffs** (screen RAM byte 1, bits 5-7): shifts the fetched character data down one line per value (range 0–7 pixels), subtracting 8 bytes per value from the fetched char data.
- **fcm_yoffs_dir** (screen RAM byte 1, bit 4): direction of that offset.

Shifting brings the preceding character's data into view at the top row, so also use row masking:

- **rowmask_flag** (color RAM byte 0, bit 3): enable row masking.
- **rowmask** (color RAM byte 1, bits 0-7): a true bit **writes** that line of character data; a false bit does **not**.

To draw a 16×8 pixie you put chars into two rows, shift the data down by the pixie ypos, and mask the top and bottom rows. Table for which char index, negative Y offset, and rowmask to use per `(ypos & 7)`:

| (ypos & 7) | line0 chrPtr | -ve yoff | rowmask | line1 chrPtr | -ve yoff | rowmask |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | chr | 0 | %111111111 | chr+1 | 0 | %00000000 |
| 1 | chr | 1 | %11111110 | chr+1 | 1 | %00000001 |
| 2 | chr | 2 | %11111100 | chr+1 | 2 | %00000011 |
| 3 | chr | 3 | %11111000 | chr+1 | 3 | %00000111 |
| 4 | chr | 4 | %11110000 | chr+1 | 4 | %00001111 |
| 5 | chr | 5 | %11100000 | chr+1 | 5 | %00011111 |
| 6 | chr | 6 | %11000000 | chr+1 | 6 | %00111111 |
| 7 | chr | 7 | %10000000 | chr+1 | 7 | %01111111 |
