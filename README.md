# GIT

***

## Installation

```shell
  sudo apt-get update
  sudo apt-get install vim
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

```shell
  syntax enable
  set number
  set background=dark
  set nocompatible
  set tabstop=4
  set shiftwidth=4
  set softtabstop=4
  set expandtab
  set foldmethod=indent
  set foldnestmax=10
  set nofoldenable
  set foldlevel=2
  set t_Co=256
  filetype off
  set rtp+=~/.vim/bundle/Vundle.vim
  let g:filetype_pl="prolog"
  call vundle#begin()
  Plugin 'VundleVim/Vundle.vim'
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
  call vundle#end()
  filetype plugin indent on
  colorscheme elflord
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

# Adding External Hard Drive

***

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

# MariaDB Server Documentation

***

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
    On Construction
```