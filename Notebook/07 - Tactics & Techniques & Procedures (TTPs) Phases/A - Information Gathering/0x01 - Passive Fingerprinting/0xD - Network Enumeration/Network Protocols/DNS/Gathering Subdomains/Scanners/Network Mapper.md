# Network Mapper

Search Tag(s): #information-gathering #passive-reconnaissance #network-protocols #network-mapper

TODO: Fill this info

```
$ sudo nmap -p 53 -sSU --script dns-nsid <domain.com>
```

```
$ nmap -n --script "(default and *dns*) or fcrdns or dns-srv-enum or dns-random-txid or dns-random-srcport" <IP>
```

---
## References

### InternalAllTheThings

- [InternalAllTheThings: Web Attack Surface](https://swisskyrepo.github.io/InternalAllTheThings/redteam/access/web-attack-surface/)