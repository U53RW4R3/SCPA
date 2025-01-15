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
# Credit Cards

## Visa

```
$ grep -Eo "4[0-9]{3}[ -]?[0-9]{4}[ -]?[0-9]{4}[ -]?[0-9]{4}" file.txt > visa.txt
```

## MasterCard

```
$ grep -Eo "5[0-9]{3}[ -]?[0-9]{4}[ -]?[0-9]{4}[ -]?[0-9]{4}" file.txt > mastercard.txt
```

## American Express

```
$ grep -Eo "\b3[47][0-9]{13}\b" file.txt > american-express.txt
```

## Diners Club

```
$ grep -Eo "\b3(?:0[0-5]|[68][0-9])[0-9]{11}\b" file.txt > diners.txt
```

## Discover

```
$ grep -Eo "6011[ -]?[0-9]{4}[ -]?[0-9]{4}[ -]?[0-9]{4}" file.txt > discover.txt
```

## JCB

```
$ grep -Eo "\b(?:2131|1800|35d{3})d{11}\b" file.txt > jcb.txt
```

## AMEX

```
$ grep -Eo "3[47][0-9]{2}[ -]?[0-9]{6}[ -]?[0-9]{5}" file.txt > amex.txt
```

---
## References

### Hacktricks

- [Hacktricks: Useful Linux Commands](https://book.hacktricks.wiki/en/linux-hardening/useful-linux-commands.html)