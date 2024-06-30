# Unix Shell

Search Tag(s): #windows

## 01 - Dependencies

Debian-based distros.

```
$ sudo apt install -y genisoimage
```

Arch-based distros.

```
$ sudo pacman -S genisoimage
```

## 02 - Usage

```
$ genisoimage -o file.iso file.txt

$ genisoimage -rJo file.iso /path/to/directory
```

### 2.1 - Generate image container

```
$ dd if=/dev/zero of=ntfs_image.img bs=1M count=100

$ mkntfs -F ntfs_image.img
```

You can confirm the file has been formatted as NTFS.

```
$ file ntfs_image.img
ntfs_image.img: DOS/MBR boot sector, code offset 0x52+2, OEM-ID "NTFS    ", sectors/cluster 8, Media descriptor 0xf8, sectors/track 0, dos < 4.0 BootSector (0x80), FAT (1Y bit by descriptor); NTFS, sectors 204799, $MFT start cluster 4, $MFTMirror start cluster 12799, bytes/RecordSegment 2^(-1*246), clusters/index block 1, serial number 057a3f39d70fd3df9
```

You can of course convert the image container (`.img`) to ISO (`.iso`).

```
$ genisoimage -o ntfs_iso.iso -Jr ntfs_image.img

$ mkntfs -F ntfs_iso.iso
```

Create a temporary directory to mount the image container.

```
$ mkdir /tmp/ntfs/
```

### 2.2 -  Mount the container to interact alternate data streams (ADS)

```
$ sudo mount -t ntfs-3g -o streams_interface=windows ntfs_image.img /tmp/ntfs/

$ echo "Nothing to see here" > /tmp/ntfs/file.txt

$ echo "Confidential information" > /tmp/ntfs/file.txt:secret.txt

$ getfattr -n ntfs.streams.list /tmp/ntfs/file.txt
getfattr: Removing leading '/' from absolute path names
# file: mnt/ntfs/file.txt
ntfs.streams.list="secret.txt"

$ cat /mnt/ntfs/file.txt:secret.txt
Confidential information
```

Unmount the container.

```
$ sudo umount /tmp/ntfs/
```

### 2.3 -  Mount the container with extended attributes

```
$ sudo mount -t ntfs-3g -o streams_interface=xattr ntfs_image.img /tmp/ntfs/

$ attr -l /tmp/ntfs/file.txt
Attribute "secret.txt" has a 23 byte value for /tmp/ntfs_image/file.txt
```

Unmount the container.

```
$ sudo umount /tmp/ntfs/
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/F - Post Exploitation/Shell Is The Beginning/02 - Defense Evasion/10 - Hide Artifacts/Alternate Data Streams (ADS)/Living off the Land|Windows: Hide Artifacts]]

- [BlueMonkey 4n6: Using Linux to handle NTFS Alternate Data Streams](https://www.youtube.com/watch?v=A7MBLlUFDgk)