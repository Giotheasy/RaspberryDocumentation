# MiniDLNA

---

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
