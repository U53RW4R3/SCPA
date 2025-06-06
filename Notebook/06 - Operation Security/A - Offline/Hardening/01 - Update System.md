# 01 - Update System

## 1.1 - Update Packages

### 1.1.1 - Debian-based Distros

```
$ sudo apt update && sudo apt full-upgrade -y
```

### 1.1.2 - Red Hat-based Distros

```
$ sudo yum update -y

$ sudo dnf update -y
```

### 1.1.3 - Arch-based Distros

```
$ sudo pacman -Syu --noconfirm && yay -Syu --noconfirm
```

## 1.2 - Firmware

```
$ sudo fwupdmgr get-devices

$ sudo fwupdmgr refresh --force

$ sudo fwupdmgr update
```