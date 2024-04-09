# Metasploit

```
msf > use auxiliary/scanner/winrm/winrm_login

msf auxiliary(scanner/winrm/winrm_login) > options

Module options (auxiliary/scanner/winrm/winrm_login):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   BLANK_PASSWORDS   false            no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                yes       How fast to bruteforce, from 0 to 5
   DB_ALL_CREDS      false            no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false            no        Add all passwords in the current database to the list
   DB_ALL_USERS      false            no        Add all users in the current database to the list
   DB_SKIP_EXISTING  none             no        Skip existing credentials stored in the current database (Accepted: none, user, user&realm)
   DOMAIN            WORKSTATION      yes       The domain to use for Windows authentification
   PASSWORD                           no        A specific password to authenticate with
   PASS_FILE                          no        File containing passwords, one per line
   Proxies                            no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                             yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT             5985             yes       The target port (TCP)
   SSL               false            no        Negotiate SSL/TLS for outgoing connections
   STOP_ON_SUCCESS   false            yes       Stop guessing when a credential works for a host
   THREADS           1                yes       The number of concurrent threads (max one per host)
   URI               /wsman           yes       The URI of the WinRM service
   USERNAME                           no        A specific username to authenticate as
   USERPASS_FILE                      no        File containing users and passwords separated by space, one pair per line
   USER_AS_PASS      false            no        Try the username as the password for all users
   USER_FILE                          no        File containing usernames, one per line
   VERBOSE           true             yes       Whether to print output for all attempts
   VHOST                              no        HTTP server virtual host

msf auxiliary(scanner/winrm/winrm_login) > set rhosts <IP>

msf auxiliary(scanner/winrm/winrm_login) > set domain <domain_name>

msf auxiliary(scanner/winrm/winrm_login) > set threads 4

msf auxiliary(scanner/winrm/winrm_login) > set username <username>

msf auxiliary(scanner/winrm/winrm_login) > set password <password>

msf auxiliary(scanner/winrm/winrm_login) > run -j
```