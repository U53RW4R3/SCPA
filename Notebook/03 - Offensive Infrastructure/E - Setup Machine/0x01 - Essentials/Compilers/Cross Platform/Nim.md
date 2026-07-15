---
author(s):
  - Userware
tags:
  - helpers
  - command-line
  - compiler
  - nim
  - cross-platform
---
# Nim

## 01 - Install Nim Compiler

Install the packages according to your package manager.

```
$ sudo apt install -y nim zippy nimcrypto

$ yay -S --noconfirm nim nimlangserver-bin nimble-git
```

Universal installer.

```
$ curl -sSf https://nim-lang.org/choosenim/init.sh | sh
```

## 02 - Install Required Dependencies

```
$ nimble install winim zippy nimcrypto
```

## 03 - Cross compile

```
$ nim c -d=mingw --app=console --cpu=<amd64 | i386> payload.nim
```

---
## References

### Source Repositories

- [arnetheduck: nlvm](https://github.com/arnetheduck/nlvm)