---
type: source
source_url: https://github.com/dansanderson/bsa-vscode
tags: [vscode-extension, bsa-assembler, syntax-highlighting, language-server, ide-tooling, 45gs02]
related: [Edilbert-BSA]
product: bsa-vscode
detail_level: brief
created: 2026-06-12
updated: 2026-06-12
---

**bsa-vscode** is Dan Sanderson's VS Code extension providing IDE support for the BSA assembler ([[Edilbert-BSA]]), primarily for MEGA65 development. It adds syntax highlighting, error marking, symbol navigation, and go-to-definition to VS Code for `.asm`/`.src` BSA source files.

_All claims below are sourced from ../../raw/github/dansanderson-bsa-vscode.md unless otherwise noted._

## What it does

Implements a Language Server Protocol (LSP) server for BSA assembly syntax. Features: syntax highlighting, error/warning underlining, list and jump to symbol/macro references, go to definition. File association configured via `.vscode/settings.json` (`"*.asm": "bsa"`).

## Installation

Download the `.vsix` from releases; install via Extensions → ... → Install from VSIX. Build from source: `npm install` + `npm run package`.

## Key features

- Syntax coloring scopes that inherit from the active VS Code theme
- Customizable via `editor.tokenColorCustomizations` (see README for examples)
- LSP client + server in TypeScript; Jest unit tests for the server

## Architecture

Standard VS Code extension structure: `client/` (extension host), `server/` (language server), `syntaxes/bsa.tmLanguage.json` (TextMate grammar).

## Maintenance status

2 stars, 0 forks, GPL-3.0, latest release v0.0.2 (2023-12-11). Parsing of pseudo-op arguments and addressing-mode validation are listed as not yet implemented.
