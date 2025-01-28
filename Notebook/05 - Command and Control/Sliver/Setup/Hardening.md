---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - sliver
  - firewall-rules
---

# Hardening

## 01 - Teamserver

```
$ sudo systemctl stop sliver
```

```json
$ cat /root/.sliver/configs/server.json

{
    "daemon_mode": true,
    "daemon": {
        "host": "",
        "port": <PORT>
    },
    "logs": {
        "level": 4,
        "grpc_unary_payloads": false,
        "grpc_stream_payloads": false,
        "tls_key_logger": false
    },
    "jobs": {
        "multiplayer": null
    },
    "watch_tower": null,
    "go_proxy": ""
```

```
$ sudo systemctl daemon-reload

$ sudo systemctl start sliver
```

## 02 - Firewall Rules

```
# mkdir /etc/iptables
# iptables -I INPUT 1 -p tcp -s 0.0.0.0/0 --dport <PORT> -j DROP
# iptables -I INPUT 1 -p tcp -s 127.0.0.1 --dport <PORT> -j ACCEPT
# iptables-save > /etc/iptables/rules.v4
```

- A script to autorun after reboot. Run this as root (without `sudo`)

```bash
cat << EOF > /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iptables-restore < /etc/iptables/rules.v4

exit 0
EOF
```

- Change permission and start the service.

```
$ sudo chmod 755 /etc/rc.local

$ sudo systemctl start rc-local
```