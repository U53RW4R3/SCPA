# Metasploit

```
msf > use auxiliary/scanner/postgres/postgres_login

msf auxiliary(scanner/postgres/postgres_login) > options

Module options (auxiliary/scanner/postgres/postgres_login):

   Name              Current Setting                                                               Required  Description
   ----              ---------------                                                               --------  -----------
   BLANK_PASSWORDS   false                                                                         no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                                                                             yes       How fast to bruteforce, from 0 to 5
   DATABASE          template1                                                                     yes       The database to authenticate against
   DB_ALL_CREDS      false                                                                         no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false                                                                         no        Add all passwords in the current database to the list
   DB_ALL_USERS      false                                                                         no        Add all users in the current database to the list
   DB_SKIP_EXISTING  none                                                                          no        Skip existing credentials stored in the current database (Accepted: none, user, user&realm)
   PASSWORD                                                                                        no        A specific password to authenticate with
   PASS_FILE         /usr/share/metasploit-framework/data/wordlists/postgres_default_pass.txt      no        File containing passwords, one per line
   Proxies                                                                                         no        A proxy chain of format type:host:port[,type:host:port][...]
   RETURN_ROWSET     true                                                                          no        Set to true to see query result sets
   RHOSTS                                                                                          yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT             5432                                                                          yes       The target port
   STOP_ON_SUCCESS   false                                                                         yes       Stop guessing when a credential works for a host
   THREADS           1                                                                             yes       The number of concurrent threads (max one per host)
   USERNAME                                                                                        no        A specific username to authenticate as
   USERPASS_FILE     /usr/share/metasploit-framework/data/wordlists/postgres_default_userpass.txt  no        File containing (space-separated) users and passwords, one pair per line
   USER_AS_PASS      false                                                                         no        Try the username as the password for all users
   USER_FILE         /usr/share/metasploit-framework/data/wordlists/postgres_default_user.txt      no        File containing users, one per line
   VERBOSE           true                                                                          yes       Whether to print output for all attempts

msf auxiliary(scanner/postgres/postgres_login) > set rhosts <IP>

msf auxiliary(scanner/postgres/postgres_login) > set database <database>

msf auxiliary(scanner/postgres/postgres_login) > set user_file /path/to/users.lst

msf auxiliary(scanner/postgres/postgres_login) > set pass_file /path/to/passwords.lst

msf auxiliary(scanner/postgres/postgres_login) > set bruteforce_speed [0-5]

msf auxiliary(scanner/postgres/postgres_login) > run -j
```