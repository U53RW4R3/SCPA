---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - cross-platform
  - rustcat
---
# Rustcat

## 01 - Setup

Install it according to your distribution.

```
$ bash <(curl -s https://raw.githubusercontent.com/robiot/rustcat/master/pkg/debian-install.sh)

$ yay -S rustcat

$ emerge net-analyzer/rustcat
```

Universal installation.

```
$ cargo install rustcat
```

## 02 - Usage

Launch a listener on the attacker's machine in all addresses (`0.0.0.0`) with command history and command completion and `SIGINT` (`Ctrl + C`) blocking.

```
> rcat listen -ib <attacker_PORT>

> rcat l -ib <attacker_PORT>
```

---
## References

### Source Repositories

- [robiot: `rustcat`](https://github.com/robiot/rustcat)