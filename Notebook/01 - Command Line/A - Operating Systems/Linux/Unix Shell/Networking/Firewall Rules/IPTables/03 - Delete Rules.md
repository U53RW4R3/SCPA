---
author(s):
  - Userware
tags:
  - command-line
  - networking
  - linux
---
# 03 - Delete Rules

TODO: Fill this info

```
$ sudo iptables
```

```
# iptables -A INPUT -p icmp -m icmp --icmp-type any -j DROP
iptables -A OUTPUT -p icmp -j DROP
```

Delete current rules.

```
# iptables --flush
```

Delete current chains.

```
# iptables --delete-chain
```

---
## References

### Hacktricks

- [Hacktricks: Useful Linux Commands](https://book.hacktricks.wiki/en/linux-hardening/useful-linux-commands.html)