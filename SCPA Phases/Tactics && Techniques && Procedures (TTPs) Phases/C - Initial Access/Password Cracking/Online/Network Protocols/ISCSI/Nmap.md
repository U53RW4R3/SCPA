# Nmap

`$ nmap -p 3260 -Pn -n -sV --script iscsi-brute --script-args "userdb=users.txt,passdb=passwords.txt" <IP>`