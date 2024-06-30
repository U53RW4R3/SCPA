# Unix Shell

Search Tag(s): #initial-foothold #defense-evasion #windows

## 01 - Dependencies

Debian-based distros.

```
$ sudo apt install -y genisoimage qemu-utils ntfs-3g
```

Arch-based distros.

```
$ sudo pacman -S genisoimage ntfs-3g
```

## 02 - Usage

### 2.1 - Generate disk image file

```
$ dd if=/dev/zero of=disk_file.<img | raw> bs=1M count=1024

$ truncate -s 1M ntfs_image.<img | raw>
```

### 2.2 - Generate ISO file

```
$ genisoimage -o disk_file.iso file.txt

$ genisoimage -rJo disk_file.iso /path/to/directory/
```

### 2.3 - Generate VHD (Virtual Hard Disk)

```
$ qemu-img create -f vpc disk_file.vhd 10M
```

## 03 - Use Case

### 3.1 - Appending files via alternate data streams in Linux

#### 3.1.1 - Generate image container

```
$ dd if=/dev/zero of=ntfs_image.img bs=1M count=100

$ truncate -s 1M ntfs_image.img

$ mkntfs -F ntfs_image.img
```

You can confirm the file has been formatted as NTFS.

```
$ file ntfs_image.img
ntfs_image.img: DOS/MBR boot sector, code offset 0x52+2, OEM-ID "NTFS    ", sectors/cluster 8, Media descriptor 0xf8, sectors/track 0, dos < 4.0 BootSector (0x80), FAT (1Y bit by descriptor); NTFS, sectors 204799, $MFT start cluster 4, $MFTMirror start cluster 12799, bytes/RecordSegment 2^(-1*246), clusters/index block 1, serial number 057a3f39d70fd3df9
```

Create a temporary directory to mount the image container.

```
$ sudo mkdir /mnt/ntfs/
```

#### 3.1.3 -  Convert IMG to ISO file

You can of course convert the image container (`.img`) to ISO (`.iso`).

```
$ genisoimage -o ntfs_iso.iso -Jr ntfs_image.img

$ mkntfs -F ntfs_iso.iso
```

#### 3.1.4 -  Generate VHD file

First detach anything that was occupying the `/dev/loop0` since it is required for mounting the file.

```
$ lsblk

$ sudo losetup -d /dev/loop0
```

Generate VHD (`.vhd`) disk file then convert it to raw. Erase the VHD since it'll be converted back.

```
$ qemu-img create -f vpc disk_file.vhd 1M

$ qemu-img convert -O raw disk_file.vhd disk_file.raw
```

Mount the raw disk file to `/dev/loop0` to format the partition as NTFS that allows to interact the filesystem in a native way by appending **alternate data streams (ADS)**.

```
$ sudo losetup /dev/loop0 disk_file.raw

$ lsblk

$ sudo mkfs -t ntfs -F /dev/loop0
```

Unmount the virtual disk then convert it back to VHD. Then reformat it.

```
$ sudo losetup -d /dev/loop0

$ qemu-img convert -O vpc disk_file.raw disk_file.vhd

$ mkntfs -F disk_file.vhd

$ rm disk_file.raw

$ file disk_file.vhd
```

#### 3.1.5 -  Mount the container to interact alternate data streams (ADS)

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

#### 3.1.6 -  Mount the container with extended attributes

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