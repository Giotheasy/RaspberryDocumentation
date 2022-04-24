# MariaDB Server Documentation

---

## Instalation

```sh
sudo apt-get update
sudo apt-get install mariadb-server-10.3
```

## Network configuration

Modify
`/etc/mysql/mariadb.conf.d/50-server.cnf`

```sh
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

```sh
# datadir = /var/lib/mysql
datadir = /media/Seagate/mariadb
```
