---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - havoc
---
# Hardening

Search Tag(s): #red-team-infrastructure #havoc

## 01 - Firewall Rules

```
# mkdir /etc/iptables

iptables -I INPUT 1 -p tcp -s 0.0.0.0/0 --dport 40056 -j DROP

iptables -I INPUT 1 -p tcp -s 127.0.0.1 --dport 40056 -j ACCEPT

iptables-save > /etc/iptables/rules.v4
```

A script to autorun after reboot. Run this as root (without `sudo`).

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

```
$ sudo chmod 755 /etc/rc.local

$ sudo systemctl start rc-local
```

## 02 - Domain Fronting

TODO: Provide an example usage for Havoc C2

---
## References

- [Havoc ProfileGenerator](https://github.com/0xv1n/Havoc-ProfileGenerator)

- [WesleyWong420: RedTeamOps-Havoc-101](https://github.com/WesleyWong420/RedTeamOps-Havoc-101)