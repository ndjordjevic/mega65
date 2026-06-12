---
type: source
source_url: https://github.com/dansanderson/homebrew-mega65
tags: [homebrew-tap, macos, m65connect, xemu, mega65-tools, package-distribution]
related: [dansanderson.com, lgblgblgb-xemu, MEGA65-mega65-tools, MEGA65-m65connect]
product: homebrew-mega65
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**homebrew-mega65** is Dan Sanderson's small macOS packaging repo for the practical MEGA65 desktop stack: it turns the usual "download a DMG/ZIP and wire up PATH" chores into standard Homebrew installs for M65Connect, [[lgblgblgb-xemu]], and the CLI binaries from [[MEGA65-mega65-tools]]. That makes it a useful operational companion to the workflow guidance in [[dansanderson.com]].

_All claims below are sourced from ../../raw/github/dansanderson-homebrew-mega65.md unless otherwise noted._

## What it does

Provides a custom Homebrew tap for MEGA65-related software on macOS. In its current form the tap ships two casks — `mega65-m65connect` and `mega65-xemu` — plus one formula, `mega65-tools`.

## Installation

Add the tap with `brew tap dansanderson/homebrew-mega65`, then install either a cask or the formula. GUI apps use `brew install --cask`; the README recommends `--no-quarantine` because the MEGA65 apps are unsigned.

## Key features

- One-command macOS installs for M65Connect and Xemu
- A build-from-source Homebrew formula for the official `mega65-tools` CLI suite
- PATH caveats embedded in the casks so the app-bundled binaries are available from Terminal
- Uninstall notes for the user-data directories Homebrew does not remove automatically

## Architecture

The repository is intentionally tiny: `Casks/` contains one Ruby manifest per app, while `Formula/` currently contains a placeholder README plus a single `mega65-tools.rb` formula. The casks pin direct download URLs and package metadata; the formula builds `MEGA65/mega65-tools` from the `development` branch with `make allmac` and installs the resulting binaries.

## Example usage

```text
brew tap dansanderson/homebrew-mega65
brew install --cask --no-quarantine mega65-m65connect
brew install --cask --no-quarantine mega65-xemu
brew install mega65-tools
brew upgrade mega65-m65connect
```

## Maintenance status

0 stars / 0 forks, default branch `main`, no tagged releases, last pushed 2024-07-06, and no declared repo license. The tap is clearly narrow in scope rather than a broad package index: one formula, two casks, no Linux support, and `livecheck` disabled in both casks pending a better upstream version source.
