# LDAP

## 01 - Hydra

TODO: Provide a syntax for brute forcing

`$ hydra -U <ldap2|ldap3>`

## 02 - Nmap

`$ nmap -p 389 --script ldap-brute --script-args ldap.base='"cn=users,dc=<domain_name>,dc=<tdl>"' <IP>`

## 03 - Metasploit

TODO: Fill this info

```
msf > use auxiliary/scanner/ldap/ldap_login
```