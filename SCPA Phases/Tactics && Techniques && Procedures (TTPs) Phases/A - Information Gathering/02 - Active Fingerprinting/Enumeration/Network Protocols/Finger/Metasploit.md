# Metasploit

```
msf > use auxiliary/scanner/finger/finger_users

msf auxiliary(scanner/finger/finger_users) > options

Module options (auxiliary/scanner/finger/finger_users):

   Name        Current Setting                                Required  Description 
   ----        ---------------                                --------  ----------- 
   RHOSTS                                                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit 
   RPORT       79                                             yes       The target port (TCP) 
   THREADS     1                                              yes       The number of concurrent threads (max one per host) 
   USERS_FILE  /opt/metasploit/data/wordlists/unix_users.txt  yes       The file that contains a list of default UNIX accounts.

msf auxiliary(scanner/finger/finger_users) > set rhosts <IP>

msf auxiliary(scanner/finger/finger_users) > run
```