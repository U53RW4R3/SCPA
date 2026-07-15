---
author(s):
  - Userware
tags:
  - help-menu
  - red-team-infrastructure
  - command-and-control
  - interactive-shell
  - dnscat2
---
# Installation

## Dependencies

```
$ sudo apt install -y ruby-dev
```

## Install DNSCat2

```
$ git clone https://github.com/iagox86/dnscat2.git && \
cd dnscat2/server/ && bundle install
```

---
## References

### Source Repositories

- [DNSCat2](https://github.com/iagox86/dnscat2)

### Phra

- [Phra: Using DNS over HTTPS as a C2 Channel](https://iwantmore.pizza/posts/dnscat2-over-doh.html)

### Cynet

- [Cynet: How Hackers Use DNS Tunneling to Own Your Network](https://www.cynet.com/attack-techniques-hands-on/how-hackers-use-dns-tunneling-to-own-your-network/)

### CryptoWorld

- [CryptoWorld: How to organize DNS tunneling](https://cryptoworld.su/kak-organizovat-dns-tunneling/)