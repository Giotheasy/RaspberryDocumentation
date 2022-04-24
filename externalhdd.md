# Adding External Hard Drive

---

## Configuration

Install NTFS:

```sh
sudo apt-get update
sudo apt-get install ntfs-3g
```

Obtain the external drive UUID:

```sh
sudo blkid
```

Create a mount place:

```sh
sudo mkdir /media/Seagate
sudo chmod 777 /media/Seagate
sudo ln -s /media/Seagate/ /home/pi/Seagate
```

Backup and modify the `fstab` file:

```sh
sudo cp /etc/fstab fstab.old
sudo vim /etc/fstab
```

Inside the `fstab` file add the hard drive UUID(replace the UUID):

```sh
UUID=361E05831E053D7D /media/Seagate ntfs defaults 0 0
```

Or with the last ntfs-3g

```sh
UUID=361E05831E053D7D /media/Seagate ntfs-3g  auto,users,permissions 0 0
```
