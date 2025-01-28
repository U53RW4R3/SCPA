---
author(s):
  - Userware
tags:
  - command-line
  - networking
  - linux
---
# 01 - Create Rules

TODO: Fill this info

Allow established connections.

```
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```


### 1.1 - Incoming Traffic

```
# iptables -A INPUT -i lo -j ACCEPT

iptables -A OUTPUT -o lo -j ACCEPT
```

#### SSH

```
# iptables -A INPUT -s 10.10.10.10/24 -p tcp -m tcp --dport 22 -j ACCEPT
```

#### HTTP

```
# iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
```

#### TLS

```
# iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 443 -j ACCEPT
```

#### DNS

```
# iptables -A INPUT -p udp -m udp --sport 53 -j ACCEPT
iptables -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT

# iptables -A INPUT -p tcp -m tcp --sport 53 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 53 -j ACCEPT
```

## Revert Settings

Revert back default policies.

```
# iptables -P INPUT DROP
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

---
## References

### Hacktricks

- [Hacktricks: Useful Linux Commands](https://book.hacktricks.wiki/en/linux-hardening/useful-linux-commands.html)

### CertCube

- [CertCube: Linux IP tables for Beginners](https://blog.certcube.com/linux-iptables-for-beginners/)

### Hackers Arise

- [Hackers Arise: Linux Basics for Hackers, Part 11: Linux Firewalls (iptables)](https://www.hackers-arise.com/post/linux-basics-for-hackers-part-11-linux-firewalls-iptables)