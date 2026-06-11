# Sounds of the SID

- URL: https://dansanderson.com/mega65/sounds-of-the-sid/
- Published: November 27, 2022
- Fetched: 2026-06-11

## Overview

MEGA65 sound capabilities: the SID chip architecture, BASIC 65 SOUND and PLAY commands, PAL vs NTSC timing implications, and the 4-SID configuration.

## The SID Chip

MOS 6581 Sound Interface Device: 3 independent voices per chip, 4 waveform types (pulse, triangle, sawtooth, noise), ADSR envelope control (attack, decay, sustain, release). The MEGA65 includes **four SID chips = 12 total voices**, arranged in stereo with adjustable mixing via the Freeze menu.

## BASIC 65 Sound Commands

**SOUND command**: single sound effects — parameters: frequency, duration, sweep effects, waveform type, pulse width.

**PLAY command**: musical sequences via string notation:
- Note names A–G with sharps/flats
- Octave control (0–6)
- Duration: whole, half, quarter, eighth, sixteenth notes
- 10 built-in instrument envelopes
- Looping and tempo control (1–255)

## PAL vs NTSC

Music playback historically tied to video refresh: PAL = 50 Hz, NTSC = 60 Hz. MEGA65 maintains compatibility; switchable via Freeze menu.

## Note

ROM v0.95 declared stable at time of this issue. Real-Time Clock replacement program available for units with faulty RTC (affected ~20%).
