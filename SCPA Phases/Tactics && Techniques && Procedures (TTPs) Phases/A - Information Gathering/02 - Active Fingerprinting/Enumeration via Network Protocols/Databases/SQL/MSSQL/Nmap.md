# Nmap

TODO: Re-arrange from this section to post exploitation under **Enumeration and Discovery**

## 01 - MSSQL Information

```
$ nmap -p 1433 -Pn --script ms-sql-info <IP>

$ nmap -p 1433 -Pn --script ms-sql-ntlm-info --script-args mssql.instance-port=1433 <IP>
```

## 02 - Dedicated Admin Connection

```
$ sudo nmap -p 1433 -Pn -sU --script ms-sql-dac <IP>
```

## 03 - Configuration

```
$ nmap -p 1443 -Pn --script ms-sql-config --script-args mssql.username=<username>,mssql.password=<password> <IP>
```

## 05 - Database

### 5.1 - Retrieve Relation

```
$ nmap -p 1433 -Pn --script ms-sql-tables --script mssql.username=<username>,password=<password> <IP>
```

### 5.2 - Database Access

```
$ nmap -p 1433 -Pn --script ms-sql-hasdbaccess --script-args mssql.username=<username>,mssql.password=<password> <IP>
```

## 06 - SQL Queries

### 6.1 - System Logins

```
$ nmap -p 1433 -Pn --script ms-sql-query --script-args mssql.username=<username>,mssql.password=<password>,ms-sql-query="SELECT * FROM master..syslogins" <IP>
```

## 07 - Hashdump

```
$ nmap -p 1433 -Pn --script ms-sql-dump-hashes --script-args mssql.username=<username>,mssql.password=<password> <IP>
```

## 08 - XP_Cmdshell

```
$ nmap -p 1433 -Pn --script ms-sql-xp-cmdshell --script-args mssql.username=<username>,mssql.password=<password>,ms-sql-xp-cmdshell="<commands>" <IP>
```

---
## References

- [SS64: SQLCMD](https://ss64.com/sql/sqlcmd.html)

- [Microsoft Documentation: Invoke-SQLCMD](https://learn.microsoft.com/en-us/powershell/module/sqlserver/invoke-sqlcmd?view=sqlserver-ps)

- [Hacktricks: Pentesting MSSQL Microsoft SQL Server](https://book.hacktricks.xyz/pentesting/pentesting-mssql-microsoft-sql-server)

- [Hacking Articles: MSSQL for Pentester Nmap](https://www.hackingarticles.in/mssql-for-pentesternmap/)