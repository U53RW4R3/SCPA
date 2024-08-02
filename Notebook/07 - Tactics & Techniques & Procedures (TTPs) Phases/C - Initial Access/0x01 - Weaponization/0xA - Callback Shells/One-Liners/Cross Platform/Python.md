# Python

## Base64 encoded one-line from CLI

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

- [don't code me on that: Python Reverse Shells](https://medium.com/dont-code-me-on-that/bunch-of-shells-python-b3fb1400b823)

- [PuckieStyle: Python one-line b64 Shellcode](https://www.puckiestyle.nl/python-one-line-shellcode/)