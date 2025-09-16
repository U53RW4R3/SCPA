# Virt Manager

## Installation

Install the packages according to your package manager.

```
$ sudo pacman -S qemu virt-manager ovmf ebtables
```

Enable the daemon service.

```
$ sudo systemctl enable libvirtd

sudo systemctl start libvirtd
```

Add user to the `libvirt` group.

```
$ sudo usermod -G libvirt -a $USER
```