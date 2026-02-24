---
author(s):
  - Userware
tags:
  - dnsenum
---
# DNSEnum

## Setup

### Package Manager

Install it according to your package manager.

```
$ sudo apt install -y dnsenum2
```

### Universal Install

Install the rest of the dependencies for `dnsenum`.

```
$ sudo apt install -y cpanminus

$ sudo dnf install -y cpan

$ sudo pacman -S --noconfirm cpanminus perl-xml-writer

$ sudo cpanm String::Random Net::Netmask XML::Writer
```

Clone the repository

```
$ git clone https://github.com/SparrowOchon/dnsenum2 && cd dnsenum2 && \
make && sudo make install
```

---
## References

### Source Repositories

- [SparrowOchon: dnsenum2](https://github.com/SparrowOchon/dnsenum2)

### Kali Tools

- [Kali Tools: `dnsenum`](https://www.kali.org/tools/dnsenum/)