# 06 - Credentials

Search Tag(s): #metasploit-framework #command-and-control

## 6.1 - Help Menu

```
Credentials Backend Commands
============================

    Command       Description
    -------       -----------
    creds         List all credentials in the database

msf > creds -h

With no sub-command, list credentials. If an address range is
given, show only credentials with logins on hosts within that
range.

Usage - Listing credentials:
  creds [filter options] [address range]

Usage - Adding credentials:
  creds add uses the following named parameters.
    user      :  Public, usually a username
    password  :  Private, private_type Password.
    ntlm      :  Private, private_type NTLM Hash.
    postgres  :  Private, private_type postgres MD5
    ssh-key   :  Private, private_type SSH key, must be a file path.
    hash      :  Private, private_type Nonreplayable hash
    jtr       :  Private, private_type John the Ripper hash type.
    realm     :  Realm, 
    realm-type:  Realm, realm_type (domain db2db sid pgdb rsync wildcard), defaults to domain.

Examples: Adding
   # Add a user, password and realm
   creds add user:admin password:notpassword realm:workgroup
   # Add a user and password
   creds add user:guest password:'guest password'
   # Add a password
   creds add password:'password without username'
   # Add a user with an NTLMHash
   creds add user:admin ntlm:E2FC15074BF7751DD408E6B105741864:A1074A69B1BDE45403AB680504BBDD1A
   # Add a NTLMHash
   creds add ntlm:E2FC15074BF7751DD408E6B105741864:A1074A69B1BDE45403AB680504BBDD1A
   # Add a Postgres MD5
   creds add user:postgres postgres:md5be86a79bf2043622d58d5453c47d4860
   # Add a user with an SSH key
   creds add user:sshadmin ssh-key:/path/to/id_rsa
   # Add a user and a NonReplayableHash
   creds add user:other hash:d19c32489b870735b5f587d76b934283 jtr:md5
   # Add a NonReplayableHash
   creds add hash:d19c32489b870735b5f587d76b934283

General options
  -h,--help             Show this help information
  -o <file>             Send output to a file in csv/jtr (john the ripper) format.
                        If file name ends in '.jtr', that format will be used.
                        If file name ends in '.hcat', the hashcat format will be used.
                        csv by default.
  -d,--delete           Delete one or more credentials

Filter options for listing
  -P,--password <text>  List passwords that match this text
  -p,--port <portspec>  List creds with logins on services matching this port spec
  -s <svc names>        List creds matching comma-separated service names
  -u,--user <text>      List users that match this text
  -t,--type <type>      List creds of the specified type: password, ntlm, hash or any valid JtR format
  -O,--origins <IP>     List creds that match these origins
  -r,--realm <realm>    List creds that match this realm
  -R,--rhosts           Set RHOSTS from the results of the search
  -v,--verbose          Don't truncate long password hashes

Examples, John the Ripper hash types:
  Operating Systems (starts with)
    Blowfish ($2a$)   : bf
    BSDi     (_)      : bsdi
    DES               : des,crypt
    MD5      ($1$)    : md5
    SHA256   ($5$)    : sha256,crypt
    SHA512   ($6$)    : sha512,crypt
  Databases
    MSSQL             : mssql
    MSSQL 2005        : mssql05
    MSSQL 2012/2014   : mssql12
    MySQL < 4.1       : mysql
    MySQL >= 4.1      : mysql-sha1
    Oracle            : des,oracle
    Oracle 11         : raw-sha1,oracle11
    Oracle 11 (H type): dynamic_1506
    Oracle 12c        : oracle12c
    Postgres          : postgres,raw-md5

Examples, listing:
  creds               # Default, returns all credentials
  creds 1.2.3.4/24    # Return credentials with logins in this range
  creds -O 1.2.3.4/24 # Return credentials with origins in this range
  creds -p 22-25,445  # nmap port specification
  creds -s ssh,smb    # All creds associated with a login on SSH or SMB services
  creds -t ntlm       # All NTLM creds

Example, deleting:
  # Delete all SMB credentials
  creds -d -s smb
```

## 6.2 - Usage

```
msf > creds
Credentials
===========

host       origin     service        public              private                                                            realm  private_type  JtR Format
----       ------     -------        ------              -------                                                            -----  ------------  ----------
10.0.2.15  10.0.2.15  445/tcp (smb)  WDAGUtilityAccount  aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  WDAGUtilityAccount  aad3b435b51404eeaad3b435b51404ee:4cd2a45742e6693f6416abf9e2982956         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  Winpwn10            aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  Winpwn10            aad3b435b51404eeaad3b435b51404ee:8034586795ebaf0427cc3417ebea341c         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  Administrator       aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  DefaultAccount      aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  Guest               aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  administrator       aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  guest               aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  defaultaccount      aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  wdagutilityaccount  aad3b435b51404eeaad3b435b51404ee:4cd2a45742e6693f6416abf9e2982956         NTLM hash     nt,lm
10.0.2.15  10.0.2.15  445/tcp (smb)  winpwn10            aad3b435b51404eeaad3b435b51404ee:8034586795ebaf0427cc3417ebea341c         NTLM hash     nt,lm
```


---
## References

- [Metasploit For Pentester Creds](https://www.hackingarticles.in/metasploit-for-pentester-creds/)