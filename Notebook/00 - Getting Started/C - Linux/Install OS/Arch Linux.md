# Arch Linux

## 01 - Wizard Guide Installation

### 1.1 - Check Internet Connection

^e6a8cb

If you have plugged in the ethernet port then check the internet connection. ^9053f9

```
root@archiso:~# ping -c 1 google.com
```

^30a93b

If you have laptop with only a builtin wireless card or an external adapter at least. Run a few commands to check the available network interfaces (either it's `wlan0` or `wlp2s0`) then scan the wireless endpoints to connect it. Finally, check if you have an assigned IPv4 address from the wireless network interface then check the internet connection. ^e671fb

```
root@archiso:~# ip address

root@archiso:~# iwctl

[iwd]# station <wireless_interface> get-networks

root@archiso:~# iwctl --passphrase "<password>" station <wireless_interface> connect "<Wi-Fi_network>"

root@archiso:~# ip address show <wireless_interface>

root@archiso:~# ping -c 1 google.com
```

^b69f75

### 1.2 - Locales

1. Choose the **keyboard layout**. By default it's QWERTY US keyboard layout (`us`).
2. Select your **Locale language**.
3. For **Locale encoding** just leave UTF-8 by default.

### 1.3 - Disk Partitions

Select **Disk Configuration**.

#### 1.3.1 - First Drive

##### 1.3.1.1 - Boot Partition

For the `/boot` partition with FAT32.

1. The start sectors is `1 MiB`, or `2048` Bytes.
2. The end sectors is `1 GB`.

##### 1.3.1.2 - Root Partition

For the root (`/`) partition with BTRFS/EXT4

Note: Best to stick with EXT4 partition format. Just make your life easier.

1. Set GPT as a partition table type.
2. The start sectors is `4096 MiB` or `2099200` Bytes.
3. The end sectors is `20 GiB`, `20480 MiB`, or `41943040` Bytes (enter by default).

#### 1.3.2 - Swap

Keep it enabled by default.

#### 1.3.3 - Bootloader

Leave GRUB by default.

### 1.4 - Hostname

Change the computer name.

### 1.5 - Set Password

- Select **Root password** and insert your password.
- Select **User account** then add a user and finally a password. Finally, you'll see a prompt if you want your user account to be superuser. Choose yes by default.

### 1.6 - Profile

- Select **Type** then **Desktop** then you can choose whatever desktop environment you prefer.
- Select **Graphics driver** if you have AMD then choose the open source drivers. If Nvidia best to choose the proprietary graphics since open source isn't polished yet. If you don't have any graphic cards then **All open-source** or if you have Intel CPU then choose **Intel (open-source)**.
- The **Greeter** depends on the desktop environment you chose. If you wan to customize then choose to do so.

### 1.7 - Audio Server

For the novice users choose `pipewire`. For easy voice changer choose `pulseaudio`.

### 1.8 - Kernel

Select `linux` (bleeding edge) and `linux-lts` (long-term support). In case anything goes wrong you can switch a different kernel version to boot your system normally.

### 1.9 - Network configuration

#### 1.9.1 - Automated

- If you chose any of two desktop environments either it's GNOME or KDE. Select **Use NetworkManager**.
- If you have a different desktop environment then you can select **Copy ISO network configuration to installation**.

#### 1.9.2 - Manual

- Select **Manual configuration** then **Add interface**. From here choose which network interface that is connected to the internet. It starts from the **Check internet connection** section. If you have a ethernet cable connected either it's `eth0` or `enp0s3`. If it's a wireless interface either it's `wlan0` or `wlp2s0`.
- Once selected then choose **DHCP** as the mode. It'll assign a private IPv4 address.

### 1.10 - Optional Repositories

Select it and choose `multilib`.

### 1.11 - Timezone

Select your timezone.

### 1.12 - Automatic Time Sync

This requires an internet connection that uses the NTP protocol to sync the timezone.

### 1.13 - Finish The Installation Process

Once everything set then select **Install**.

### 1.14 - Post Installation

```
$ sudo pacman -S networkmanager man
```

## 02 - Manual Installation

![[#^e6a8cb]]
![[#^9053f9]]
![[#^30a93b]]
![[#^e671fb]]
![[#^b69f75]]

### 2.1 - [Keyboard Layout](https://wiki.archlinux.org/title/Linux_console/Keyboard_configuration)

Check what keyboard layout it uses.

```
root@archiso:~#
```

Search for the keyboard layout you need.

```
root@archiso:~# localectl list-keymaps | less

root@archiso:~# ls /usr/share/kbd/keymaps/**/*.map.gz | less
```

Once selected the keyboard layout enter the command with two letters by default it's `us`.

```
root@archiso:~# loadkeys <keyboard_layout>
```

### 2.2 - [Timezone](https://wiki.archlinux.org/title/System_time)

```
root@archiso:~# timedatectl status

root@archiso:~# cat /etc/timezone
```

To get the exact geolocation for your time. Lookup using `curl` to which timezone is suitable.

```
root@archiso:~# curl https://ipapi.co/timezone
```

Step a specific timezone based on your geolocation.

```
root@archiso:~# timedatectl list-timezones

root@archiso:~# timedatectl set-timezone UTC
```

The next step requires an internet connection that uses the NTP protocol to sync the timezone.

```
root@archiso:~# timedatectl set-ntp true
```

### 2.3 - Disk Partitions

> [!NOTE] Easier Partitioning
> `cfdisk` is much easier to use.

List the available drives.

```
root@archiso:~# lsblk

root@archiso:~# fdisk -l
```

#### 2.3.1 - First Drive

Select the drive to install where the operating system will boot. Next is to create a partition table with the letter `g` for UEFI motherboards. 

```
root@archiso:~# fdisk /dev/sda

Command (m for help): g
```

Print the partition layout of your drive.

```
Command (m for help): p
```

##### 2.3.1.1 - Boot EFI Partition (First Partition)

For the `/boot/efi` partition with **FAT32**. Select primary (`p`) as the partition type and choose the first partition.

```
Command (m for help): n
Partition type
Partition number (1-128), default 1): 1
```

Leave the default 2048 bytes for the first sector.

```
First sector (2048-41943006, default 2048):
```

For the last sector specify `512M` (Megabytes) to contain the boot partition.

```
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-41943006, default 41943006): 512M

Created a new partition 1 of type 'Linux' and of size 512 MiB.
```

Change the default `Linux filesystem` partition type to `EFI System`. Select the first then consult `L` to list partition types or aliases then you'll see the first line related to UEFI partition format.

```
Command (m for help): t
Partition number (1-1, default 1): 1
Partition type or alias (type L to list all): 1
```

###### 2.3.1.1.1 - Encrypt Partition

Select the second partition.

```
Command (m for help): n
Partition type
Partition number (2-128), default 1): 2
```

Leave the default **2048 bytes** for the first sector.

```
First sector (2048-41943006, default 2048):
```

For the last sector specify `1G` (Megabytes) to contain the boot partition.

```
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-41943006, default 41943006): 1G

Created a new partition 1 of type 'Linux' and of size 1 GiB.
```

Finally for the last partition that will be encrypted just fill out the whole free space.

```
Command (m for help): n
Partition number (3-128), default 3): 3
```

##### 2.3.1.2 - Without Encryption

###### 2.3.1.2.1 - Swap Partition

Create another partition for **swap**. Add a first partition.

```
Command (m for help): n
Partition number (2-128), default 2): 2
```

Leave the default 1128448 bytes for the first sector.

```
First sector (1128448-41943006, default 1128448):
```

Refer to this table depending on the RAM size that is installed in the hardware.

| RAM Size | Swap Size (Without Hibernation)  | Swap size (With Hibernation)  |
|----------|----------------------------------|-------------------------------|
| 256MB    | 256MB                            | 512MB                         |
| 512MB    | 512MB                            | 1GB                           |
| 1GB      | 1GB                              | 2GB                           |
| 2GB      | 1GB                              | 3GB                           |
| 3GB      | 2GB                              | 5GB                           |
| 4GB      | 2GB                              | 6GB                           |
| 6GB      | 2GB                              | 8GB                           |
| 8GB      | 3GB                              | 11GB                          |
| 12GB     | 3GB                              | 15GB                          |
| 16GB     | 4GB                              | 20GB                          |
| 24GB     | 5GB                              | 29GB                          |
| 32GB     | 6GB                              | 38GB                          |
| 64GB     | 8GB                              | 72GB                          |
| 128GB    | 11GB                             | 139GB                         |

For the last sector specify the amount of memory that the swap requires depending on your RAM size in my case it's 4GB of RAM so I specify `2GB` without hibernation.

```
Last sector, +/-sectors or +/-size{K,M,G,T,P} (1128448-41943006, default 41943006): +2G

Create a new partition 1 of type 'Linux filesystem' and of size 2 GiB.
```

Change the default `Linux filesystem` partition type to `Linux Swap`.

```
Command (m for help): t
Partition number (1-2, default 2): 2
Partition type or alias (type L to list all): 19
```

###### 2.3.1.2.2 - Root Partition (Third Partition)

> [!NOTE]
> Best to stick with EXT4 partition format. Just make your life easier.

For the root (`/`) partition with BTRFS/EXT4.

```
Command (m for help): n
Partition number (3-128), default 3): 3
```

We don't need to change the default `Linux filesystem` which uses the EXT4 format partition. But if you prefer to change it to BRTFS be sure to list the partition types to change it.

```
Command (m for help): t
Partition number (1-3, default 3): 3
Partition type or alias (type L to list all):
```

Optionally you can specify a partition type to encrypt the operating system. If not you can skip this process.

```
Command (m for help): t
Partition number (1-3, default 3): 3
Partition type or alias (type L to list all):
```

Now to save exchanges just press `w`.

```
Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.
```

#### 2.3.2 - Second Drive (additional storage)

Skip this section if you don't have an additional **hard disk drive (HDD)** or **solid state drive (SSD)** in your system. Create a GPT partition table and insert just one partition then enter the prompts by default since it'll just fill in the space.

```
root@archiso:~# fdisk /dev/sdb

Command (m for help): g

Command (m for help): p

Command (m for help): n
```

It doesn't require a boot partition. It's just an extra storage.

### 2.4 - Format Partitions

Format the boot partition.

```
root@archiso:~# mkfs.fat -F32 /dev/sda1
```

Format the partition with **EXT4**.

```
root@archiso:~# mkfs.ext4 /dev/sda2
```

#### 2.4.1 - Encrypt Partition

Encrypt the partition and type `YES` in all capital letters to accept overwriting the data then enter your passphrase twice.

```
root@archiso:~# cryptsetup luksFormat /dev/sda3
```

Open the encrypted partition then enter your passphrase. Then format the encrypted partition either **EXT4** (`mkfs.ext4`).

```
root@archiso:~# cryptsetup open /dev/sda3 cryptroot

root@archiso:~# mkfs.ext4 /dev/mapper/cryptroot
```

Now mount the encrypted root partition to install the essential packages.

```
root@archiso:~# mount /dev/mapper/cryptroot /mnt/
```

#### 2.4.2 - Without Encryption

Format a swap partition.

```
root@archiso:~# mkswap /dev/sda2

root@archiso:~# swapon /dev/sda2
```

Format the root partition.

```
root@archiso:~# mkfs.ext4 /dev/sda3
```

Now mount the root partition to install the essential packages.

```
root@archiso:~# mount /dev/sda3 /mnt/
```

### 2.5 - Extra Storage

Format the partition for an extra storage drive.

```
root@archiso:~# mkfs.ext4 /dev/sdb1
```

### 2.6 - Install Necessary Packages

If you have a fast internet speed then consider modifying the config file to download and install packages faster. Just uncomment one line. Change the number depending on how many threads your system specs.

```
root@archiso:~# nano /etc/pacman.conf
..[omitted]..
ParallelDownloads = 4
```

Install the Linux kernel and other necessary packages.

```
root@archiso:~# pacstrap /mnt/ base base-devel nano vim networkmanager linux linux-headers linux-lts linux-lts-headers linux-firmware grub efibootmgr dosfstools os-prober mtools
```

If you encrypted the partition be sure to include these packages.

```
root@archiso:~# pacstrap /mnt/ base base-devel nano vim networkmanager lvm2 cryptsetup linux linux-headers linux-lts linux-lts-headers linux-firmware grub efibootmgr dosfstools os-prober mtools
```

### 2.7 - Generate Filesystem Table

```
root@archiso:~# genfstab -U /mnt/ >> /mnt/etc/fstab
```

Change root to the `/mnt/` to install other files.

```
root@archiso:~# arch-chroot /mnt/
```

### 2.8 - Configure The Package Manager

Uncomment the lines in `[multilib]` to install 32-bit packages especially for gaming.

```
[root@archiso /]# nano /etc/pacman.conf
..[omitted]..
[multilib]
Include = /etc/pacman.d/mirrorlist
```

### 2.9 - Install GPU Drivers

Check what graphics card that is installed in the system.

```
[root@archiso /]# lscpi | less
```

#### 2.9.1 - AMD

If you have AMD GPU card then install the necessary packages.

```
[root@archiso /]# pacman -S mesa vulkan-radeon libva-mesa-driver mesa-vdpau
```

#### 2.9.2 - Nvidia

If you have NVIDIA GPU card then install the necessary packages. 

```
[root@archiso /]# pacman -S nvidia nvidia-utils nvidia-lts
```

#### 2.9.3 - Intel

If you have Intel GPU card (not the integrated graphics in the CPU) then install the necessary packages. 

```
[root@archiso /]# pacman -S intel-media-driver
```

### 2.10 - Timezone

List the directory to check which region and city you live in to match your timezone.

```
[root@archiso /]# ls /usr/share/zoneinfo/
```

Once selected the timezone then create a soft symlink to `/etc/localtime`.

```
[root@archiso /]# ln -sf /usr/share/zoneinfo/<region>/<city> /etc/localtime

[root@archiso /]# ln -sf /usr/share/zoneinfo/UTC /etc/localtime
```

### 2.11 - Hardware Clock

```
[root@archiso /]# hwclock --systohc
```

### 2.12 - Locale

Choose the locale encoding setting by uncommenting the line.

```
[root@archiso /]# nano /etc/locale.gen
..[omitted]..
en_US.UTF-8 UTF-8

[root@archiso /]# locale-gen
```

Add a line for the language setting.

```
[root@archiso /]# nano /etc/locale.conf
LANG=en_US.UTF-8
```

### 2.13 - Network Configuration

Rename your computer name.

```
[root@archiso /]# nano /etc/hostname
computer
```

Add the DNS Hosts.

```
[root@archiso /]# nano /etc/hosts
127.0.0.1	localhost
::1		localhost
127.0.0.1	computer.localdomain	computer
```

### 2.14 - Add Password

Add your `root` password.

```
[root@archiso /]# passwd
```

Create a new user then give admin privileges with the `wheel` group.

```
[root@archiso /]# useradd -mG wheel -s /bin/bash user
```

Add a password for the created user.

```
[root@archiso /]# passwd user
```

Add more groups for the user.

```
[root@archiso /]# usermod -aG audio,video,optical,storage user
```

Install the `sudo` package. Edit the `/etc/sudoers` file to add the user to give administrative privileges. Just uncomment the `wheel` group.

```
[root@archiso /]# pacman -S sudo

[root@archiso /]# EDITOR=nano visudo
..[omitted]..
%wheel ALL=(ALL) ALL
```

If you have an extra drive modify the `/etc/fstab` to mount it in `/media/` and give it user access. Copy the file as a backup in case anything goes wrong.

```
[root@archiso /]# cp /etc/fstab /etc/fstab.bak

[root@archiso /]# blkid -o value -s UUID /dev/sdb1 >> /etc/fstab

[root@archiso /]# nano /etc/fstab
UUID=<UUID_extra_storage>	/media/<folder_name>	ext4	rw,user,exec	0	0
```

Create a folder and give user permission.

```
[root@archiso /]# mkdir -p /media/<folder_name>

[root@archiso /]# chown user:user /media/<folder_name>
```

### 2.15 - Configure Bootloader

#### 2.15.1 - Encrypted Boot

> [!NOTE]
> Skip this step if you didn't encrypt your partition.

Insert a few keywords in a array variable `HOOKS` in order for the encrypted partition to boot. Before modification.

```
[root@archiso /]# nano /etc/mkinitcpio.conf
..[omitted]..
HOOKS=(base udev autodetect microcode modconf kms keyboard keymap consolefont block filesystems fsck)
```

After modification then save changes.

```
HOOKS=(base udev autodetect microcode modconf kms keyboard keymap consolefont block encrypt lvm2 filesystems fsck)
```

Apply the changes as long there are no `ERROR` signs then everything is working as expected.

```
[root@archiso /]# mkinitcpio -P
```

Create a boot directory and mount it. Finally, install the GRUB bootloader.

```
[root@archiso /]# mkdir /boot/EFI/

[root@archiso /]# lsblk

[root@archiso /]# mount /dev/sda1 /boot/EFI/

[root@archiso /]# export GRUB_ENABLE_CRYPTODISK=y

[root@archiso /]# grub-install --target=x86_64-efi --efi-directory=/boot/EFI --bootloader-id=grub_uefi /dev/sda
```

Before making configurations of the GRUB bootloader we need to specify the encrypted and decrypted UUID partitions in order to boot properly. Take note of the UUIDs

```
[root@archiso /]# blkid -o value -s UUID /dev/sda3 >> /etc/default/grub

[root@archiso /]# blkid -o value -s UUID /dev/mapper/cryptroot >> /etc/default/grub
```

Include the noted UUIDs in a specific line in order to make the proper configurations.

```
[root@archiso /]# nano /etc/default/grub
..[omitted]..
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet cryptdevice=UUID=</dev/sda2_UUID>:cryptroot root=UUID=</dev/mapper/cryptroot_UUID>
```

Make the GRUB config file.

```
[root@archiso /]# grub-mkconfig -o /boot/grub/grub.cfg
```

#### 2.15.2 - Without Encryption

Create a boot directory then mount it with the first partition for booting the operating system. Once it was mounted install the GRUB bootloader. After the installation is finished then make a GRUB config file.

```
[root@archiso /]# mkdir /boot/EFI/

[root@archiso /]# mount /dev/sda1 /boot/EFI/

[root@archiso /]# grub-install --target=x86_64-efi --bootloader-id=grub_uefi --recheck

[root@archiso /]# grub-mkconfig -o /boot/grub/grub.cfg
```

### 2.16 - Post Installation

Enable the `NetworkManager` daemon service.

```
[root@archiso /]# systemctl enable NetworkManager.
```

#### 2.16.1 - Desktop Environments

##### 2.16.1.1 - [GNOME](https://wiki.archlinux.org/title/GNOME)

```
[user@computer ~]$ sudo pacman -S gnome gnome-tweaks

[user@computer ~]$ sudo systemctl enable gdm
```

##### 2.16.1.2 - [KDE](https://wiki.archlinux.org/title/KDE)

Install the packages then enable the service.

```
[user@computer ~]$ sudo pacman -S plasma-desktop console sddm

[user@computer ~]$ sudo systemctl enable --now sddm
```

Create a directory and configure the autologin.

```
[user@computer ~]$ sudo mkdir /etc/sddm.conf.d/

[user@computer ~]$ sudo pacman nano /etc/sddm.conf.d/autologin.conf
[Autologin]
User=user
Session=plasma
```

##### 2.16.1.3 - [MATE](https://wiki.archlinux.org/title/MATE)

```
[user@computer ~]$ sudo pacman -S mate mate-extra lightdm lightdm-gtk-greeter

[user@computer ~]$ sudo systemctl enable lightdm
```

##### 2.16.1.4 - [XFCE](https://wiki.archlinux.org/title/Xfce)

```
[user@computer ~]$ sudo pacman -S xfce4 xfce4-goodies lightdm lightdm-gtk-greeter

[user@computer ~]$ sudo systemctl enable lightdm
```

#### 2.16.2 - Install The Essential Packages

```
[root@archiso /]# pacman -S flatpak man timeshift steam gamemode
```

#### 2.16.3 - Reboot The System

```
[root@archiso /]# exit

root@archiso:~# umount -l /mnt/

root@archiso:~# reboot
```

---
## References

### Source Repositories

- [mjkstra: Arch Linux Installation Guide](https://gist.github.com/mjkstra/96ce7a5689d753e7a6bdd92cdc169bae)

### Comfy.Guide

- [Comfy.Guide: LUKS Encryption](https://comfy.guide/client/luks/ )