---
author(s):
  - Userware
tags:
  - information-gathering
  - active-fingerprinting
  - network-ports
  - irc
  - network-mapper
---
# IRC

## 01 - Banner Grab

### 1.1 - Netcat

```
$ nc -nv <IP> 6667
```

### 1.2 - Irssi

```
$ irssi -c <IP>

/connect <IP>
```

## 02 - TLS Certificate

```
$ openssl s_client -connect <IP>:6697 -quiet
```

## 03 - IRC Information

```
$ nmap -p 6667 --script irc-info <IP>
```

## 04 - IRC Botnet Channels

```
$ nmap -p 6667 --script irc-botnet-channels --script-args 'irc-botnet-channels.channels={security,general,HTP}' <IP>
```

---
## References

### Wikipedia

- [Wikipedia: List of Internet Relay Chat commands](https://en.wikipedia.org/wiki/List_of_Internet_Relay_Chat_commands)

### Hacktricks

- [Hacktricks: Pentesting IRC](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-irc.html)