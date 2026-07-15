---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - command-and-control
  - pwncat-vl
---
# 0x08 - Pwncat-vl

## Installation

### Package Manager

Install the packages according to your package manager.

```
$ pipx install git+https://github.com/Chocapikk/pwncat-vl
```

### Universal Install

Install from source.

```
$ git clone https://github.com/Chocapikk/pwncat-vl.git
cd pwncat-vl
python3 -m venv venv
source venv/bin/activate
pip install .
```

## Post Installation

Download plugin binaries for Windows post-exploitation.

```
$ pwncat-vl --download-plugins
```

---
## References

### Source Repositories

- [Chocapikk: Pwncat](https://github.com/Chocapikk/pwncat-vl)