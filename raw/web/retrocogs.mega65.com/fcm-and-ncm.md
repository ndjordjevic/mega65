# VIC-IV graphics, setting up FCM and NCM

- URL: https://retrocogs.mega65.com/2025/08/13/vic-iv-graphics-setting-up-fcm-and-ncm/
- Published: 2025-08-13
- Fetched: 2026-06-11
- Note: the author marks this doc "in progress" (images being added)

## Refresher on C64 background graphics

The VIC-II can only access 16KB; select the bank with bits 0&1 of **$DD00** (%11=$0000, %10=$4000, %01=$8000, %00=$C000). The C64 screen is fixed 40×25 (1000 bytes): screen RAM offset via bits 4-7 of **$D018**, color RAM fixed at **$D800**. Each screen byte indexes one of 256 characters (8 bytes each = 2048 bytes, offset via bits 0-3 of $D018). Screen memory selects the character (8 bits); color memory selects the color (lower 4 bits).

## Mega65 screen using SEAM (Super Extended Attribute Mode)

The VIC-IV can reference an impressive **8192** characters (vs 256), which needs more than one byte. Enable **SEAM** with CHR16 (bit 0 of **$D054**):

```
// Enable Super Extended Attributes (16-bit char indices, SEAM)
lda #%00000001
tsb $d054
```

This makes all screen and color data 2 bytes per tile and adds:

- Reference a character anywhere in the bottom 512KB (64-byte granularity).
- Per character: Full color (FCM), Nibble color (NCM), or Mono.
- The GOTOX flag to jump the write position in the Raster Rewrite Buffer (multi-layer effects).
- Vertical/horizontal flipping; right-hand pixel trimming.
- NCM palette selection per character (1 of 16 palettes).
- Vertical shifting of character data as it's read from RAM.
- Row masking (which rows of the character are drawn).
- Foreground/Background priority vs sprites.
- Opaque/Transparent (whether color index 0 writes — enables overlaying characters).

When SEAM is enabled, LINECOUNT (**$D058/9**) must account for 2 bytes per char — typically LINECOUNT = CHRCOUNT * 2.

## Palettes

The VIC-IV has 4 palettes of 256 colors. Enable palette editing with the PAL flag (bit 2 of **$D030**):

```
// Enable RAM palettes (bit2 = PAL)
lda #%00000100
tsb $d030
```

Select the currently mapped palette via MAPEDPAL (bits 6&7 of **$D070**). Then read/write Red at **$D100-D1FF**, Green at **$D200-D2FF**, Blue at **$D300-D3FF**.

- **NOTE:** palette nibbles are flipped — swap lo/hi nibble for a true 0–255 value (color $37 stored as $73).
- **NOTE:** bit 0 of Red is reserved for genlock (not implemented), so only 2^23 colors (~8 million) display.

Select which palette is used for Text (BTPALSEL bits 4&5 $D070), Sprites (SPRPALSEL bits 2&3), and Alternate Text (ABTPALSEL bits 0&1):

```
// Edit=pal0, Text=pal0, Sprite=pal0, Alt=pal2
lda #%00000010
sta $d070
```

## Enabling FCM / NCM

Enable 8-bit color by clearing ATTR (bit 5 of **$D031**). Enable FCM for chars > 255 (index <256 = Mono, >255 = FCM/NCM) with FCLRHI (bit 2 of **$D054**):

```
// Clear bit5=ATTR to enable 8-bit color
lda #%00100000
trb $d031
// Set bit2=FCM for chars >$ff
lda #%00000100
tsb $d054
```

## Full Color Mode (FCM)

FCM characters are 8×8 pixels, 256 colors per character — one byte per pixel selecting a palette color. 64 bytes per character, 64-byte aligned. Color index 255 is special: instead of the last palette color, it uses the index specified in color RAM (byte 1).

## Nibble Color Mode (NCM)

NCM characters are 16×8 pixels, 16 colors per character — each byte holds 2 pixels (left = high nibble, right = low nibble), each nibble an index into a sub-palette selected by color RAM. 64 bytes per character, 64-byte aligned. Color index 15 is special: it uses color RAM (byte 1 lo nibble); the sub-palette is selected by color RAM (byte 1 hi nibble) — e.g. $4f = palette 4, index 15.
