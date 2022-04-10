# GIT

***

## Installation

```sh
sudo apt-get update
sudo apt-get install git
```

## Set remote origin with token

```shell
git remote set-url origin https://<githubtoken>@github.com/<username>/<repositoryname>.git
```

# VIM

***

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

# NEOVIM

***

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

# Adding External Hard Drive

---

## Configuration

Install NTFS:

```shell
sudo apt-get update
sudo apt-get install ntfs-3g
```

Obtain the external drive UUID:

```shell
sudo blkid
```

Create a mount place:

```shell
sudo mkdir /media/Seagate
sudo chmod 777 /media/Seagate
sudo ln -s /media/Seagate/ /home/pi/Seagate
```

Backup and modify the `fstab` file:

```shell
sudo cp /etc/fstab fstab.old
sudo vim /etc/fstab
```

Inside the `fstab` file add the hard drive UUID(replace the UUID):

```shell
UUID=361E05831E053D7D /media/Seagate ntfs defaults 0 0
```

Or with the last ntfs-3g

```shell
UUID=361E05831E053D7D /media/Seagate ntfs-3g  auto,users,permissions 0 0
```

# MariaDB Server Documentation

---

## Instalation

```shell
sudo apt-get update
sudo apt-get install mariadb-server-10.3
```

## Network configuration

Modify
`/etc/mysql/mariadb.conf.d/50-server.cnf`

```shell
[mysqld]
user = mysql
pid-file = /run/mysqld/mysqld.pid
socket = /run/mysqld/mysqld.sock
# port = 3306
basedir = /usr
datadir = /var/lib/mysql
tmpdir = /tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking
# bind-address = 127.0.0.1
```

## Change data directory

Modify
`/etc/mysql/mariadb.conf.d/50-server.cnf`

```shell
# datadir = /var/lib/mysql
datadir = /media/Seagate/mariadb
```

# SAMBA Server Documentation

***

Install SAMBA

```shell
sudo apt-get update
sudo apt-get install samba samba-common-bin
# Backup
sudo cp /etc/samba/smb.conf smb.old
# Modify configuration file
sudo nano -w /etc/samba/smb.conf
```

Inside the configuration file:

```shell
[Seagate]
comment = USB Share
path = /media/Seagate
writeable = Yes
create mask = 0777
directory mask = 0777
browseable = Yes
valid users @users
force user = pi
```

Then create an account for example:

```shell
sudo smbpasswd -a pi
sudo /etc/init.d/samba-restart
```

# MiniDLNA

***

## Installation

Download and install:

```shell
sudo apt-get install minidlna
```

Backup and modify the configuration file:

```shell
sudo cp /etc/minidlna.conf /etc/minidlna.conf.old
sudo vim /etc/minidlna.conf
```

Inside the `minidlna.conf` select the audio and videos location. Also set a friendly name:

```shell
media_dir=A,/media/Seagate/Multimedia/Musica
media_dir=V,/media/Seagate/Multimedia/Videos

friendly_name=Raspberry DLNA
```

Finally restart the service:

```shell
sudo service minidlna restart
```

## Database Restart

To restart the MiniDLNA database:

```shell
sudo minidlnad -R
sudo service minidlna restart
```

# Jupyter Notebooks

***

## Installation

Update, install pip for python3 and install `virtualenv`

```shell
sudo apt-get update
sudo apt-get install python3-pip
sudo pip3 install virtualenv
```

Create the Jupyter Notebooks folder

```shell
mkdir ~/Jupyter
cd ~/Jupyter
```

Inside the folder create a virtual environment

```shell
virtualenv env
```

Activate the virtual environment

```shell
source ~/Jupyter/env/bin/activate
```

Once activated the virtual environment install Jupyter Notebooks

```shell
pip install jupyter
```

Set the password:

```shell
jupyter notebook password
```

## Create and modify the configuration file

Create the configuration file:

```shell
jupyter notebook --generate-config
```

Edit the configuration file:

```shell
vim ~/.jupyter/jupyter_notebook_config.py
```

Inside the file add the next lines, in this case `IP=192.168.0.114` and `PORT=8888`:

```python
c.NotebookApp.open_browser = False
c.NotebookApp.ip = '192.168.0.114'
c.NotebookApp.port = 8888
c.NotebookApp.alow_remote_access = True
```

## Start a notebook

```shell
jupyter notebook
```

# Docker

***

## Installation

