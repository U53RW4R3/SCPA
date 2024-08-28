# MySQL

## 01 - Banner Grab

### 1.1 - Manual

```
$ nc -v <IP> 3306

$ telnet <IP> 3306
```

### 1.2 - Metasploit

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

## 02 - MySQL Information

```
$ nmap -p 3306 -sV --script mysql-info <IP>
```

## 03 - Authentication

```
$ mysql [-h <IP>] -u <username>

$ mysql [-h <IP>] -u <username> -p <password>
```