# 07 - Joins

General example of a `JOIN`.

```sql
SELECT * FROM table1 JOIN table2 ON table1.column = table2.column;

SELECT * FROM Sales JOIN Customers ON Sales.CustomerID = Customers.CustomerID;
```

`INNER JOIN` selects records that have matching values in both tables.

```sql
SELECT column_name(s) FROM table1 INNER JOIN table2 ON table1.column_name = table2.column_name;

SELECT Sales.OrderID, Customers.CustomerName FROM Sales INNER JOIN Customers ON Sales.CustomerID = Customers.CustomerID;
```

`LEFT JOIN` returns all records from the left table and matched records from the right table.

```sql
SELECT column_name(s) FROM table1 LEFT JOIN table2 ON table1.column_name = table2.column_name;

SELECT Customers.CustomerName, Sales.OrderID FROM Customers LEFT JOIN Sales ON Customers.CustomerID = Sales.CustomerID;
```

`RIGHT JOIN` returns all records from the right table and matched records from the left table.

```sql
SELECT column_name(s) FROM table1 RIGHT JOIN table2 ON table1.column_name = table2.column_name;

SELECT Sales.OrderID, Employees.LastName FROM Sales RIGHT JOIN Employees ON Sales.EmployeeID = Employees.EmployeeID;
```

`CROSS JOIN` returns all records from both tables.

```sql
SELECT column_name(s) FROM table1 CROSS JOIN table2;

SELECT Customers.CustomerName, Products.ProductName FROM Customers CROSS JOIN Products;
```

`SELF JOIN` joins a table with itself.

```sql
SELECT column_name(s) FROM table1 AS T1, table1 AS T2 WHERE condition;

SELECT A.CustomerName AS Customer1, B.CustomerName AS Customer2, A.City FROM Customers A, Customers B WHERE A.CustomerID <> B.CustomerID AND A.City = B.City;
```