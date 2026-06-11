# Build MEGA65 Tools on Mac OS X (Intel and M1) | And an intro to the MEGA65 community

- URL: https://retrocombs.com/mega65-tools
- Published: 2021-08-28
- Fetched: 2026-06-11

## Overview

Building the MEGA65 development tools on Intel and M1 Macs, with notes on the welcoming MEGA65 community.

## Key Technical Content

- Setup: GitHub account, Homebrew, `git` and `gh`
- Dependency: `libusb-compat` via Homebrew
- M1: custom `Makefile` flags / library paths for ARM
- Repo: `gh repo clone MEGA65/mega65-tools`; update with `git stash` / `git pull` / `git stash pop`
- Device detection: `/dev` directory or M65 Connect
- Tools: `m65.osx` (interaction), `mega65_ftp.osx` (file transfer)
- Commands: `dir`, `put`, `get`, `fhget`, `-T` (remote typing), `-S` (screenshots), `-F` (restart)
