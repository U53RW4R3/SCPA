# Nmap

`$ nmap -p 6667 --script irc-info <IP>`

`$ nmap -p 6667 --script irc-botnet-channels --script-args 'irc-botnet-channels.channels={security,general,HTP}' <IP>`