---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - offensive-tools
  - initial-access
  - exploitation
  - wireless-attacks
  - aircrack-ng
  - wifite2
---
# Wi-Fi

## Compatible Wireless Adapters

| Vendor   | Wireless Card     | Chipset           | Frequency | Protocol         | Antenna  |
| -------- | ----------------- | ----------------- | --------- | ---------------- | -------- |
| TP-Link  | TP-Link TL-WN722N | Atheros AR9271    | 2.4 GHz   | 802.11b/g/n      | External |
| Panda    | Panda PAU06       | Ralink RT5372     | 2.4 GHz   | 802.11b/g/n      | External |
| Panda    | Panda PAU09       | Ralink RT5572     | 2.4/5 GHz | 802.11a/b/g/n    | External |
| Alfa     | Alfa AWUS036NHA   | Atheros AR9271    | 2.4 GHz   | 802.11b/g/n      | External |
| Alfa     | Alfa AWUS1900     | Realtek RTL8814AU | 2.4/5 GHz | 802.11a/b/g/n/ac | External |
| Alfa     | Alfa AWUS036ACH   | Realtek RTL8812AU | 2.4/5 GHz | 802.11a/b/g/n/ac | External |
| Alfa     | Alfa AWUS036NH    | Ralink RT3070     | 2.4 GHz   | 802.11b/g/n      | External |
| Alfa     | Alfa AWUS036NHA   | Atheros AR9271    | 2.4 GHz   | 802.11b/g/n      | External |
| Realtek  | Realtek RTL8811AU | Realtek RTL8811AU | 2.4/5 GHz | 802.11a/b/g/n/ac | External |
| Atheros  | Atheros AR9271    | Atheros AR9271    | 2.4 GHz   | 802.11b/g/n      | External |
| Ralink   | Ralink RT3070     | Ralink RT3070     | 2.4 GHz   | 802.11b/g/n      | External |
| Ralink   | Ralink RT3572     | Ralink RT3572     | 2.4/5 GHz | 802.11a/b/g/n    | External |
| Ralink   | Ralink RT5572     | Ralink RT5572     | 2.4/5 GHz | 802.11a/b/g/n    | External |
| Ralink   | Ralink RT5370N    | Ralink RT5370N    | 2.4 GHz   | 802.11b/g/n      | External |
| MediaTek | MediaTek MT7610U  | MediaTek MT7610U  | 2.4/5 GHz | 802.11a/b/g/n/ac | External |
| Alfa     | Alfa AWUS036ACM   | Realtek RTL8812AU | 2.4/5 GHz | 802.11a/b/g/n/ac | External |
| ASUS     | ASUS USB-AC68     | Realtek RTL8814AU | 2.4/5 GHz | 802.11a/b/g/n/ac | External |
| Netgear  | Netgear A6210     | Realtek RTL8812AU | 2.4/5 GHz | 802.11a/b/g/n/ac | External |

## Install Wireless Tools

### aircrack-ng

#### Package Manager

```
$ sudo apt install -y aircrack-ng

$ sudo dnf install -y aircrack-ng

$ sudo pacman -S --noconfirm aircrack-ng
```

#### Universal Install

```
$ git clone https://github.com/aircrack-ng/aircrack-ng && cd aircrack-ng
autoreconf -i
./configure
make
sudo make install
sudo ldconfig
```

### wifite2

#### Package Manager

```
$ sudo apt install -y wifite

$ sudo dnf install -y wifite

$ sudo pacman -S --noconfirm wifite
```

#### Universal Install

```
$ git clone https://github.com/kimocoder/wifite2.git && cd wifite2 \
sudo python3 setup.py install
```

## Install Drivers

```
$ sudo apt install -y realtek-rtl88xxau-dkms

$ yay -S --onconfirm rtl8812au-openhd-dkms-git
```

### Universal Install

```
$ git clone -b v5.6.4.2 https://github.com/aircrack-ng/rtl8812au.git && cd rtl8812au
sudo apt update
sudo apt install -y dkms build-essential libelf-dev linux-headers-$(uname -r)
make && sudo make install
```

---
## References

### Source Repositories

- [aircrack-ng: rtl8812au](https://github.com/aircrack-ng/rtl8812au)

- [cilynx: rtl88x2bu](https://github.com/cilynx/rtl88x2bu)

- [morrownr: 8814au](https://github.com/morrownr/8814au)

### Penetration Testing Tools

- [Penetration Testing Tools: USB Wi-Fi Adapters with monitor mode and wireless injection (100% compatible with Kali Linux) 2022](https://miloserdov.org/?p=2196)