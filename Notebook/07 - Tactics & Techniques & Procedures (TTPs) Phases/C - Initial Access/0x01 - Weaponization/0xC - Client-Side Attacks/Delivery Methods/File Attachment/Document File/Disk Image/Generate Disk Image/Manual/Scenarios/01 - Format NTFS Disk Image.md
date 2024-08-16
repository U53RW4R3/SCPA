# 01 - Format NTFS Disk Image

Search Tag(s): #initial-access #windows #use-cases

## 1.1 - Generate image container

Create an empty container.

```
$ truncate -s 2M ntfs_image.img
```

Format the empty partition as NTFS.

```
$ mkfs.ntfs -QF ntfs_image.img

$ mkntfs -QF ntfs_image.img
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

## 1.2 -  Convert IMG to ISO file

You can of course convert the image container (`.img`) to ISO (`.iso`).

```
$ genisoimage -o ntfs_iso.iso -Jr ntfs_image.img

$ mkntfs -QF ntfs_iso.iso
```

---
## References

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/File Attachment/Document File/Disk Image/Generate Disk Image/Manual/Usage|Usage: Generate Disk Image]]