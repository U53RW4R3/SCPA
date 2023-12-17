# Nmap

- Test all HTTP methods

`$ nmap -p 80,443 -Pn -n -sV --script http-methods --script-args http-methods.test=all <IP>`