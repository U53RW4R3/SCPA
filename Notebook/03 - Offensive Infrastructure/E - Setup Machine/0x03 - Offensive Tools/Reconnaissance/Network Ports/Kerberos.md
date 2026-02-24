---
author(s):
  - Userware
tags:
  - offensive-infrastructure
  - offensive-tools
  - reconnaissance
---
# Kerberos

## 01 - #kerbrute

Clone the repository then compile.

```
$ git clone https://github.com/ropnop/kerbrute.git && cd kerbrute && \
make linux && chmod 755 dist/kerbrute_linux_amd64 && \
sudo mv dist/kerbrute_linux_amd64 /usr/local/bin/kerbrute && \
```

Download the pre-compiled binary.

```
$ sudo wget -O /usr/local/bin/kerbrute https://github.com/ropnop/kerbrute/releases/download/v1.0.3/kerbrute_linux_amd64 && \
sudo chmod 755 /usr/local/bin/kerbrute
```

---
## References

### Source Repositories

- [Kerbrute](https://github.com/ropnop/kerbrute)