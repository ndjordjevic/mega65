# The Justified Ancients of Mu Mu

- URL: https://dansanderson.com/mega65/justified-ancients/
- Published: March 14, 2024
- Fetched: 2026-06-11

## Overview

PCM (Pulse-Code Modulation) digitized audio on the MEGA65: audio DMA system, sample formats, and complete BASIC + conversion tool examples.

## PCM Fundamentals

- **Sample rate**: how frequently waveform is measured (Hz/kHz). Higher = more detail. CD quality = 44.1 kHz.
- **Bit depth**: vertical resolution. 8-bit = 256 values; 16-bit = 65,536 values.
- **Signed vs unsigned**: signed waveforms oscillate around 0; unsigned around a middle value (e.g., 128 for 8-bit).

## MEGA65 Storage Constraints

8 MB Attic RAM can hold ~45s of CD-quality audio; practical max for real-time playback is 64 KB first-bank RAM. At 64 KB:
- 4 kHz 8-bit: 16 seconds; 8 kHz: 8 sec; 16 kHz: 4 sec

## Audio DMA System

Requirements: CPU at 40 MHz; sample data in first 384 KB. Supports 16-bit, 8-bit, 4-bit depths; looping; variable playback rates. CPU free during playback.

### BASIC Audio DMA Example

```basic
10 FOR X=0 TO 255 : POKE $50000+X,X : NEXT X   : REM sawtooth wave
20 POKE $D720,0                                 : REM disable DMA
30 SETBIT $D711,7                               : REM enable audio DMA
40 POKE $D721,$00:POKE $D722,$00:POKE $D723,$05 : REM start address
50 POKE $D72A,$00:POKE $D72B,$00:POKE $D72C,$05 : REM top address
60 POKE $D727,$FF:POKE $D728,$00                : REM volume
70 POKE $D71C,$22 : POKE $D729,$22             : REM 8-bit unsigned
80 POKE $D724,$8C:POKE $D725,$B8:POKE $D726,$00 : REM sample rate
90 POKE $D720, $80 + $40 + $20 + $02           : REM start playback
100 GETKEY A$
110 POKE $D720,0                                : REM stop
```

## Audio Conversion Tools

### Audacity (free)

File → Export Audio → "Other uncompressed files" → RAW header-less → Signed 16-bit or Unsigned 8-bit PCM, mono, 8000 Hz.

### ffmpeg

```
ffmpeg -i input.wav -f u8 -ar 8000 -ac 1 output.raw
```

Formats: `s16le` (signed 16-bit LE), `u16le` (unsigned 16-bit), `u8` (unsigned 8-bit).

## 4-Bit Sample Packing (Python)

```python
samp_one = int(data_one[i]) // 16
samp_two = int(data_two[i]) // 16
result = samp_two * 16 + samp_one
outfile.write(bytes([result]))
```

## MOD Files

MOD format encodes music as short digitized sounds at varying frequencies (Amiga heritage). MEGA65 includes **Manche** MOD player using audio DMA.
