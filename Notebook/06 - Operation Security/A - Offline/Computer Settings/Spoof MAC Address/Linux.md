---
author(s):
  - Userware
tags:
  - operation-security
  - spoofing
  - command-line
  - linux
---
# Linux

## 01 - Manual

`ip` command

```
$ sudo ip link set dev <interface> down && \
sudo ip link set dev <interface> address $(openssl rand -hex 6 | sed 's/../&:/g;s/:$//') && \
sudo ip link set dev <interface> up
```

`ifconfig` command

```
$ sudo ifconfig <interface> hw ether $(openssl rand -hex 6 | sed 's/../&:/g;s/:$//')
```

## 02 - Macchanger

### 2.1 - Help Menu

```
$ macchanger -h
GNU MAC Changer
Usage: macchanger [options] device

  -h,  --help                   Print this help
  -V,  --version                Print version and exit
  -s,  --show                   Print the MAC address and exit
  -e,  --ending                 Don't change the vendor bytes
  -a,  --another                Set random vendor MAC of the same kind
  -A                            Set random vendor MAC of any kind
  -p,  --permanent              Reset to original, permanent hardware MAC
  -r,  --random                 Set fully random MAC
  -l,  --list[=keyword]         Print known vendors
  -b,  --bia                    Pretend to be a burned-in-address
  -m,  --mac=XX:XX:XX:XX:XX:XX  Set the MAC XX:XX:XX:XX:XX:XX

Report bugs to https://github.com/alobbs/macchanger/issues
```

### 2.2 - Usage

Change the MAC Address randomly

```
$ sudo macchanger -r <interface>
```

Set the MAC Address manually

```
$ sudo macchanger -r <interface> -m ab:cd:ef:12:34:56
```

### 2.3 - Use Case

#### 2.3.1 - Schedule Task

Setup a cronjob when rebooting the machine.

```
$ sudo crontab -e
@reboot macchanger -r <interface>
```

#### 2.3.2 - Impersonate Device

TODO: Fill this info with a specific backlink.

You can bypass filters...