# Nmap

TODO: Fill in this information

```
$ nmap -p 80,443,8000,8080,8443 --script http-brute --script-args http.useragent='<user_agent>' <IP>

$ nmap -p 80,443,8000,8080,8443 --script http-proxy-brute --script-args http.useragent='<user_agent>' <IP>

$ nmap -p 80,443,8000,8080,8443 --script http-form-brute --script-args http.useragent='<user_agent>' <IP>

$ nmap -p 80,443,8000,8080,8443 --script http-frontpage-login --script-args http.useragent='<user_agent>' <IP>
```

---
## References

- [[User Agents]]

- [Hacking Articles: Nmap for Pentester Password Cracking](https://www.hackingarticles.in/nmap-for-pentester-password-cracking/)