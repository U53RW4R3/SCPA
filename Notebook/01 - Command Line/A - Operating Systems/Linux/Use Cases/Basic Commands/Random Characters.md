---
author(s):
  - Userware
tags:
  - command-line
  - use-cases
  - linux
---
# Random Characters

Using hash digest with random number.

```
$ echo $RANDOM | cksum -a md5 --untagged | head -c 20; echo;
```

Random alphanumeric characters.

```
$ head -c 1024 /dev/urandom | tr -dc "[:alnum:]"
```

Random UUID characters.

```
$ sed 's/[-]//g' /proc/sys/kernel/random/uuid | head -c 20; echo
```

Random hexadecimal bytes.

```
$ openssl rand -hex 16
```

Random base64 characters.

```
$ openssl rand -base64 21
```