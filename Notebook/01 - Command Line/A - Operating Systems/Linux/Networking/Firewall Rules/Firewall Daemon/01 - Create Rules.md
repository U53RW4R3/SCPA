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

```
# firewall-cmd --list-all

# firewall-cmd --list-all --permanent

# firewall-cmd --get-services
```

```
# firewall-cmd --add-service=http --permanent
```

```
# firewall-cmd --add-port=123/tcp

# firewall-cmd --add-port=123/udp
```

---
## References

- [Hackers Arise: Uncomplicated Firewall (ufw)](https://www.hackers-arise.com/post/linux-firewalls-uncomplicated-firewall-ufw)