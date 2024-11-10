# Manual

## 01 - Setup

> [!NOTE]
> The enumeration process is the same thing when using Windows own native program called `sqlcmd` or `osql` which is why `sqsh` on Linux uses the same syntax.

### 1.1 - Package Manager

Install `sqsh` according to your package manager.

```
$ sudo apt install -y sqsh

$ yay -S --noconfirm sqsh
```

## 02 - Usage

Usage of the program.

```
$ sqsh -S <IP> -D <database> -U [<domain>\]<username> -P <password>

$ sqsh -S <IP> -D <database> -U [<domain\]<username -P 00000000000000000000000000000000:<nt_hash>
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