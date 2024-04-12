# LDAPSearch

## 01 - Usage

- Note: tdl (Top Level Domain) is `.com`, `.net`, etc...

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN>\<username>' -w '<password>' -b "DC=<1_subdomain>,DC=<tdl>"`


TODO: Re-arrange from this section to post exploitation

## 03 - Enumerate User Accounts

### 3.1 - Usernames

- Retrieve Users

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN_NAME>\<username>' -w '' -b "CN=Users,DC=<subdomain>,DC=<tdl>"`

- Retrieve a specific user account

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN_NAME>\<username>' -w '' -b "CN=<username>,CN=Users,DC=<subdomain>,DC=<tdl>"`

- Retrieve Domain Users

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN_NAME>\<username>' -w '' -b "CN=Domain Users,CN=Users,DC=<subdomain>,DC=<tdl>"`

#### 1.3.2 - Administrators

- Retrieve Domain Admins

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN_NAME>\<username>' -w '' -b "CN=Domain Admins,CN=Users,DC=<subdomain>,DC=<tdl>"`

- Retrieve Enterprise Admins

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN_NAME>\<username>' -w '' -b "CN=Enterprise Admins,CN=Users,DC=<subdomain>,DC=<tdl>"`

- Retrieve Administrators

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN_NAME>\<username>' -w '' -b "CN=Administrators,CN=Builtin,DC=<subdomain>,DC=<tdl>"`

#### 1.3.3 - Remote Desktop Users

- Retrieve Remote Desktop Group

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN_NAME>\<username>' -w '' -b "CN=Remote Desktop Users,CN=Builtin,DC=<subdomain>,DC=<tdl>"`

### 1.4 - Retrieve Computers

`$ ldapsearch -x ldap://<IP> -D '<DOMAIN_NAME>\<username>' -w '' -b "CN=Computers,DC=<subdomain>,DC=<tdl>"`

---
## References

- [Hacktricks: Pentesting LDAP](https://book.hacktricks.xyz/pentesting/pentesting-ldap)

- [Malicious.link: LDAPSearch Reference](https://room362.com/posts/2022/ldapsearch-reference/)

- [Malicious.link: Dump LAPS passwords with ldapsearch](https://room362.com/posts/2017/dump-laps-passwords-with-ldapsearch/)

- [Techno Herder: How To Search LDAP using ldapsearch (With Examples)](https://hack.technoherder.com/how-to-search-ldap-using-ldapsearch-with-examples/)