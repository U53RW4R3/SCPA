# Nmap

`$ sudo nmap -p 123 -sUV -Pn --script ntp-info,ntp-monlist <IP>`

`$ sudo nmap -p 123 -sUV --script "ntp-* and (discovery or vuln) and not (dos or brute)" <IP>`