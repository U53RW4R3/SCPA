# Quickemu

## Debian-based Distros

### Ubuntu

```
$ sudo add-apt-repository ppa:flexiondotorg/quickemu

sudo apt install -y quickemu qemu bash coreutils ovmf grep jq lsb-base procps python3 genisoimage usbutils util-linux sed socat spice-client-gtk libtss2-tcti-swtpm0 wget xdg-user-dirs zsync unzip
```

## Red Hat-based Distros

```
$ sudo dnf install -y qemu bash coreutils edk2-tools grep jq lsb procps python3 genisoimage usbutils util-linux sed socat spice-gtk-tools swtpm wget xdg-user-dirs xrandr unzip
```

## NixOS-based Distros

```
$ nix-env -iA pkgs.quickemu
```

## Arch-based Distros

```
$ yay -S --noconfirm quickemu
```

---
## References

### Source Repositories

- [quickemu-project: quickemu](https://github.com/quickemu-project/quickemu)

- [quickemu-project: quickgui](https://github.com/quickemu-project/quickgui)