---
author(s):
  - Userware
tags:
  - command-line
  - networking
  - linux
---
# IP Address

Network overview

```
$ nmcli -o
```

Display network devices in details

```
$ nmcli -p connection show "<name>"

$ nmcli -p connection show id "<name>"

$ nmcli -p connection show filename /path/to/file.nmconnection

$ nmcli -p connection show uuid "<uuid>"

$ nmcli -p device show
```

Check route

```
$ ip route show

$ route -n
```

Print network manager configuration.

```
$ NetworkManager --print-config
```