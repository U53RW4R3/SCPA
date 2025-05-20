# System Audit

## Lynis

### Setup

#### Clone the repository

```
$ git clone https://github.com/CISOfy/lynis && cd lynis
```

#### Download archive file

```
$ wget --no-hsts -qO lynis.zip [--no-check-certificate] https://github.com/CISOfy/lynis/archive/refs/heads/master.zip

$ curl -so lynis.zip [-k] https://github.com/CISOfy/lynis/archive/refs/heads/master.zip
```

Then extract the archive.

```
$ unzip lynis.zip

$ 7z x lynis.zip
```

### Usage

```
$ ./lynis audit system
```

---
## References

### Source Repositories

- [CISOfy: Lynis](https://github.com/CISOfy/Lynis)

### CISOfy

- [Lynis](https://cisofy.com/lynis)

### Null Byte

- [Null Byte: Locking Down Linux - Using Ubuntu as Your Primary OS, Part 4 (Auditing, Antivirus & Monitoring)](https://null-byte.wonderhowto.com/how-to/locking-down-linux-using-ubuntu-as-your-primary-os-part-4-auditing-antivirus-monitoring-0185572/)