```shell
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

## Basic Commands

#### Pull images from the docker public repository

```shell
docker pull <image>
# Example: pulling alpine image
docker pull alpine
```

#### Create and run a container from an image. Modifier `-it` permit use all the host resources. Modifier `-d` starts the container detached (background).

```shell
docker run -it -d <image>
# Example: running mariadb
docker run -it -d mariadb
```

#### List the running containers

```shell
docker ps
```

#### Show all the running and exited containers

```shell
docker ps -a
```

#### Access to a running container

```shell
docker exec -it <container_id> bash
```

#### Stop a running container

```shell
docker stop <container_id>
```

#### Kill instantly a running container

```shell
docker kill <container_id>
```

#### Creates a new image of an edited container on the local system

```shell
docker commit <container_id>
```

#### Delete a stopped container

```shell
docker rm <container_id>
```

#### Delete an image from local storage

```shell
docker rmi <image_id>
```

#### Build an image from a specified docker file

```shell
docker build <path to docher file>
```

#### Run a container and give it a port on the local machine

```shell
docker run -d -p <local_port>:<container_port> <image_id>
# Example: run a container detached where connects the local port 5000 to the container port 8000
docker run -d -p 5000:8000 missingpets
```

## Dockerfile Example

```dockerfile
FROM alpine:latest
RUN apk -U update \
    && apk upgrade \
    && apk add --no-cache python3-dev \
    && apk add --no-cache --virtual build-deps gcc musl-dev \
    && apk add --no-cache mariadb mariadb-dev mariadb-common mariadb-client \
    && apk add --no-cache py3-pip \
    && apk add --no-cache jpeg-dev zlib-dev libjpeg \
    && python3 -m pip install --upgrade pip \
    && mkdir "missingpets"
COPY . /missingpets
WORKDIR /missingpets

RUN pip install -r requirements.txt
EXPOSE 8000
ENTRYPOINT ["./gunicorn_starter.sh"]
```

## .dockerignore Example

```docker
venv/
env/
.idea/
.git/
```

## PostgreSQL over Docker

```shell
docker run --name db-postgres -p 5432:5432 -e POSTGRES_PASSWORD=<mysecretpassword> -d postgres

# ... or more complete
docker run --name db-postgres -p 5432:5432 -d -e POSTGRES_PASSWORD=<password> \
 -e POSTGRES_USER=<username> \
 -e POSTGRES_DB=<example> \
 -v pgdata:/var/lib/postgresql/data \
  postgres

```

## Docker-compose example with PostgreSQL

```yaml
version: "3.3"

services:
  postgres:
    image: postgres
    ports:
      - "5432:5432"
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: <password>
      POSTGRES_USER: <username>
      POSTGRES_DB: <database_name>
      DATABASE_HOST: 127.0.0.1
    volumes:
      - /localpath/local/postgres:/var/lib/postgresql/data
```

# NodeJS RaspberryOS

***

## Enable the NodeSource Repository

```shell
sudo su
curl -fsSL https://deb.nodesource.com/setup_17.x | bash -
```

## Installation

```shell
sudo apt install nodejs
```

Verify installation

```shell
node --version
```

# Alacritty config file

```yaml
colors:
  # Default colors
  primary:
    background: "0x292C3E"
    foreground: "0xEBEBEB"

  # Cursor colors
  cursor:
    text: "0xFF261E"
    cursor: "0xFF261E"

  # Normal colors
  normal:
    black: "0x0d0d0d"
    red: "0xFF301B"
    green: "0xA0E521"
    yellow: "0xFFC620"
    blue: "0x1BA6FA"
    magenta: "0x8763B8"
    cyan: "0x21DEEF"
    white: "0xEBEBEB"

  # Bright colors
  bright:
    black: "0x6D7070"
    red: "0xFF4352"
    green: "0xB8E466"
    yellow: "0xFFD750"
    blue: "0x1BA6FA"
    magenta: "0xA578EA"
    cyan: "0x73FBF1"
    white: "0xFEFEF8"

window:
    opacity: 0.8

cursor:
  style:
    shape: Beam
    blinking: Always
  blink_interval: 500
  thickness: 0.2

font:
  normal:
    family: "MesloLGS NF"
  size: 10
```

# Node.js / React

## Create a React project

Verify the Node installation

```sh
node --version
```

Create the project folder and use the create command:

```shell
mkdir <projectname>
cd <projectname>
npx create-react-app .
```

# Mumble Server

***

## Installation

To install and init:

```shell
sudo apt-get install mumble-server
sudo dpkg-reconfigure mumble-server
```

## Configuration

Finally, edit the server configuration file:

```shell
sudo vim /etc/mumble-server.ini
sudo /etc/init.d/mumble-server restart
```

## Manually Start Service

ON CONSTRUCTION

```shell
ON CONSTRUCTION
```
