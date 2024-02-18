# Nmap

```
$ nmap -p 27017,27018 -Pn -n --script mongodb-brute --script-args userdb=users.lst,passdb=passwords.lst <IP>
```