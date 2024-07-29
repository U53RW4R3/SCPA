# Nmap

```
$ nmap -p 23 -Pn -n --script telnet-brute --script-args "userdb=users.lst,passdb=passwords.lst,telnet-brute.timeout=<seconds>s" <IP>
```

---
## References

- [Hacking Articles: Nmap for Pentester Password Cracking](https://www.hackingarticles.in/nmap-for-pentester-password-cracking/)