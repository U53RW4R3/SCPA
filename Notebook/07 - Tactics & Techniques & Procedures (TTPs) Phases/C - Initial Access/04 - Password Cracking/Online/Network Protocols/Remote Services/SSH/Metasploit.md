# Metasploit

TODO: Fill this info

- Bruteforce SSH credentials

```
msf > use auxiliary/scanner/ssh/ssh_login

msf auxiliary(scanner/ssh/ssh_login) > options

msf auxiliary(scanner/ssh/ssh_login) > set
```

- Bruteforce SSH Public Keys

Note: Any file extension that ends with `.pub`

```
msf > use scanner/ssh/ssh_identify_pubkeys

msf auxiliary(scanner/ssh/ssh_identify_pubkeys) > options

Module options (auxiliary/scanner/ssh/ssh_identify_pubkeys):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   BRUTEFORCE_SPEED  5                yes       How fast to bruteforce, from 0 to 5
   DB_ALL_USERS      false            no        Add all users in the current database to the list
   DB_SKIP_EXISTING  none             no        Skip existing credentials stored in the current database (Accepted: none, user, user&realm)
   KEY_FILE                           yes       Filename of one or several cleartext public keys.
   RPORT             22               yes       The target port
   STOP_ON_SUCCESS   false            yes       Stop guessing when a credential works for a host
   THREADS           1                yes       The number of concurrent threads (max one per host)
   USERNAME                           no        A specific username to authenticate as
   USER_FILE                          no        File containing usernames, one per line
   VERBOSE           true             yes       Whether to print output for all attempts

msf auxiliary(scanner/ssh/ssh_identify_pubkeys) > set filename <ssh_public_key>

msf auxiliary(scanner/ssh/ssh_identify_pubkeys) > set threads 4

msf auxiliary(scanner/ssh/ssh_identify_pubkeys) > run -j
```

---
## References

- [Null Byte: Gain SSH Access to Servers by Brute-Forcing Credentials](https://null-byte.wonderhowto.com/how-to/gain-ssh-access-servers-by-brute-forcing-credentials-0194263/)