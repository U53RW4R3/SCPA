# Nmap

## 01 - Anonymous Credentials

```
$ nmap -p 389 -n -sV --script "ldap* and not brute" <IP>
```

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

## 02 - LDAP Search

Enumerate sAMAccountName

```
$ nmap -p 389 --script ldap-search --script-args 'ldap.username="cn=<username>,cn=users,dc=<domain>,dc=<tdl>",ldap.password=<password>, ldap.qfilter=users,ldap.attrib=sAMAccountName' <IP>
```

Enumerate operating system

```
$ nmap -p 389 --script ldap-search --script-args 'ldap.username="cn=<username>,cn=users,dc=<domain>,dc=<tdl>",ldap.password=<password>,ldap.qfilter=custom,ldap.searchattrib="operatingSystem",ldap.searchvalue="Windows *Server*",ldap.atrrib={operatingSystem,whencreated,OperatingSystemServicePack}' <IP>
```

## 03 - Novel Universal Password

```
$ nmap -p 636 --script ldap-novell-getpass --script-args 'ldap-novell-getpass.username="CN=<username>,O=<company>",ldap-novell-getpass.password=<password>,ldap-novell-getpass.account="CN=<username>,OU=<project>,O=<company>"'
```

## 04 - LDAP RootDSE

```
$ nmap -p 389 --script ldap-rootdse <IP>
```