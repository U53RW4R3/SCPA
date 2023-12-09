# Nmap

`$ nmap -p 88 --script=krb5-enum-users --script-args krb5-enum-users.realm="<domain_name>",userdb=<usernames.txt> <IP>`