# nvim config

A personal Neovim configuration built on top of [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim).

## Requirements

* Neovim [stable](https://github.com/neovim/neovim/releases/tag/stable) or [nightly](https://github.com/neovim/neovim/releases/tag/nightly)
* `git`, `make`, `unzip`, C compiler (`gcc`)
* [ripgrep](https://github.com/BurntSushi/ripgrep#installation) and [fd-find](https://github.com/sharkdp/fd#installation)
* A [Nerd Font](https://www.nerdfonts.com/) — required, icons are enabled by default
* Clipboard tool: `xclip`/`xsel` (Linux), `win32yank` (Windows), or `pbcopy` (macOS)
* **Java**: JDK 17+ for `jdtls` LSP support
* **Python**: `python3` for Ruff linting/formatting

## Installation

Back up any existing config, then clone:

```sh
git clone https://github.com/shaungulati/kickstart.nvim.git "${XDG_CONFIG_HOME:-$HOME/.config}"/nvim
```

Start Neovim — [lazy.nvim](https://github.com/folke/lazy.nvim) will install all plugins automatically:

```sh
nvim
```

Use `:Lazy` to check plugin status, `:Mason` to check LSP/tool status, `:checkhealth` to diagnose issues.

## Plugins

| Plugin | Purpose |
| :----- | :------ |
| [lazy.nvim](https://github.com/folke/lazy.nvim) | Plugin manager |
| [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim) | Fuzzy finder |
| [nvim-lspconfig](https://github.com/neovim/nvim-lspconfig) + mason | LSP client + auto-install |
| [blink.cmp](https://github.com/saghen/blink.cmp) | Autocompletion |
| [LuaSnip](https://github.com/L3MON4D3/LuaSnip) | Snippet engine |
| [conform.nvim](https://github.com/stevearc/conform.nvim) | Auto-formatting on save |
| [nvim-lint](https://github.com/mfussenegger/nvim-lint) | Linting |
| [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter) | Syntax highlighting |
| [tokyonight.nvim](https://github.com/folke/tokyonight.nvim) | Colorscheme (night variant) |
| [which-key.nvim](https://github.com/folke/which-key.nvim) | Keymap hints |
| [gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim) | Git gutter signs + hunk keymaps |
| [neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim) | File explorer |
| [mini.nvim](https://github.com/echasnovski/mini.nvim) | Statusline, surround, text objects |
| [todo-comments.nvim](https://github.com/folke/todo-comments.nvim) | Highlight TODO/FIXME/NOTE |
| [nvim-autopairs](https://github.com/windwp/nvim-autopairs) | Auto bracket/quote pairs |
| [indent-blankline.nvim](https://github.com/lukas-reineke/indent-blankline.nvim) | Indent guides |
| [nvim-dap](https://github.com/mfussenegger/nvim-dap) | Debug adapter protocol |
| [lazydev.nvim](https://github.com/folke/lazydev.nvim) | Lua LSP for Neovim config/runtime |
| [guess-indent.nvim](https://github.com/NMAC427/guess-indent.nvim) | Auto-detect indentation |
| [fidget.nvim](https://github.com/j-hui/fidget.nvim) | LSP progress notifications |

## Language Support

| Language | LSP | Formatter | Linter |
| :------- | :-- | :-------- | :----- |
| Lua | `lua_ls` | `stylua` | — |
| Java | `jdtls` | `google-java-format` | — |
| Python | — | `ruff_format` | `ruff` |

All tools are installed automatically via Mason.

The Java LSP (`jdtls`) is configured with:
- JavaSE-17 runtime
- Download sources for Maven/Eclipse dependencies
- Implementations and references code lens
- Organize imports on save

## Keymaps

`<leader>` is `<Space>`.

### Search (Telescope)

| Key | Action |
| :-- | :----- |
| `<leader>sf` | Find files |
| `<leader>sg` | Live grep |
| `<leader>sh` | Search help tags |
| `<leader>sd` | Search diagnostics |
| `<leader>sw` | Search current word |
| `<leader>sk` | Search keymaps |
| `<leader>sr` | Resume last search |
| `<leader>s.` | Recent files |
| `<leader>sn` | Search Neovim config files |
| `<leader><leader>` | Find open buffers |
| `<leader>/` | Fuzzy search in current buffer |
| `<leader>s/` | Grep in open files |

### LSP

| Key | Action |
| :-- | :----- |
| `grn` | Rename symbol |
| `gra` | Code action |
| `grr` | Go to references |
| `grd` | Go to definition |
| `grD` | Go to declaration |
| `gri` | Go to implementation |
| `grt` | Go to type definition |
| `gO` | Document symbols |
| `gW` | Workspace symbols |
| `<leader>th` | Toggle inlay hints |

### Diagnostics

| Key | Action |
| :-- | :----- |
| `<leader>q` | Open diagnostic quickfix list |
| `<leader>ee` | Show diagnostic float |
| `<leader>ec` | Send buffer diagnostics to Claude Code |
| `<leader>el` | Auto-fix with linter (LSP code action) |

### Claude Code Integration

| Key | Action |
| :-- | :----- |
| `<leader>ac` | Toggle Claude Code floating terminal |
| `<leader>af` | Send current file to Claude (`Review @<path>`) |
| `<leader>as` | Send visual selection to Claude (with filetype fence) |
| `<leader>ec` | Send all buffer diagnostics to Claude for fixing |

Claude Code runs inside a floating terminal (85% of screen). The session persists — toggling hides/shows the window without restarting Claude.

### Other

| Key | Action |
| :-- | :----- |
| `<leader>f` | Format buffer |
| `<C-h/j/k/l>` | Move between splits |
| `<Esc>` | Clear search highlight |
| `<Esc><Esc>` | Exit terminal mode |

## Options

Notable non-default settings:

| Option | Value | Effect |
| :----- | :---- | :----- |
| `relativenumber` | `true` | Relative line numbers |
| `tabstop / shiftwidth` | `2` | 2-space indent by default |
| `scrolloff` | `10` | Keep 10 lines above/below cursor |
| `confirm` | `true` | Prompt to save instead of erroring on `:q` |
| `virtual_text` | truncated to 40% width | Long inline diagnostics are trimmed |
| `have_nerd_font` | `true` | Nerd Font icons enabled everywhere |

## Extending

Add custom plugins in `lua/custom/plugins/`. Any `*.lua` file placed there that returns a plugin spec will be picked up automatically once you uncomment the `{ import = 'custom.plugins' }` line near the bottom of `init.lua`.
