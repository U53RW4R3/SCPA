# Mount Secondary Drive

```
$ sudo mkdir -p /media/secondarydrive

$ sudo chown -R $USER:$USER /media/secondarydrive
```

Take note of the second drive and it's own filesystem

```
$ df

$ blkid

$ sudo nano /etc/fstab
UUID=<uuid> /media/secondarydrive <filesystem>      rw,user,exec    0       0

$ sudo systemctl daemon-reload

$ sudo mount -a
```