# Nmap

`$ nmap -p 6667 -Pn --script irc-brute --script-args userdb=users.lst,passdb=passwords.lst <IP>`

`$ nmap -p 6667 -Pn --script irc-sasl-brute --script-args userdb=users.lst,passdb=passwords.lst <IP>`