---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - offensive-tools
  - password-cracking
  - hashcat
  - johntheripper
---
# Offline

## 01 - Hashcat

### 1.1 - Package Manager

Install it according to your package manager.

```
$ sudo apt install -y hashcat
```

These are the required dependencies that is from the AUR.

```
$ yay -S --noconfirm opencl-amd hashcat-git

$ pamac install opencl-amd hashcat-git
```

### 1.2 - Troubleshooting

#### 1.2.1 - Arch-based distros

Always add the flag in order to use `hashcat`.

```
$ hashcat --self-test-disable
```

## 02 - John The Ripper

### 2.1 - Package Manager

```
# apt install -y john

# pacman -S --noconfirm john
```