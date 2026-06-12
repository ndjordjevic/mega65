# dansanderson/homebrew-mega65

## Metadata
- Stars: 0
- Primary language: Ruby
- Default branch: main
- Latest release: none
- License: none declared
- Forks: 0
- Pushed: 2024-07-06
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/dansanderson/homebrew-mega65

## Description
Homebrew casks and formulae related to MEGA65 projects

## README
# MEGA65 Homebrew tap

This is the [Homebrew](https://brew.sh/) tap for projects of the MEGA65 team. You can use this to install MEGA65-related tools and applications for macOS.

For more information about Homebrew, see the [Homebrew documentation](https://docs.brew.sh/) and [Homebrew terminology](https://docs.brew.sh/Formula-Cookbook#homebrew-terminology).

Casks:
* `mega65-m65connect` : M65Connect, a desktop application for transferring files and performing other MEGA65 tasks
* `mega65-xemu` : Xemu MEGA65 emulator (xmega65.app)

If you experience any issues with this tap, [inquire on Discord](https://discord.gg/5DNvESf) or [file an issue](https://github.com/dansanderson/homebrew-mega65/issues).

## How to use this tap with Homebrew

To set up the tap:

```
brew tap dansanderson/homebrew-mega65
```

To install a cask, run `brew cask install` with the cask name as an argument. Use the `--no-quarantine` argument to bypass warnings about developer signatures. (MEGA65 projects cannot sign macOS apps.)

```
brew install --cask --no-quarantine mega65-m65connect
```

To install a formula, use the same command with the formula name, and omit the `--cask` and `--no-quarantine` arguments.

To update a specific formula or cask, use the `brew upgrade` command with the name of the formula or cask. (No other arguments are needed.)

```
brew upgrade mega65-m65connect
```

## Notes

M65Connect and Xemu do not remove their user files when uninstalled. To fully remove these, see:

* M65Connect: `~/Documents/MEGA65/M65Connect`
* Xemu: `~/Library/Application Support/xemu-lgb/mega65`, and the `~/.xemu-lgb` shortcut

There is not yet a Linux version of this tap. This is macOS only.

## Docs

### Casks/mega65-m65connect.rb

Homebrew cask for M65Connect 2.3. Downloads a ZIP from the MEGA65 Filehost, installs `M65Connect.app`, adds its Resources directory to `PATH`, and includes a caveat to clear the macOS quarantine attribute manually before first launch. The cask homepage points to `https://github.com/MEGA65/m65connect`. Livecheck is intentionally disabled because the tap does not yet have a reliable version-discovery source.

### Casks/mega65-xemu.rb

Homebrew cask for Xemu 1.0. Downloads the macOS installer DMG from `lgblgblgb/xemu-binaries`, installs `xmega65.app`, and adds the app's `Contents/MacOS` directory to `PATH`. Livecheck is also disabled here, with a TODO about GitHub releases.

### Formula/README.md

The `Formula/` folder is explicitly positioned as future expansion space: "This is the future home of MEGA65-related Homebrew formulae."

### Formula/mega65-tools.rb

The only current formula is `mega65-tools`, a build-from-source package for the official CLI suite. It pulls the `development` branch head of `MEGA65/mega65-tools`, depends on `conan` for the build, runs `make allmac`, and installs `m65`, `mega65_ftp`, `etherload`, `coretool`, and `romdiff`. The formula's test block only verifies that each installed binary responds to `--help`.

## Top-level structure
- `Casks/` — two macOS app packages: `mega65-m65connect.rb` and `mega65-xemu.rb`
- `Formula/` — one command-line package definition (`mega65-tools.rb`) plus a placeholder README for future formulas
- `README.md` — the user-facing tap instructions, caveats, and uninstall notes
