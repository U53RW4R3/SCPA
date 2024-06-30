# Unix Shell

Search Tag(s): #initial-foothold #defense-evasion #windows

## 01 - Dependencies

Debian-based distros.

```
$ sudo apt install -y genisoimage ntfs-3g
```

Arch-based distros.

```
$ sudo pacman -S genisoimage ntfs-3g
```

## 02 - Usage

```
$ genisoimage -o file.iso file.txt

$ genisoimage -rJo file.iso /path/to/directory/
```

## 03 - Use Case

### 3.1 - Appending files via alternate data streams in Linux

#### 3.1.1 - Generate image container

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
$ sudo mkdir /mnt/ntfs/
```

#### 3.1.2 -  Mount the container to interact alternate data streams (ADS)

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

Unmount the container.

```
$ sudo umount /mnt/ntfs/
```

#### 3.1.3 -  Mount the container with extended attributes

```
$ sudo mount -t ntfs-3g -o streams_interface=xattr ntfs_image.img /mnt/ntfs/

$ attr -l /mnt/ntfs/file.txt
Attribute "secret.txt" has a 23 byte value for /tmp/ntfs_image/file.txt
```

Unmount the container.

```
$ sudo umount /mnt/ntfs/
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/F - Post Exploitation/Shell Is The Beginning/02 - Defense Evasion/10 - Hide Artifacts/Alternate Data Streams (ADS)/Living off the Land|Windows: Hide Artifacts]]

- [BlueMonkey 4n6: Using Linux to handle NTFS Alternate Data Streams](https://www.youtube.com/watch?v=A7MBLlUFDgk)