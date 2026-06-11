# lgblgblgb-xemu

## Metadata
- Stars: 266
- Primary language: C
- Default branch: master
- Latest release: rolling (branch-based: master=stable, next, dev; binaries at https://github.lgb.hu/xemu)
- License: GPL-2.0
- Homepage: https://github.com/lgblgblgb/xemu/wiki
- Forks: 33
- Pushed: 2026-05-01
- Fetched: 2026-06-10
- Final URL: https://github.com/lgblgblgb/xemu
- Mode: brief (usage docs only)

## Description
Emulations (running on Linux/Unix/Windows/macOS, utilizing SDL2) of some - mainly - 8 bit machines, including the Commodore LCD, Commodore 65, and the MEGA65 as well. By LGB (Gábor Lénárt), 2016-2026.

## README (head; full docs live on the project wiki)

# X-Emulators ~ "Xemu"

[![Build Status](https://github.com/lgblgblgb/xemu/actions/workflows/main.yml/badge.svg?branch=next)](https://github.com/lgblgblgb/xemu/actions)
[![Gitter](https://badges.gitter.im/lgblgblgb/xemu.svg)](https://gitter.im/lgblgblgb/xemu)
[![Download](https://img.shields.io/badge/download-binaries-%236060FF)](https://github.lgb.hu/xemu)
[![License: GPL-2.0](https://img.shields.io/github/license/lgblgblgb/xemu.svg)](./LICENSE)
[![Contributors](https://img.shields.io/github/contributors/lgblgblgb/xemu.svg)](https://github.com/lgblgblgb/xemu/graphs/contributors)
[![GitHub last commit (dev)](https://img.shields.io/github/last-commit/lgblgblgb/xemu/dev?label=Last%20commit%20DEV)](https://github.com/lgblgblgb/xemu/wiki/ReleaseLogDEVEL)
[![GitHub last commit (next)](https://img.shields.io/github/last-commit/lgblgblgb/xemu/next?label=Last%20commit%20NEXT)](https://github.com/lgblgblgb/xemu/wiki/ReleaseLogNEXT)
[![GitHub last commit (master)](https://img.shields.io/github/last-commit/lgblgblgb/xemu/master?label=Last%20commit%20MASTER)](https://github.com/lgblgblgb/xemu/wiki/ReleaseLog)

Emulators running on Linux/Unix/Windows/OSX of various (mainly 8 bit) machines,
including the Commodore LCD and Commodore 65 and MEGA65 as well.

Written by (C)2016-2026 LGB (Gábor Lénárt) <lgblgblgb@gmail.com>
Source repository: https://github.com/lgblgblgb/xemu

Xemu also contains code wasn't written by me (sources I use from others,
or direct contributors to this project). Please read file AUTHORS

Xemu is licensed under the terms of GNU/GPL v2, for more information please
read file LICENSE. You can find the source on github, see above.

Note: there is no serious logic about the set of emulated machines by the
Xemu project. The only reason that I emulate these within a single project,
that I can easily re-use some of the components needed, that's all! Also, the
list of emulated machines is simply the preference of myself, what I would
like to emulate, nothing special about my selection.

This file is only some place holder :) For some sane documentation, please **visit
the wiki section of the project, here**:

https://github.com/lgblgblgb/xemu/wiki

## Emulators within the Xemu project

### List of emulators which can be useful:

* **MEGA65**: Emulation of the modern reincarnation of the Commodore 65 with
  many-many enhancements and new features: https://mega65.org/
* **Commodore 65**: Emulation of Commodore's final, never finished 8 bit machine,
  quite rare, and expensive to buy.
* **Commodore LCD**: Emulation of Commodore's portable LCD based computer, never
  released, about 4-5 units estimated to exist (much more rare than the
  Commodore 65, and not possible to get one). I've created the first working
  emulation of this machine ever. This emulator within Xemu is a refactored
  version of that emulator of mine.
* **Enterprise 128**: Emulation of a not so well known but neat, versatile, Z80
  based computer with very unique features among 8 bit systems, both in
  hardware and software solutions.
* **Videoton TV Computer** ("TVC"): Emulation of a Hungarian computer.
* **Primo**: Emulation of a simple but neat Hungarian computer.

### Not so much useful, unfinished and/or obsoleted but in theory can be compiled and started:

* **Commander X16**: The 8-bit guy's "dream" computer, 65C02 based, not compatible
  with existing micros. This emulator is old, buggy, missing features, and
  cannot use modern ROMs for the X16 any more. Please note, this emulator is
  **nothing** to do with the official X16 emulator, it's just my fun project to
  emulate X16 by my own, from its documentation only.
* **Commodore VIC20**: Somewhat barebone emulation of the VIC20, no sound, no
  storage medium emulation (tape or disk) ...
* **Commodore GEOS**: This was an unfinished experiment of mine. The intent was
  creating a very rudimentary C64 emulation just enough to run GEOS, and
  trying to experiment with custom modifications on GEOS this way, or even
  creating a free GEOS re-implementation later.

### Absolutely not working, not useable or even cannot be compiled:

* **Commodore 900**: Commodore's never released Z8000 based Coherent UNIX based
  machine. Currently it does nothing, work-in-progress (on the longer term!).
* **ZX Spectrum + clones**: Currently unusable, my intent was to emulate the
  original Speccy to learn about it more in this way, and add some "advanced
  clones" kind of features later, like ULAplus, and who knows what else.
* **RC2014**: Z80 based generic "SBC" emulation under the name of RC2014 but will

(README continues with build instructions; canonical docs: https://github.com/lgblgblgb/xemu/wiki — MEGA65 quick-start at /wiki/MEGA65-quickstart. Branch model: master = stable for most users, next = newer features e.g. latest ALL_INTROS support, dev = bleeding edge.)
