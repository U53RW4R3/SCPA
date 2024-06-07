# Manual

## 01 - Usage

### 1.1 - Authenticate

- Local

`$ mysql -u <username>`

`$ mysql -u <username> -p <password>`

- Remote

`$ mysql -h <IP> -u <username>`

`$ mysql -h <IP> -u <username>@<IP>`

`$ mysql -h <IP> -u <username> -p <password>`

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

### 1.2 - MySQL Version

- MySQL service version

`MySQL [(none)]> SELECT VERSION();`

### 1.3 - Operating System

- **Enumerate OS**

`MySQL [(none)]> SHOW VARIABLES LIKE "%version%";`

`MySQL [(none)]> SELECT LOAD_FILE('/etc/issue');`

`MySQL [(none)]> SELECT LOAD_FILE('/proc/self/environ');`

`MySQL [(none)]> SELECT LOAD_FILE('/proc/self/cmdline');`

`MySQL [(none)]> SELECT LOAD_FILE('/proc/self/arp');`

`MySQL [(none)]> SELECT LOAD_FILE('/etc/os-release');`

`MySQL [(none)]> SELECT LOAD_FILE('/proc/mounts');`

### 1.3 - Database

#### 1.3.1 - List databases

`MySQL [(none)]> SHOW DATABASES;`

#### 1.3.2 - Retrieve Tables

- Select Database

`MySQL [(none)]> USE <database>;`

- Show tables

`MySQL [database_name]> SHOW TABLES;`

- Enumerate field

`MySQL [database_name]> DESCRIBE <table_name>;`

- Display records from a table

`MySQL [database_name]> SELECT * FROM <table_name>;`

`MySQL [(none)]> SELECT @@datadir;`

`MySQL [(none)]> SHOW VARIABLES WHERE Variable_Name LIKE "%dir";`

#### 1.3.3 - Hashdump Credentials

- Method 1:

`MySQL [(none)]> SELECT user,authentication_string from mysql.user;`

`MySQL [(none)]> SELECT user,password from mysql.user;`

- Method 2:

`MySQL [(none)]> use mysql;`

`MySQL [(mysql)]> SELECT user,authentication_string from user;`

`MySQL [(mysql)]> SELECT user,password from user;`

### 1.4 - Enumerate Users

#### 1.4.1 - Discover users connected to the compromised MySQL database server

`MySQL [(none)]> SELECT USER();`

`MySQL [(none)]> SELECT LOAD_FILE('/etc/passwd');`

### 1.5 - Privilege Escalation

TODO: Finish the enumeration part for escalating to root/admin privileges

#### 1.5.1 - Discover what privileges does the user have access

`MySQL [(none)]> SHOW PRIVILEGES;`

`MySQL [(none)]> SHOW PRIVILEGES \G;`

These two are the most critical ways other than the basic query SQL commands just to get a reverse shell and escalate privileges for abusing the UDF MySQL feature. Look at the [[Tactics && Techniques && Procedures (TTPs) Phases/F - Post Exploitation/Shell Is The Beginning/03 - Privilege Escalation/Linux/Service Exploits/MySQL/Unix Shell|Service Exploits]] section.

```
*************************** <number>. row ***************************
Privilege: Execute
  Context: Functions,Procedures
  Comment: To execute stored routines
*************************** <number>. row ***************************
Privilege: File
  Context: File access on server
  Comment: To read and write files on the server

MySQL [(none)]> SELECT user,host FROM mysql.user;

MySQL [(none)]> SHOW GRANTS FOR <username>@<IP>;
```

### 2.4 - Database

#### 2.4.1 - Retrieve Users

`$ nmap -p 3306 --script mysql-users --script-args="mysqluser='<username>',mysqlpass='<password>'" <IP>`

#### 2.4.2 - Retrieve Databases

`$ nmap -p 3306 --script mysql-databases --script-args="mysqluser='<username>',mysqlpass='<password>'" <IP>`

#### 2.4.3 - Retrieve Variables

`$ nmap -p 3306 --script mysql-variables --script-args="mysqluser='<username>',mysqlpass='<password>'" <IP>`

#### 2.4.4 - Hashdump

`$ nmap -p 3306 --script mysql-dump-hashes --script-args "username='<username>',password='<password>'" <IP>`

---
## References

- [Hacktricks: Pentesting MySQL](https://book.hacktricks.xyz/pentesting/pentesting-mysql)

- [SQL Injection](https://www.websec.ca/kb/sql_injection)

- [MySQL Show Privileges Statement](https://www.tutorialspoint.com/mysql/mysql_show_privileges_statement.htm)

- [MySQL Show User Privileges](https://phoenixnap.com/kb/mysql-show-user-privileges)

- [How to Find The MySQL Data Directory From Command Line in Windows](https://stackoverflow.com/questions/17968287/how-to-find-the-mysql-data-directory-from-command-line-in-windows)

- [Hacking Articles: MySQL Penetration Testing Nmap](https://www.hackingarticles.in/mysql-penetration-testing-nmap/)

- [Hacking Articles: Penetration Testing on MySQL Port 3306](https://www.hackingarticles.in/penetration-testing-on-mysql-port-3306/)

- [Metasploit Unleashed: Admin MySQL Auxiliary Modules](https://www.offensive-security.com/metasploit-unleashed/admin-mysql-auxiliary-modules/)