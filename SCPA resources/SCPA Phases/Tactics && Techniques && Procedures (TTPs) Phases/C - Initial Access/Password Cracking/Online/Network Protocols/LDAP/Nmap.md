# Nmap

```
$ nmap -p 389 --script ldap-brute --script-args ldap.base='"cn=users,dc=<domain>,dc=<tdl>"' <IP>
```