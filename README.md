# `highlight2ansi.nvim`

This repo implements generating text that is highlighted with ANSI escape
sequences from syntax highlighting in Neovim. This can be used to print code
highlighted the way your Neovim would do it to a terminal or to programs that
understand ANSI such as `fzf`.

> [!note]
> This is currently only implemented for 256-color (`cterm`) color schemes
> because that's all I need for myself. The code can however easily be extended
> to support true colors, the placeholders are already there. Feel free to open
> an issue if you want it and we can talk about it.

## Usage

Install this plugin however you install plugins. The most useful/common
functions are the following

```lua
local ansi = require('highlight2ansi')

-- get ANSI escape sequence for given highlight group (string)
local comment_ansi = ansi.hl_to_ansi(highlight_group)

-- get full ANSI highlighted text from open buffer
local highlighted_code = ansi.get(buf, start_line, start_col, end_line, end_col)
```

## Examples

- `fzf` picker of relevant code symbols where I use `get` to get syntax
  highlighting into the `fzf` input:
  [`fzf_symbols.lua`](https://github.com/jannis-baum/dotfiles/blob/6ad7deb2b422dfb5d03d90b29badf08c3d7dacf5/config/nvim/plugin/fzf_symbols.lua#L68)
- `fzf` picker of LSP diagnostics where I use `hl_to_ansi` to use the correct
  warning, error, etc. colors from the color scheme in `fzf`:
  [`lsp.lua`](https://github.com/jannis-baum/dotfiles/blob/6ad7deb2b422dfb5d03d90b29badf08c3d7dacf5/config/nvim/plugin/lsp.lua#L77-L138)
