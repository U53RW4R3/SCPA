---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - reconnaissance
  - netdiscover
---
# Netdiscover

## 01 - Package Manager

Install the package according to your package manager.

```
$ sudo apt install -y netdiscover

$ yay -S --noconfirm netdiscover
```

## 02 - Universal Installation

Install the required dependencies according to your package manager.

```
$ sudo apt install -y dos2unix curl

$ sudo dnf install -y dos2unix curl

$ sudo pacman --noconfirm -S dos2unix curl
```

Clone the repository, update the MAC address list, and compile the source code then install it in the system.

```
$ git clone https://github.com/netdiscover-scanner/netdiscover.git && \
cd netdiscover && ./update-oui-database.sh && ./autogen.sh && \
./configure && make && sudo make install
```

Alternatively download the archived source code then repeat the steps to install it locally.

```
$ wget https://github.com/netdiscover-scanner/netdiscover/archive/refs/heads/master.zip && \
unzip master.zip && cd netdiscover-master && ./update-oui-database.sh && ./autogen.sh && \
./configure && make && sudo make install
```

---
## References

### Source Repositories

- [Netdiscover](https://github.com/netdiscover-scanner/netdiscover)