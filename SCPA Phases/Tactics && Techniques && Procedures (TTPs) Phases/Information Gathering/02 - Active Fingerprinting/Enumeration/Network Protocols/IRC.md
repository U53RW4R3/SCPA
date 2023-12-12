# IRC

## 01 - Manual

### 1.1 - Banner Grab

`$ nc -nv <IP> 6667`

`$ openssl s_client -connect <IP>:6697 -quiet`

## 02 - Nmap

`$ nmap -p 6667 --script irc-info <IP>`

`$ nmap -p 6667 --script irc-botnet-channels --script-args 'irc-botnet-channels.channels={security,general,HTP}' <IP>`

---
## References

- [Pentesting IRC](https://book.hacktricks.xyz/pentesting/pentesting-irc)

- [List of Internet Relay Chat commands](https://en.wikipedia.org/wiki/List_of_Internet_Relay_Chat_commands)