---
author(s):
  - Userware
tags:
  - information-gathering
  - active-reconnaissance
  - network-protocols
  - ldap
  - network-mapper
---
# LDAP

## 01 - Usage

### 1.1 - LDAPDomainDump

```
$ ldapdomaindump <IP> [-r <IP>] -u '<domain>\<username>' -p '<password>' [--authtype SIMPLE] --no-json --no-grep -o ldap-loot-dir
```

### 1.2 - LDAPSearch

> [!INFO] What TLD looks like?
> TLD (Top Level Domain) looks like this `.com`, `.net`, etc.

```
$ ldapsearch -x ldap://<IP> -D '<DOMAIN>\<username>' -w '<password>' -b "DC=<1_subdomain>,DC=<tdl>"
```

### 1.3 - Samba-Tool

```

```

## 02 - Anonymous Credentials

### 2.1 - Manual

```

```

### 2.2 - Network Mapper

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

TODO: Re-arrange from this section to post exploitation

## 01 - LDAP Search

```
msf > use auxiliary/gather/ldap_query

msf auxiliary(gather/ldap_query) > options

Module options (auxiliary/gather/ldap_query):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   BASE_DN                         no        LDAP base DN if you already have it
   DOMAIN                          no        The domain to authenticate to
   OUTPUT_FORMAT  table            yes       The output format to use (Accepted: csv, table, json)
   PASSWORD                        no        The password to authenticate with
   RHOSTS                          yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT          389              yes       The target port
   SSL            false            no        Enable SSL on the LDAP connection
   USERNAME                        no        The username to authenticate with


   When ACTION is RUN_SINGLE_QUERY:

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   QUERY_ATTRIBUTES                   no        Comma seperated list of attributes to retrieve from the server
   QUERY_FILTER                       no        Filter to send to the target LDAP server to perform the query


   When ACTION is RUN_QUERY_FILE:

   Name             Current Setting  Required  Description
   ----             ---------------  --------  -----------
   QUERY_FILE_PATH                   no        Path to the JSON or YAML file to load and run queries from


Auxiliary action:

   Name           Description
   ----           -----------
   ENUM_ACCOUNTS  Dump info about all known user accounts in the domain.



View the full module info with the info, or info -d command.

msf auxiliary(gather/ldap_query) > set
```

## 02 - LDAP Hashdump

```
msf > use auxiliary/gather/ldap_hashdump

msf auxiliary(gather/ldap_hashdump) > options

Module options (auxiliary/gather/ldap_hashdump):

   Name          Current Setting                                              Required  Description
   ----          ---------------                                              --------  -----------
   BASE_DN                                                                    no        LDAP base DN if you already have it
   DOMAIN                                                                     no        The domain to authenticate to
   MAX_LOOT                                                                   no        Maximum number of LDAP entries to loot
   PASSWORD                                                                   no        The password to authenticate with
   PASS_ATTR     userPassword, sambantpassword, sambalmpassword, mailuserpas  yes       LDAP attribute, that contains password hashes
                 sword, password, pwdhistory, passwordhistory, clearpassword
   READ_TIMEOUT  600                                                          no        LDAP read timeout in seconds
   RHOSTS                                                                     yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT         636                                                          yes       The target port
   SSL           true                                                         no        Enable SSL on the LDAP connection
   THREADS       1                                                            yes       The number of concurrent threads (max one per host)
   USERNAME                                                                   no        The username to authenticate with
   USER_ATTR     dn                                                           no        LDAP attribute(s), that contains username


Auxiliary action:

   Name  Description
   ----  -----------
   Dump  Dump all LDAP data



View the full module info with the info, or info -d command.

msf auxiliary(gather/ldap_hashdump) >
```

---
## References

- [Hacktricks: Pentesting LDAP](https://book.hacktricks.xyz/pentesting/pentesting-ldap)

- [Rapid7: Metasploit Framework - LDAP Auxiliary Module](https://docs.metasploit.com/docs/pentesting/metasploit-guide-ldap.html)