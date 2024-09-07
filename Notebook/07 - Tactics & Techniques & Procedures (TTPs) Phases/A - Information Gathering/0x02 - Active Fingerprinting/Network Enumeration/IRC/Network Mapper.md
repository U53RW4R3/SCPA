# Network Mapper

Search Tag(s): #information-gathering #active-reconnaissance #network-protocols #network-mapper

TODO: Create headers to each commands.

```
$ nmap -p 6667 --script irc-info <IP>
```

```
$ nmap -p 6667 --script irc-botnet-channels --script-args 'irc-botnet-channels.channels={security,general,HTP}' <IP>
```