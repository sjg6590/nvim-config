# Changelog

All notable changes to this configuration are documented here.
Upstream kickstart.nvim changes are not listed — see the [kickstart.nvim releases](https://github.com/nvim-lua/kickstart.nvim/commits/master/) for those.

## [Unreleased]

### Fixed
- Replace `/add` with `@` inline file references in Claude Code integration (`claude_send_file`, `claude_send_diagnostics`)

### Added
- `<leader>ec` — send all current buffer diagnostics to Claude Code for fixing
- `<leader>el` — auto-fix with linter via LSP `quickfix`/`source.fixAll` code action

## [2025-05-22] — Ruff + diagnostics polish

### Added
- Ruff linter and formatter for Python (`ruff` via Mason, `ruff_format` in conform, `ruff` in nvim-lint)

### Fixed
- Truncate long inline diagnostic virtual text to 40% of screen width to prevent overflow
- Add `<leader>ee` keymap to open diagnostic float

## [2025-05-21] — Initial personalisation

### Added
- **Claude Code integration** — floating terminal (85% screen) toggled with `<leader>ac`
  - `<leader>af` sends current file reference to Claude
  - `<leader>as` sends visual selection with filetype fence
  - Session persists across toggle (hide/show without restarting)
- **Java LSP** — `jdtls` via Mason with JavaSE-17 runtime, download sources, code lens, organize imports on save, `google-java-format` formatter
- **Nerd Font** enabled by default (`vim.g.have_nerd_font = true`)
- Relative line numbers (`vim.o.relativenumber = true`)
- 2-space indent defaults for all filetypes
- `<leader>a` and `<leader>e` which-key groups documented

### Changed
- Based on kickstart.nvim at commit `3338d39` (Mason new address update)
- All kickstart optional plugins enabled: debug, indent_line, lint, autopairs, neo-tree, gitsigns
