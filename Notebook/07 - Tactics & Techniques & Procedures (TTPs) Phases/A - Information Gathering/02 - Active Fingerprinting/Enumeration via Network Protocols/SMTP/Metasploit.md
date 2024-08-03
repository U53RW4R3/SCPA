# Metasploit

## 01 - Banner Grab

```
msf > use auxiliary/scanner/smtp/smtp_version

msf auxiliary(scanner/smtp/smtp_version) > options

Module options (auxiliary/scanner/smtp/smtp_version):

   Name     Current Setting  Required  Description 
   ----     ---------------  --------  ----------- 
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT    25               yes       The target port (TCP) 
   THREADS  1                yes       The number of concurrent threads (max one per host) 

msf auxiliary(scanner/smtp/smtp_version) > set rhosts <IP>

msf auxiliary(scanner/smtp/smtp_version) > set threads 10

msf auxiliary(scanner/smtp/smtp_version) > run
```

- For domain controller

```
msf > use auxiliary/scanner/smtp/smtp_ntlm_domain

msf auxiliary(scanner/smtp/smtp_ntlm_domain) > options

Module options (auxiliary/scanner/smtp/smtp_ntlm_domain):

   Name         Current Setting  Required  Description
   ----         ---------------  --------  -----------
   EHLO_DOMAIN  localhost        yes       The domain to send with the EHLO command
   RHOSTS                        yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT        25               yes       The target port (TCP)
   THREADS      1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/smtp/smtp_ntlm_domain) > set rhosts <IP>

msf auxiliary(scanner/smtp/smtp_ntlm_domain) > run
```

## 02 - Username Bruteforce Enumeration

```
msf > use auxiliary/scanner/smtp/smtp_enum

msf auxiliary(scanner/smtp/smtp_enum) > options

Module options (auxiliary/scanner/smtp/smtp_enum):

   Name       Current Setting                                                Required  Description
   ----       ---------------                                                --------  -----------
   RHOSTS                                                                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      25                                                             yes       The target port (TCP)
   THREADS    1                                                              yes       The number of concurrent threads (max one per host)
   UNIXONLY   true                                                           yes       Skip Microsoft bannered servers when testing unix users
   USER_FILE  /usr/share/metasploit-framework/data/wordlists/unix_users.txt  yes       The file that contains a list of probable users accounts.

msf auxiliary(scanner/smtp/smtp_enum) > set rhosts <IP>

msf auxiliary(scanner/smtp/smtp_enum) > set threads 256

msf auxiliary(scanner/smtp/smtp_enum) > run
```

## 03 - SMTP Relay

Check for open SMTP relays that can be used to create a spoofed email when planning a spear phishing attempt.

```
msf > use auxiliary/scanner/smtp/smtp_relay

msf auxiliary(scanner/smtp/smtp_relay) > options

Module options (auxiliary/scanner/smtp/smtp_relay):

   Name      Current Setting     Required  Description
   ----      ---------------     --------  -----------
   EXTENDED  false               yes       Do all the 16 extended checks
   MAILFROM  sender@example.com  yes       FROM address of the e-mail
   MAILTO    target@example.com  yes       TO address of the e-mail
   RHOSTS                        yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     25                  yes       The target port (TCP)
   THREADS   1                   yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/smtp/smtp_relay) > set rhosts <IP>

msf auxiliary(scanner/smtp/smtp_relay) > set mailfrom <sender_email@target.com>

msf auxiliary(scanner/smtp/smtp_relay) > set mailto <victim@target.com>

msf auxiliary(scanner/smtp/smtp_relay) > set threads 2 <IP>

msf auxiliary(scanner/smtp/smtp_relay) > set extended <true | false>

msf auxiliary(scanner/smtp/smtp_relay) > exploit -j
```

---
## References

- [Hacktricks: Pentesting SMTP](https://book.hacktricks.xyz/pentesting/pentesting-smtp)

- [Hacktricks: SMTP Commands](https://book.hacktricks.xyz/pentesting/pentesting-smtp/smtp-commands)