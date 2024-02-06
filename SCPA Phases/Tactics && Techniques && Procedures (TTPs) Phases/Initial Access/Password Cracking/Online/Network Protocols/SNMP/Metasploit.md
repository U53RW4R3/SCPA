# Metasploit

```
msf > use auxiliary/scanner/snmp/snmp_login

msf auxiliary(scanner/snmp/snmp_login) > options

Module options (auxiliary/scanner/snmp/snmp_login): 

   Name              Current Setting                                       Required  Description 
   ----              ---------------                                       --------  ----------- 
   BLANK_PASSWORDS   false                                                 no        Try blank passwords for all users 
   BRUTEFORCE_SPEED  5                                                     yes       How fast to bruteforce, from 0 to 5 
   DB_ALL_CREDS      false                                                 no        Try each user/password couple stored in the current database 
   DB_ALL_PASS       false                                                 no        Add all passwords in the current database to the list 
   DB_ALL_USERS      false                                                 no        Add all users in the current database to the list 
   DB_SKIP_EXISTING  none                                                  no        Skip existing credentials stored in the current database (Accepted: none, user, user&realm) 
   PASSWORD                                                                no        The password to test 
   PASS_FILE         /opt/metasploit/data/wordlists/snmp_default_pass.txt  no        File containing communities, one per line 
   RHOSTS                                                                  yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit 
   RPORT             161                                                   yes       The target port 
   STOP_ON_SUCCESS   false                                                 yes       Stop guessing when a credential works for a host 
   THREADS           1                                                     yes       The number of concurrent threads (max one per host) 
   USER_AS_PASS      false                                                 no        Try the username as the password for all users 
   VERBOSE           true                                                  yes       Whether to print output for all attempts 
   VERSION           1                                                     yes       The SNMP version to scan (Accepted: 1, 2c, all)

msf auxiliary(scanner/snmp/snmp_login) > set rhosts <IP>

msf auxiliary(scanner/snmp/snmp_login) > set pass_file passwords.lst

msf auxiliary(scanner/snmp/snmp_login) > set stop_on_success true

msf auxiliary(scanner/snmp/snmp_login) > run -j

msf auxiliary(scanner/snmp/snmp_login) > creds
```