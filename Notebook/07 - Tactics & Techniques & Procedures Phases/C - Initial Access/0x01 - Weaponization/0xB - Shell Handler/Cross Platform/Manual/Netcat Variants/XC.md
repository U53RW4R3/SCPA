---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - cross-platform
  - xc
---
# XC

## Setup

```
$ git clone --recurse-submodules https://github.com/xct/xc.git

GO111MODULE=off go get golang.org/x/sys/...
GO111MODULE=off go get golang.org/x/text/encoding/unicode
GO111MODULE=off go get github.com/hashicorp/yamux
GO111MODULE=off go get github.com/libp2p/go-reuseport
```

```
$ python3 build.py
```

## Usage

```
> xc -l -p <PORT>

$ rlwrap xc -l -p <PORT>
```

---
## References

### Source Repositories

- [xct: `xc`](https://github.com/xct/xc)