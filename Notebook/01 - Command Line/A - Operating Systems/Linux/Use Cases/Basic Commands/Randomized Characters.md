---
author(s):
  - Userware
tags:
  - command-line
  - use-cases
  - linux
---
# Randomized Characters

```
$ echo $RANDOM | md5sum | head -c 20; echo;

$ head -c 1024 /dev/urandom | tr -dc "[:alnum:]"

$ cat /proc/sys/kernel/random/uuid | sed 's/[-]//g' | head -c 20; echo

$ openssl rand -hex 16
```

---
## References

- [Linux Hint: Generate Random String Bash](https://linuxhint.com/generate-random-string-bash/)