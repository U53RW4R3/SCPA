# Virt Manager

## Installation

### Debian-based Distros

```
# apt install -y qemu qemu-kvm virt-manager bridge-utils libvirt-daemon-system qemu-system-x86 qemu-utils
```

### Red Hat-based Distros

```
# dnf install -y virt-manager
```

### Arch-based Distros

```
# pacman -S qemu virt-manager ovmf ebtables
```

### Gentoo-based Distros

```
# emerge --quiet --ask=0 virt-manager
```

## Post Installation

Enable the daemon service.

```
# systemctl enable libvirtd
systemctl start libvirtd
```

Add user to the `libvirt` group.

```
# usermod -G libvirt -a $USER
```