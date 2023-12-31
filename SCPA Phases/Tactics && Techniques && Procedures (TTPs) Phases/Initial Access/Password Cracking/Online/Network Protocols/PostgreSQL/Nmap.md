# Nmap

`$ nmap -p 5432 --script pgsql-brute --script-args userdb=users.lst,passdb=passwords.lst <IP>`