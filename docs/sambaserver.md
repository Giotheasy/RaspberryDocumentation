# SAMBA Server Documentation

---

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
