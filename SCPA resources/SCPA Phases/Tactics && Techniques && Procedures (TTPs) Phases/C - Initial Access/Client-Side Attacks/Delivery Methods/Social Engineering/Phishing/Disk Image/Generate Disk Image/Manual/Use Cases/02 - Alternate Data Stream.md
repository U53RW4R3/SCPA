# 02 - Alternate Data Stream

Search Tag(s): #initial-foothold #defense-evasion #windows #use-cases

## 2.1 -  Appending files via ADS in Linux

```
$ sudo mount -t ntfs-3g -o streams_interface=windows ntfs_image.img /mnt/ntfs/

$ echo "Nothing to see here" > /mnt/ntfs/file.txt

$ echo "Confidential information" > /mnt/ntfs/file.txt:secret.txt

$ getfattr -n ntfs.streams.list /mnt/ntfs/file.txt
getfattr: Removing leading '/' from absolute path names
# file: mnt/ntfs/file.txt
ntfs.streams.list="secret.txt"

$ cat /mnt/ntfs/file.txt:secret.txt
Confidential information
```

## 2.2 -  Mount the container with extended attributes

```
$ sudo mount -t ntfs-3g -o streams_interface=xattr ntfs_image.img /mnt/ntfs/

$ attr -l /mnt/ntfs/file.txt
Attribute "secret.txt" has a 23 byte value for /tmp/ntfs_image/file.txt
```

---
## References

- [BlueMonkey 4n6: Using Linux to handle NTFS Alternate Data Streams](https://www.youtube.com/watch?v=A7MBLlUFDgk)