# 08 - Set Operations

`UNION` combines the result sets of two or more `SELECT` statements, removing duplicates.

```sql
SELECT column_name(s) FROM table1 UNION SELECT column_name(s) FROM table2;

SELECT City FROM Customers UNION SELECT City FROM Suppliers;
```

`UNION ALL` combines the result sets of two or more `SELECT` statements, including duplicates.

```sql
SELECT column_name(s) FROM table1 UNION ALL SELECT column_name(s) FROM table2;

SELECT City FROM Customers UNION ALL SELECT City FROM Suppliers;
```