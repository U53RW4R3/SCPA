# VirtualBox

## Debian-based Distros

### Ubuntu

 Follow the [instructions](https://www.virtualbox.org/wiki/Linux_Downloads) for the latest version in Ubuntu.

```
$ wget -O- https://www.virtualbox.org/download/oracle_vbox_2016.asc | sudo gpg --yes --output /usr/share/keyrings/oracle-virtualbox-2016.gpg --dearmor

$ echo "deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] https://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list

$ sudo apt update

$ sudo apt install virtualbox-7.1
```

Add user to the `vboxusers` group.

```
$ sudo usermod -aG vboxusers $USER
```

## Arch-based Distros

### Manjaro

Before installing the necessary packages. Check the kernel version.

```
$ mhwd-kernel -li
Currently running: 6.15.7-1-MANJARO (linux615)
..[omitted]..

$ uname -r
6.15.7-1-MANJARO
```

Include the kernel version for the hypervisor's host modules.

```
$ sudo pacman -S --noconfirm virtualbox linux615-virtualbox-host-modules
```

Add user to the `vboxusers` group.

```
$ sudo gpasswd -a $USER vboxusers
```

In order to use the hypervisor. Reload the modules.

```
$ sudo vboxreload
```

### Arch Linux

```
$ sudo pacman -S --noconfirm virtualbox virtualbox-host-modules-arch
```

Add user to the `vboxusers` group.

```
$ sudo usermod -aG vboxusers $USER
```

In order to use the hypervisor. Reload the modules.

```
$ sudo modprobe vboxdrv
```

---
## References

### VirtualBox

- [VirtualBox](https://www.virtualbox.org)

### Manjaro Wiki

- [Manjaro Wiki: VirtualBox](https://wiki.manjaro.org/index.php/VirtualBox)

### Arch Wiki

- [Arch Wiki: VirtualBox](https://wiki.archlinux.org/title/VirtualBox)