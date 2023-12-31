# Nmap

`$ nmap -p 6667 --script irc-brute --script-args userdb=users.lst,passdb=passwords.lst <IP>`

`$ nmap -p 6667 --script irc-sasl-brute --script-args userdb=users.lst,passdb=passwords.lst <IP>`