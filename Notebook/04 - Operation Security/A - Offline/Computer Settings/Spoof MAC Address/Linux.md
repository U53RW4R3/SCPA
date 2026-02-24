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

## 02 - [[Macchanger]]

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

You can bypass a login portal by impersonating the router's mac addresses as the gateway.

```
$ sudo macchanger -m <mac_address> <interface>
```