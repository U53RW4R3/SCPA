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

Install the package according to your package manager.

```
$ sudo apt install -y fwupd

$ sudo dnf install -y fwupd

$ sudo zypper install -y fwupd

$ sudo pacman -S --noconfirm fwupd
```

Retrieve information of the firmware.

```
$ sudo fwupdmgr get-devices
```

Retrieve latest updates for the firmware.

```
$ sudo fwupdmgr refresh --force
```

Get all updates of the devices.

```
$ sudo fwupdmgr get-updates
```

Download and install the firmware.

```
$ sudo fwupdmgr update -y
```