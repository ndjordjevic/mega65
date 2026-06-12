---
type: source
source_url: https://github.com/dansanderson/joytest65
tags: [joystick-input, paddle-input, cia-registers, sid-pot-registers, acme-assembler, controller-testing]
related: [dansanderson.com, dansanderson-easyasm65]
product: joytest65
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**joytest65** is Dan Sanderson's small MEGA65 controller-input demo: a practical 45GS02 assembly reference for reading joystick directions, paddle dials, and multi-button controller variants directly from the machine's CIA and SID-facing registers. It is especially useful as a local, citable companion to the broader controller guidance in [[dansanderson.com]], and it also highlights where the code goes beyond [[dansanderson-easyasm65]]'s on-device assembler subset by relying on Acme macros.

_All claims below are sourced from ../../raw/github/dansanderson-joytest65.md unless otherwise noted._

## What it does

Builds a MEGA65 PRG that visualizes both joystick ports and four paddle channels, showing raw register values alongside common gameplay-oriented interpretations. The README covers one-button joysticks, Commodore-style paddles, the C64GS three-button convention, and the five-button extension that overloads opposing directional combinations for extra buttons.

## Installation

The build story is intentionally minimal: assemble `joytest65.asm` with Acme using `acme joytest65.asm`. The README explicitly notes that the current source does not assemble with EasyAsm because it uses macros.

## Key features

- CIA joystick-bit mapping for port 1 and port 2 via `$DC01` and `$DC00`
- Paddle read procedure using `$DC00` port-select bits plus SID POT registers `$D419` / `$D41A`
- Guidance for three-button and five-button controllers that reuse paddle pins
- A live on-screen tester layout for two joysticks, five-button state indicators, and four paddle values

## Architecture

The repo is essentially one focused assembly program. `joytest65.asm` prints PETSCII setup codes, DMA-copies a prepared screen layout into place, then loops over `read_joystick_ports` and `update_display`. The controller routine follows the README's safety rules directly: `sei`, write `$FF` to `$DC00` to isolate the keyboard, read joystick bits, clear the FAST bit in `$D031` so the paddle timing happens at 1 MHz, select each port via `$DC00` bits 6-7, debounce the POT reads by comparing repeated samples from `$D419` and `$D41A`, then restore `$DC00` to `$7F` and re-enable interrupts.

## Example usage

```text
acme joytest65.asm
```

Run the resulting PRG on a MEGA65 with joysticks or paddles connected to inspect the raw CIA and paddle readings while moving the controller.

## Maintenance status

MIT-licensed, 0 stars / 0 forks, default branch `main`, latest release `v0.1` from 2024-10-20, and last pushed the same day. It is a narrow example repo rather than a framework: the remaining TODOs are support for the MEGA65 4-player joystick adapter and a future mouse/paddle visualization path.
