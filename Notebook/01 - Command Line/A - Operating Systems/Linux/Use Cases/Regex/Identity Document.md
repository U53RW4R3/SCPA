---
author(s):
  - Userware
tags:
  - command-line
  - networking
  - regex
  - use-cases
  - linux
---
# Identity Document

## Social Security Number (SSN)

```
$ grep -Eo "[0-9]{3}[ -]?[0-9]{2}[ -]?[0-9]{4}" file.txt > ssn.txt
```

## Driver License

```
$ grep -E -o "[0-9]{4}[ -]?[0-9]{2}[ -]?[0-9]{4}" file.txt > indiana-dln.txt
```

## Passport Cards

USA Passport Cards

```
$ grep -E -o "C0[0-9]{7}" file.txt > usa-pass-card.txt
```

## Passport Numbers

Extract US Passport Number

```
$ grep -E -o "[23][0-9]{8}" file.txt > usa-pass-num.txt
```

---
## References

### Hacktricks

- [Hacktricks: Useful Linux Commands](https://book.hacktricks.wiki/en/linux-hardening/useful-linux-commands.html)