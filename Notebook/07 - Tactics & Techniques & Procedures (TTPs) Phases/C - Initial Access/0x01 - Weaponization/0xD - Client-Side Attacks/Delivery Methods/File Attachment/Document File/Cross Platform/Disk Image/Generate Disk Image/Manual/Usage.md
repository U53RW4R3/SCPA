# Usage

Search Tag(s): #initial-access #defense-evasion #windows

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