# dansanderson/bsa-vscode

## Metadata
- Stars: 2
- Primary language: TypeScript
- Default branch: main
- Latest release: v0.0.2 (2023-12-11)
- License: GNU GPLv3
- Homepage: none
- Fetched: 2026-06-12
- Final URL: https://github.com/dansanderson/bsa-vscode

## Description
A VSCode extension for BitShifter Assembler syntax

## README
VS Code extension for the BSA assembler (https://github.com/MEGA65/BSA), primarily intended for MEGA65 development.

**Features implemented:**
- Syntax highlighting
- Highlight errors and warnings
- List and highlight references to a symbol or macro
- Go to definition for a symbol or macro
- List document symbols and macros

**Not yet implemented:**
- Parsing of pseudo-op arguments
- Validate addressing modes per instruction

**Installation:** Download `.vsix` package from releases. In VS Code: Extensions → ... → Install from VSIX. To associate file types, add to `.vscode/settings.json`:
```json
"files.associations": { "*.src": "bsa", "*.asm": "bsa" }
```

**Syntax coloring:** Defines scopes derived from current theme; customizable via `editor.tokenColorCustomizations`. Full scope list in `./syntaxes/bsa.tmLanguage.json`.

**Development:** TypeScript client + language server. Run `npm install` in root, `client/`, and `server/`. Debugging via "Client + Server" compound config in VS Code. Language server unit tests with Jest: `cd server; npm run test`. Build package: `npm run package`.

## Top-level structure
- dir client/ — VS Code extension client (TypeScript)
- dir server/ — Language server (TypeScript, Jest tests)
- dir syntaxes/ — TextMate grammar (bsa.tmLanguage.json)
- dir .vscode/ — debug launch configuration
- file package.json — extension manifest
- file language-configuration.json — VS Code language config
- file tsconfig.json — TypeScript config
- file CHANGELOG.md, README.md, LICENSE
