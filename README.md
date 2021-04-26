# 🌊 material.nvim
A port or [Material](https://material-theme.site) colorscheme for NeoVim written in lua

Theme is inspired by https://github.com/kaicataldo/material.vim

![screen](/media/Material.png)

## 🔱 Info

This is the lua branch that doesn't rely on colorbuddy.nvim anymore
Soon, this will replace the main branch after some more debugging

## ✨ Features

material.nvim is meant to be a modern colorscheme written in lua for NeoVim that supports a lot of the new features
added to NeoVim like built-in lsp and [TreeSitter](https://github.com/nvim-treesitter/nvim-treesitter)

+ 6 styles to choose from
    + Deep ocean ![screen](/media/deep-ocean.png)
    + Oceanic ![screen](/media/oceanic.png)
    + Palenight ![screen](/media/palenight.png)
    + Lighter ![screen](/media/lighter.png)
    + Darker ![screen](/media/darker.png)

+ Supported plugins:
    + [TreeSitter](https://github.com/nvim-treesitter/nvim-treesitter)
    + [LSP Diagnostics](https://neovim.io/doc/user/lsp.html)
    + [Lsp Saga](https://github.com/glepnir/lspsaga.nvim)
    + [LSP Trouble](https://github.com/folke/lsp-trouble.nvim)
    + [Git Gutter](https://github.com/airblade/vim-gitgutter)
    + [git-messenger](https://github.com/rhysd/git-messenger.vim)
    + [Git Signs](https://github.com/lewis6991/gitsigns.nvim)
    + [Telescope.nvim](https://github.com/nvim-telescope/telescope.nvim)
    + [Nvim-Tree.lua](https://github.com/kyazdani42/nvim-tree.lua)
    + [NERDTree](https://github.com/preservim/nerdtree)
    + [vim-which-key](https://github.com/liuchengxu/vim-which-key)
    + [Indent-Blankline.nvim](https://github.com/lukas-reineke/indent-blankline.nvim)
    + [WhichKey](https://github.com/liuchengxu/vim-which-key)
    + [Dashboard](https://github.com/glepnir/dashboard-nvim)
    + [BufferLine](https://github.com/akinsho/nvim-bufferline.lua)
    + [Lualine](https://github.com/hoob3rt/lualine.nvim)
    + [Neogit](https://github.com/TimUntersberger/neogit)
    + [vim-sneak](https://github.com/justinmk/vim-sneak)

+ Added functions for live theme switching without the need to restart NeoVim

## ⚡️ Requirements

+ Neovim >= 0.5.0

## 📦 Installation

Install via your favourite package manager:
```vim
" If you are using Vim-Plug
Plug 'marko-cerovac/material.nvim', { 'branch' : 'pure-lua' }
```

```lua
-- If you are using Packer
use {
      'marko-cerovac/material.nvim',
      branch = 'pure-lua'
}
```

## 🚀 Usage

Enable the colorscheme:
```vim
"Vim-Script:
colorscheme material
```

```lua
--Lua:
require('material').set()
```

To enable the `material-nvim` theme for `Lualine`, simply specify it in your lualine settings:
( make sure to set the theme to 'material-nvim', as 'material' already exists built in to lualine)

```lua
require('lualine').setup {
  options = {
    -- ... your lualine config
    theme = 'material-nvim'
    -- ... your lualine config
  }
}
```

## ⚙️ Configuration

+ There are 5 different styles available:
    + darker
    + lighter
    + oceanic
    + palenight
    + deep ocean

Set the desired style using:
```vim
"Vim-Script:
let g:material_style = 'darker'
```

```lua
--Lua:
vim.g.material_style = "deep ocean"
```

| Option                              | Default     | Description                                                                                                                                                     |
| ----------------------------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| material_style                      | `"oceanic"` | The theme comes in five styles, 'darker', 'lighter', 'palenight', 'oceanic' and 'deep ocean'
| material_italic_comments            | `false`     | Make comments italic                                                                                                                                            |
| material_italic_keywords            | `false`     | Make keywords italic                                                                                                                                            |
| material_italic_functions           | `false`     | Make functions italic                                                                                                                                           |
| material_italic_variables           | `false`     | Make variables and identifiers italic                                                                                                                           |
| material_contrast                   | `true`      | Make sidebars and popup menus like nvim-tree and telescope have a different background                                                                                       |
| material_borders                    | `false`     | Enable the border between verticaly split windows visable                                     |
| material_text_color                 | ` `         | Changed the default text colors (variables)

```lua
-- Example config in lua
vim.g.material_style = 'deep ocean'
vim.g.material_italic_comments = true
vim.g.material_italic_keywords = true
vim.g.material_italic_functions = true
vim.g.material_italic_variables = false
vim.g.material_contrast = true
vim.g.material_borders = false
vim.g.material_text_color = '#D3E1E8'

-- Load the colorscheme
require('material').set()
```

```vim
" Example config in lua
let g:material_style = 'deep ocean'
let g:material_italic_comments = true
let g:material_italic_keywords = true
let g:material_italic_functions = true
let g:material_italic_variables = false
let g:material_contrast = true
let g:material_borders = false
let g:material_text_color = '#D3E1E8'

-- Load the colorsheme
colorscheme material
```

## ⛵ Functions

+ Toggle the style live without the need to exit NeoVim

![screen](/media/toggle_style.gif)

Just call the function for style switching
```vim
"Vim-Script
:lua require('material.functions').toggle_style()
"This command toggles the style
```

The command can also be mapped to a key for fast style switching
```vim
"Vim-Script:
nnoremap <C-m> :lua require('material.functions').toggle_style()<CR>
```

```lua
--Lua:
vim.api.nvim_set_keymap('n', '<C-m>', [[<Cmd>lua require('material.functions').toggle_style()<CR>]], { noremap = true, silent = true })
```


+ Change the style to a desired one using the function change_style("desired style")
```vim
"Vim-Script:
:lua require('material.functions').change_style("palenight")
"This command changes the style to palenight
```

The command can also be mapped to a key for fast style switching
```vim
"Vim-Script:
nnoremap <C-9> :lua require('material.functions').change_style('lighter')<CR>
nnoremap <C-0> :lua require('material.functions').change_style('darker')<CR>
```

```lua
--Lua:
vim.api.nvim_set_keymap('n', '<C-9>', [[<Cmd>lua require('material.functions').change_style('lighter')<CR>]], { noremap = true, silent = true })
vim.api.nvim_set_keymap('n', '<C-0>', [[<Cmd>lua require('material.functions').change_style('darker')<CR>]], { noremap = true, silent = true })
```

## ⚠️ Importaint note:
The functions do not play well with lualine.
I'm currently working on fixing this, but until I do, lualine will not look right after a call to these functions
