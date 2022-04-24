# NEOVIM

---

## Installation

```shell
sudo apt install neovim
```

## Configuration

Make directory for Neovim config:

```shell
mkdir ~/.config/nvim
```

Create an `init.vim` file:

```shell
touch ~/.config/nvim/init.vim
```

Install vim-plug:

```shell
curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Create the configuration file

```shell
mkdir ~/.config/nvim/vim-plug
touch ~/.config/nvim/vim-plug/plugins.vim
```

Create the file for themes:

```shell
mkdir ~/.config/nvim/themes
touch ~/.config/nvim/themes/onedark.vim
```

Edit the `onedark.vim` file:

```vim
" onedark.vim override: Don't set a background color when running in a terminal;
if (has("autocmd") && !has("gui_running"))
  augroup colorset
    autocmd!
    let s:white = { "gui": "#ABB2BF", "cterm": "145", "cterm16" : "7" }
    autocmd ColorScheme * call onedark#set_highlight("Normal", { "fg": s:white }) " `bg` will not be styled since there is no `bg` setting
  augroup END
endif

hi Comment cterm=italic
let g:onedark_hide_endofbuffer=1
let g:onedark_terminal_italics=1
let g:onedark_termcolors=256

syntax on
colorscheme onedark


" checks if your terminal has 24-bit color support
if (has("termguicolors"))
    set termguicolors
    hi LineNr ctermbg=NONE guibg=NONE
endif
```

Edit the `~/.config/nvim/vim-plug/plugins.vim` file:

```vim
if empty(glob('~/.config/nvim/autoload/plug.vim'))
  silent !curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs
    \ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
  "autocmd VimEnter * PlugInstall
  "autocmd VimEnter * PlugInstall | source $MYVIMRC
endif

call plug#begin('~/.config/nvim/autoload/plugged')

    Plug 'sheerun/vim-polyglot'
    Plug 'scrooloose/NERDTree'
    Plug 'jiangmiao/auto-pairs'
    Plug 'vim-airline/vim-airline'
    Plug 'mattn/emmet-vim'
    Plug 'Yggdroot/indentLine'
    Plug 'terryma/vim-multiple-cursors'
    Plug 'joshdick/onedark.vim'
    Plug 'airblade/vim-gitgutter'
    Plug 'neoclide/coc.nvim', {'branch': 'release'}
    Plug 'kyazdani42/nvim-web-devicons'
    Plug 'ryanoasis/vim-devicons'
    Plug 'akinsho/bufferline.nvim'
    Plug 'frazrepo/vim-rainbow'
    Plug 'tpope/vim-fugitive'

call plug#end()

```

Edit or create the `~/.config/nvim/init.vim` file:

```vim
source $HOME/.config/nvim/vim-plug/plugins.vim
source $HOME/.config/nvim/themes/onedark.vim
source $HOME/.config/nvim/keymaps.vim
source $HOME/.config/nvim/basic.vim
source $HOME/.config/nvim/themes/airline.vim
```

Edit or create the `~/.config/nvim/keymaps.vim`

```vim
if has('nvim')
  inoremap <silent><expr> <c-space> coc#refresh()
  "Navigate buffers
  nnoremap <silent><a-left> :bp<CR>
  nnoremap <silent><a-right> :bn<CR>
  "NERDTree
  nnoremap <silent><a-up> :NERDTree<CR>
  nnoremap <silent><a-down> :NERDTreeClose<CR>

  " use <tab> for trigger completion and navigate to the next complete item

  function! s:check_back_space() abort
    let col = col('.') - 1
    return !col || getline('.')[col - 1] =~ '\s'
  endfunction

  inoremap <silent><expr> <Tab>
    \ pumvisible() ? "\<C-n>" :
    \ <SID>check_back_space() ? "\<Tab>" :
    \ coc#refresh()

else
  inoremap <silent><expr> <c-@> coc#refresh()
endif

```

Edit or create the `~/.config/nvim/basic.vim`

```vim
syntax on
set number
set background=dark
set nocompatible
set tabstop=4
set shiftwidth=4
set softtabstop=4
set textwidth=79
set autoindent smartindent
set expandtab
set foldmethod=indent
set foldnestmax=10
set nofoldenable
set foldlevel=2
set mouse=a
set relativenumber
set splitbelow
set splitright
set clipboard=unnamedplus

let g:filetype_pl="prolog"
let g:rainbow_active = 1

```

Edit or create `~/.config/nvim/themes/airline.vim`

```vim
" enable tabline
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#left_sep = ''
let g:airline#extensions#tabline#left_alt_sep = ''
let g:airline#extensions#tabline#right_sep = ''
let g:airline#extensions#tabline#right_alt_sep = ''

" enable powerline fonts
let g:airline_powerline_fonts = 1
let g:airline_left_sep = ''
let g:airline_right_sep = ''

" Switch to your current theme
let g:airline_theme = 'onedark'

" Always show tabs
set showtabline=2

" We don't need to see things like -- INSERT -- anymore
set noshowmode
```

Inside `nvim` execute

```vim
:PlugInstall
```
