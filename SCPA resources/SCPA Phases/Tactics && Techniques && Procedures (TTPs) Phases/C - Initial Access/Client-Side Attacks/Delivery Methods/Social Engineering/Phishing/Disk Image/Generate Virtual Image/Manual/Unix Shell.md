# Unix Shell

Search Tag(s): #initial-foothold #defense-evasion #windows

## 01 - Dependencies

Debian-based distros.

```
$ sudo apt install -y genisoimage qemu-utils ntfs-3g
```

Arch-based distros.

```
$ sudo pacman -S genisoimage qemu-img-2 ntfs-3g
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

### 3.1 - Format NTFS

#### 3.1.1 - Generate image container

```
$ truncate -s 2M ntfs_image.img

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

#### 3.1.5 - Alternate Data Streams (ADS)

##### 3.1.5.1 -  Appending files via ADS in Linux

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

##### 3.1.5.2 -  Spoof ZoneTransfer (bypass MOTW)

TODO: Nullify the Zone.Identifer to bypass MOTW.

```
$ cat /mnt/ntfs/file.txt:Zone.Identifer
```

Unmount the container.

```
$ sudo umount /mnt/ntfs/
```

#### 3.1.7 -  Mount the container with extended attributes

##### 3.1.7.1 - Alternate Data Streams (ADS)

```
$ sudo mount -t ntfs-3g -o streams_interface=xattr ntfs_image.img /mnt/ntfs/

$ attr -l /mnt/ntfs/file.txt
Attribute "secret.txt" has a 23 byte value for /tmp/ntfs_image/file.txt
```

##### 3.1.7.2 - Modify artifact's attributes

Make the file hidden.

```
$ setfattr -n user.DOSATTRIB -v 0x02 /mnt/ntfs/file.txt

$ getfattr -n user.DOSATTRIB /mnt/ntfs/file.txt
```

Make the file visible.

```
$ setfattr -n user.DOSATTRIB -v 0x00 /mnt/ntfs/file.txt

$ getfattr -n user.DOSATTRIB /mnt/ntfs/file.txt
```

Unmount the container.

```
$ sudo umount /mnt/ntfs/
```

### 3.2 - Format exFAT

```
$ truncate -s 3M exfat_disk.img

$ mkfs -t exfat exfat_disk.img
```

Mount the virtual disk.

```
$ sudo mkdir /mnt/exfat/

$ sudo mount -t exfat exfat_disk.img /mnt/exfat/
```

### 3.3 - Format FAT32

```
$ truncate -s 1M fat32_disk.img

$ mkfs.fat -F 32 fat32_disk.img

$ file fat32_disk.img 
fat32_disk.img: DOS/MBR boot sector, code offset 0x58+2, OEM-ID "mkfs.fat", sectors 2048 (volumes <=32 MB), Media descriptor 0xf8, sectors/track 16, FAT (32 bit), sectors/FAT 16, serial number 0x3cfcd680, unlabeled
```

Mount the virtual disk.

```
$ sudo mkdir /mnt/vfat/

$ sudo mount -t vfat -o fat=32 /mnt/vfat/
```

---
## References

- [[Tactics && Techniques && Procedures (TTPs) Phases/F - Post Exploitation/Shell Is The Beginning/02 - Defense Evasion/10 - Hide Artifacts/Alternate Data Streams (ADS)/Living off the Land|Windows: Hide Artifacts]]

- [BlueMonkey 4n6: Using Linux to handle NTFS Alternate Data Streams](https://www.youtube.com/watch?v=A7MBLlUFDgk)