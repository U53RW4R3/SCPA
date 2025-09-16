# SSD Optimzation

> [!NOTE]
> This is optional.

```
$ sudo cp /etc/fstab /etc/fstab.bak

$ sudo nano /etc/fstab
UUID=<uuid> /               btrfs   defaults,subvol=@,noatime        0       1
UUID=<uuid> /home           btrfs   defaults,subvol=@home,noatime    0       2

$ sudo systemctl status fstrim.timer
```