---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - defense-evasion
  - scenarios
  - windows
---
# 02 - Alternate Data Stream

## 2.1 -  Appending files via ADS in Linux

### 2.1.1 - Using `wine`

```
$ echo "Nothing to see here" > file.txt

$ wine cmd.exe /c "echo Confidential information > file.txt:secret.txt"
```

View the contents inside the file via ADS.

```
$ cat file.txt:secret.txt

$ wine cmd.exe /c type file.txt:secret.txt

$ wine cmd.exe /c more file.txt:secret.txt
```

### 2.1.2 - Inside Formatted Container

Mount the NTFS container file to enable by handling ADS (`-o streams_interface=windows`).

```
$ sudo mount -t ntfs -o streams_interface=windows ntfs_image.img /mnt/ntfs/

$ sudo mount -t ntfs-3g -o streams_interface=windows ntfs_image.img /mnt/ntfs/
```

Append a new file inside a file.

```
$ echo "Nothing to see here" > /mnt/ntfs/file.txt

$ echo "Confidential information" > /mnt/ntfs/file.txt:secret.txt
```

Retrieve attributes to confirm the contents are present.

```
$ getfattr -n ntfs.streams.list /mnt/ntfs/file.txt
getfattr: Removing leading '/' from absolute path names
# file: mnt/ntfs/file.txt
ntfs.streams.list="secret.txt"
```

View the contents inside the file via ADS.

```
$ cat /mnt/ntfs/file.txt:secret.txt
Confidential information
```

## 2.2 -  Mount the container with extended attributes

Mount the NTFS container file to enable by handling extended attributes (`-o streams_interface=xattr`).

```
$ sudo mount -t ntfs -o streams_interface=xattr ntfs_image.img /mnt/ntfs/

$ sudo mount -t ntfs-3g -o streams_interface=xattr ntfs_image.img /mnt/ntfs/
```

List the attributes inside the file.

```
$ attr -l /mnt/ntfs/file.txt
Attribute "secret.txt" has a 23 byte value for /tmp/ntfs_image/file.txt
```

---
## References

- [BlueMonkey 4n6: Using Linux to handle NTFS Alternate Data Streams](https://www.youtube.com/watch?v=A7MBLlUFDgk)