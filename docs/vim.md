# VIM

---

Deprecated because now we use Neovim

## Installation

```shell
sudo apt-get update
sudo apt-get install vim
```

## Configuration

Clone Vundle from git repository:

```shell
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

Edit the VIM configuration file:

```shell
vim ~/.vimrc
```

Set the configuration and save:

```vim
syntax on
set number
set background=dark
set nocompatible
set tabstop=4
set shiftwidth=4
set softtabstop=4
set textwidth=79
set autoindent
set expandtab
set foldmethod=indent
set foldnestmax=10
set nofoldenable
set foldlevel=2
set t_Co=256

"set mouse=a

filetype off

set rtp+=~/.vim/bundle/Vundle.vim
let g:filetype_pl="prolog"
let python_highlight_all=1
call vundle#begin()
Plugin 'VundleVim/Vundle.vim' "Necesario
Plugin 'vim-airline/vim-airline'
Plugin 'flazz/vim-colorschemes'
Plugin 'scrooloose/nerdtree'
Plugin 'prettier/vim-prettier'
Plugin 'rhysd/vim-clang-format'
Plugin 'Yggdroot/indentLine'
Plugin 'mattn/emmet-vim'
Plugin 'airblade/vim-gitgutter'
Plugin 'terryma/vim-multiple-cursors'
Plugin 'gorodinskiy/vim-coloresque'
Plugin 'mxw/vim-prolog'
Plugin 'nvie/vim-flake8'
call vundle#end()
filetype plugin indent on

colorscheme mohammad

```

Once saved open vim and install the plugins:

```shell
vim
```

Inside VIM console:

```shell
:PluginInstall
```

### Emmet Plugin

Basic Emmet Plugin uses:

```shell
ul>li*4>span>a
```

Then press `ctrl+y` and then `,`. The result will be the next:

```html
<ul>
  <li>
    <span><a href=""></a></span>
  </li>
  <li>
    <span><a href=""></a></span>
  </li>
  <li>
    <span><a href=""></a></span>
  </li>
  <li>
    <span><a href=""></a></span>
  </li>
</ul>
```
