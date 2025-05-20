# IRC

## Shodan

```
port:6667,6697
```

## Censys

```
host.services.protocol=IRC
host.services.port: 6667 and host.services.port: 6697 and not host.services:(not port:{6667, 6697})
```

---
## References

### Backlinks

- [[07 - Tactics & Techniques & Procedures (TTPs) Phases/A - Information Gathering/0x02 - Active Fingerprinting/Network Ports/Cross Platform/IRC]]

### IRCStats

- [IRCStats.org Research Project](https://ircstats.org)