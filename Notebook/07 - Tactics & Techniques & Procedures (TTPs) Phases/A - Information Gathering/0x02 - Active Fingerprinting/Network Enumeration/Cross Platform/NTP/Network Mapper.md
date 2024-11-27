# Network Mapper

Search Tag(s): #information-gathering #active-reconnaissance #network-protocols #network-mapper

TODO: Create headers to each commands.

```
$ sudo nmap -p 123 -sUV -Pn --script ntp-info,ntp-monlist <IP>
```

```
$ sudo nmap -p 123 -sUV --script "ntp-* and (discovery or vuln) and not (dos or brute)" <IP>
```