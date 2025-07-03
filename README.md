# Altfile-lualine

A lualine plugin to show the current alternate (`#`) buffer.

## Requirements
- [x] [Neovim](https://neovim.io/)
- [x] [Lualine](https://github.com/nvim-lualine/lualine.nvim)

## Installation

### Using lazy.nvim
```lua
{ 'wesrupert/altfile-lualine' }
```

### Using packer.nvim
```lua
use 'wesrupert/altfile-lualine'
```

### Using vim-plug
```lua
Plug 'wesrupert/altfile-lualine'
```

## Setup

Add the component `altfile` to one of your lualine sections.

**Example:**

```lua
lualine.setup({
  tabline = {
    lualine_a = { { 'tabs', mode = 2, use_mode_colors = true } },
    lualine_x = { { 'altfile', path = 1, symbols = { separator = '󰘵 ' } } },
    lualine_z = { { 'filename', path = 1 } },
  },
})
```

Customization is available. The default options are listed below.

**Example:**

```lua
lualine.setup({
  tabline = {
    lualine_x = {
      {
        'altfile',
        file_status = true,      -- Displays file status (readonly, modified)
        newfile_status = false,  -- Display new file status (not written yet)
        path = 0,                -- 0: Just the filename
                                 -- 1: Relative path
                                 -- 2: Absolute path
                                 -- 3: Absolute path, with tilde as $HOME
                                 -- 4: Filename and parent dir (with tilde)

        shorting_target = 40,    -- Shortens path to leave 40 spaces in window
        symbols = {
          separator = '^',       -- Suffix to separate from filename section
          modified = '[+]',      -- Text to show when the file is modified
          readonly = '[-]',      -- Text to show when the file is readonly
          unnamed = '[No Name]', -- Text to show for unnamed buffers
          newfile = '[New]',     -- Text to show for unwritten files
        }
      }
    },
    lualine_z = { { 'filename', path = 1 } },
  },
})
```