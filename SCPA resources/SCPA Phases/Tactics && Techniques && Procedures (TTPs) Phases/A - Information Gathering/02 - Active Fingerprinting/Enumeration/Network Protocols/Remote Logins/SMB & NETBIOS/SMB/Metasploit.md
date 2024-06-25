# Metasploit
## 01 - Banner Grab

```
msf > use auxiliary/scanner/smb/smb_version

msf auxiliary(scanner/smb/smb_version) > options

Module options (auxiliary/scanner/smb/smb_version):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   THREADS  1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/smb/smb_version) > set rhosts <IP>

msf auxiliary(scanner/smb/smb_version) > set threads 5

msf auxiliary(scanner/smb/smb_version) > run -j
```

## 03 - Users

```
msf > use auxiliary/scanner/smb/smb_enumusers

msf auxiliary(scanner/smb/smb_enumusers) > options

Module options (auxiliary/scanner/smb/smb_enumusers):

   Name          Current Setting  Required  Description
   ----          ---------------  --------  -----------
   DB_ALL_USERS  false            no        Add all enumerated usernames to the database
   RHOSTS                         yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   SMBDomain     .                no        The Windows domain to use for authentication
   SMBPass                        no        The password for the specified username
   SMBUser                        no        The username to authenticate as
   THREADS       1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/smb/smb_enumusers) > set smbuser <username>

msf auxiliary(scanner/smb/smb_enumusers) > set smbpass <password | aad3b435b51404eeaad3b435b51404ee:<nt_hash>>

msf auxiliary(scanner/smb/smb_enumusers) > set rhosts <IP>

msf auxiliary(scanner/smb/smb_enumusers) > set smbdomain [<domain_name>]

msf auxiliary(scanner/smb/smb_enumusers) > set threads 4

msf auxiliary(scanner/smb/smb_enumusers) > run
```

TODO: Fill this info

- Metasploit auxiliary bruteforce users via SID lookups

```
msf > use auxiliary/scanner/smb/smb_lookupsid

msf auxiliary(scanner/smb/smb_lookupsid) > show actions 

Auxiliary actions:

       Name    Description
       ----    -----------
       DOMAIN  Enumerate domain accounts
   =>  LOCAL   Enumerate local accounts

msf auxiliary(scanner/smb/smb_lookupsid) > options

Module options (auxiliary/scanner/smb/smb_lookupsid):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   MaxRID     4000             no        Maximum RID to check
   MinRID     500              no        Starting RID to check
   RHOSTS                      yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   SMBDomain  .                no        The Windows domain to use for authentication
   SMBPass                     no        The password for the specified username
   SMBUser                     no        The username to authenticate as
   THREADS    1                yes       The number of concurrent threads (max one per host)


Auxiliary action:

   Name   Description
   ----   -----------
   LOCAL  Enumerate local accounts



View the full module info with the info, or info -d command.

msf auxiliary(scanner/smb/smb_lookupsid) > set smbuser <username>

msf auxiliary(scanner/smb/smb_lookupsid) > set smbpass <password | aad3b435b51404eeaad3b435b51404ee:<nt_hash>>

msf auxiliary(scanner/smb/smb_lookupsid) > set smbdomain [<domain_name>]

msf auxiliary(scanner/smb/smb_lookupsid) > set action <LOCAL | DOMAIN>

msf auxiliary(scanner/smb/smb_lookupsid) > set rhosts <target_IP>

msf auxiliary(scanner/smb/smb_lookupsid) > set minrid <min_id_range>

msf auxiliary(scanner/smb/smb_lookupsid) > set maxrid <max_id_range>

msf auxiliary(scanner/smb/smb_lookupsid) > set threads 2

msf auxiliary(scanner/smb/smb_lookupsid) > run
```