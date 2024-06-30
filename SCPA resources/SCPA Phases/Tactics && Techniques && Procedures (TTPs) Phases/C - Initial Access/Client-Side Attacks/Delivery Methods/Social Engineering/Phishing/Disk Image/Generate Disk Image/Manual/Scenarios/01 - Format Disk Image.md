# 01 - Format Disk Image

Search Tag(s): #initial-foothold #windows #use-cases

## 1.1 - Format NTFS

### 1.1.1 - Generate image container

TODO: Find a way to prevent it from being corrupted when mounting on windows.

Create an empty container.

```
$ truncate -s 2M ntfs_image.img
```

Format the empty partition as NTFS.

```
$ mkfs.ntfs -QFL "Disk Image" ntfs_image.img

$ mkntfs -QFL "Disk Image" ntfs_image.img
```

You can confirm the file has been formatted as NTFS.

```
$ file ntfs_image.img
ntfs_image.img: DOS/MBR boot sector, code offset 0x52+2, OEM-ID "NTFS    ", sectors/cluster 8, Media descriptor 0xf8, sectors/track 0, dos < 4.0 BootSector (0x80), FAT (1Y bit by descriptor); NTFS, sectors 4095, $MFT start cluster 4, $MFTMirror start cluster 255, bytes/RecordSegment 2^(-1*246), clusters/index block 1, serial number 048f86c874b9c1cc9
```

Create a temporary directory to mount the image container.

```
$ sudo mkdir /mnt/ntfs/
```

### 1.1.2 -  Convert IMG to ISO file

You can of course convert the image container (`.img`) to ISO (`.iso`).

```
$ genisoimage -o ntfs_iso.iso -Jr ntfs_image.img

$ mkntfs -F ntfs_iso.iso
```

### 1.1.3 -  Generate VHD file

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

## 1.2 - Format exFAT

```
$ truncate -s 3M exfat_disk.img

$ mkfs -t exfat exfat_disk.img
```

Mount the virtual disk.

```
$ sudo mkdir /mnt/exfat/

$ sudo mount -t exfat exfat_disk.img /mnt/exfat/
```

##  1.3 - Format FAT32

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

- [[Tactics && Techniques && Procedures (TTPs) Phases/C - Initial Access/Client-Side Attacks/Delivery Methods/Social Engineering/Phishing/Disk Image/Generate Disk Image/Manual/Usage|Usage: Generate Disk Image]]