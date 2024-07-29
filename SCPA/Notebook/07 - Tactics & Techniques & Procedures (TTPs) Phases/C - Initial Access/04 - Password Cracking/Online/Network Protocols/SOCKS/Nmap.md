# Nmap

```
$ nmap -p 1080 -Pn -sCV -vvv --script socks-brute --script-args "userdb=users.lst,passdb=passwords.lst,unpwndb.timelimit=30m" <IP>
```