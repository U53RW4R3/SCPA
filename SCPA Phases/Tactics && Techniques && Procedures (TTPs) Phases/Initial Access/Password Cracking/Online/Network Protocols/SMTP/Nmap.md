# Nmap

`$ nmap -p 25 --script smtp-brute --script-args smtp-brute.auth=<LOGIN | PLAIN | CRAM-MD5 | DIGEST-MD5 | NTLM>`

`$ nmap -p 25 --script smtp-brute --script-args smtp-brute.auth=LOGIN,userdb=users.lst,passdb=passwords.lst <IP>`