# Network Mapper

Search Tag(s): #information-gathering #passive-reconnaissance #network-protocols #network-mapper

TODO: Fill this info

```
$ sudo nmap -p 53 -sSU --script dns-nsid <domain>.<tld>
```

```
$ nmap -n --script "(default and *dns*) or fcrdns or dns-srv-enum or dns-random-txid or dns-random-srcport" <IP>
```

---
## References

### InternalAllTheThings

- [InternalAllTheThings: Web Attack Surface](https://swisskyrepo.github.io/InternalAllTheThings/redteam/access/web-attack-surface/)

### Sidxparab

- [Sidxparab: Vertical Enumeration](https://sidxparab.gitbook.io/subdomain-enumeration-guide/types/vertical-enumeration)