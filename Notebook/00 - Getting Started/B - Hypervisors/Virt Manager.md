# Virt Manager

## Installation

### Debian-based Distros

```
$ sudo apt install -y qemu qemu-kvm virt-manager bridge-utils libvirt-daemon-system qemu-system-x86 qemu-utils
```

### Red Hat-based Distros

```
$ sudo dnf install -y virt-manager
```

### Arch-based Distros

```
$ sudo pacman -S qemu virt-manager ovmf ebtables
```

### Gentoo-based Distros

```
$ sudo emerge --quiet --ask=0 virt-manager
```

## Post Installation

Enable the daemon service.

```
$ sudo systemctl enable libvirtd

sudo systemctl start libvirtd
```

Add user to the `libvirt` group.

```
$ sudo usermod -G libvirt -a $USER
```