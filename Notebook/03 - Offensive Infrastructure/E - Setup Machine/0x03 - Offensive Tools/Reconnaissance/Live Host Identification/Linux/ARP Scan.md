---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - reconnaissance
  - arp-scan
---
# ARP Scan

## 01 - Package Manager

Install the package according to your package manager.

```
$ sudo apt install -y arp-scan

$ sudo pacman --noconfirm -S arp-scan
```

## 02 - Universal Installation

```
$ git clone https://github.com/royhills/arp-scan.git && \
cd arp-scan && autoreconf --install && \
./configure && make install
```