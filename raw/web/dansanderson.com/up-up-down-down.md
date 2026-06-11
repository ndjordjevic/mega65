# Up Up Down Down Left Right Left Right B A Start

- URL: https://dansanderson.com/mega65/up-up-down-down/
- Published: October 21, 2024
- Fetched: 2026-06-11

## Overview

Comprehensive guide to multi-button game controllers for MEGA65: 9-pin connector protocol, paddle controllers, 2/3-button protocols, and modern controller options.

## 9-Pin Connector (Atari Standard)

- Pin 1–4: Up/Down/Left/Right; Pin 6: Fire; Pin 8: Ground.
- BASIC 65: `JOY(port)` returns 0–8 for direction; +128 when fire pressed.

## Reading Joystick in Assembly

```assembly
sei              ; disable interrupts
ldx #$ff
stx $dc00        ; lock keyboard lines
lda $dc00        ; read port 2 pin state
ldx #$7f
stx $dc00        ; restore keyboard lines
cli
```

## Paddle Controllers (Analog)

Potentiometers report 0–255. Dedicated MEGA65 registers:
- $D620/$D621: Port 1 X/Y paddle
- $D622/$D623: Port 2 X/Y paddle

## Three-Button Protocol

- Button A: Pin 6 (standard fire)
- Button B: Pin 9 (POTY)
- Button C: Pin 5 (POTX)

```basic
J = JOY(2)
A = J > 127          : REM button A
B = POT(3) < 128     : REM button B
C = POT(4) < 128     : REM button C
```

## R3 vs R6 Mainboard

R6 (2024): bidirectional joystick port lines enabling advanced controller protocols. R3 owners need not upgrade — all current software works on both.

## Recommended Controllers

- **RetroGameBoyz gamepads**: NES-style, 9-pin, MEGA65-themed variant available
- **Commotron Gamepad Turbo 2000 Super**: wireless, 6 remappable layouts, 3-button support
- **Hyperkin Trooper/Ranger**: arcade-quality; Ranger has integrated paddle wheel
- **mouSTer**: multi-protocol USB adapter (supports 3-button and 5plusbuttonsJoystick)
- **Unijoysticle 2**: dual-port Bluetooth adapter

## Joytest65

Diagnostic utility for joystick and paddle testing (assembly source + binary on Filehost).
