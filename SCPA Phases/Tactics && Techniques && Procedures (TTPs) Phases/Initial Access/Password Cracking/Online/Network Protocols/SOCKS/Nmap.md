# Nmap

```
$ nmap -p 1080 -vvv -sCV --script socks-brute --script-args "userdb=users.lst,passdb=passwords.lst,unpwndb.timelimit=30m" <IP>
```