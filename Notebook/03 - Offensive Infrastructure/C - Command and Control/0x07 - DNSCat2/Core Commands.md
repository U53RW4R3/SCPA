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
# Core Commands

TODO: Provide a usage example with dnscat2

## Setup

### Dependencies

```
$ sudo apt install -y ruby-dev
```

### Install DNSCat2

```
$ git clone https://github.com/iagox86/dnscat2.git && \
cd dnscat2/server/ && bundle install
```

## Help Menu

```
$ sudo ./dnscat2.rb -h
```

## Usage

### Shell Handler

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

---
## References

- [DNSCat2](https://github.com/iagox86/dnscat2)

- [Phra: Using DNS over HTTPS as a C2 Channel](https://iwantmore.pizza/posts/dnscat2-over-doh.html)

- [Cynet: How Hackers Use DNS Tunneling to Own Your Network](https://www.cynet.com/attack-techniques-hands-on/how-hackers-use-dns-tunneling-to-own-your-network/)

- [CryptoWorld: How to organize DNS tunneling](https://cryptoworld.su/kak-organizovat-dns-tunneling/)