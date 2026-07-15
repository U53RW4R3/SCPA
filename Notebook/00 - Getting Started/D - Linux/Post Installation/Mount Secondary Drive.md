# Mount Secondary Drive

```
$ sudo mkdir -p /media/secondarydrive

$ sudo chown -R $USER:$USER /media/secondarydrive
```

Take note of the secondary drive and it's own filesystem.

```
$ df

$ blkid

$ sudo nano /etc/fstab
UUID=<uuid> /media/secondarydrive <filesystem>      defaults,noatime,exec    0       2

$ sudo systemctl daemon-reload

$ sudo mount -a
```