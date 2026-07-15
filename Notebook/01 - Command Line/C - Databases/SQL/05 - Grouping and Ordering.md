# 05 - Grouping and Ordering

Groups data by a single column.

```sql
SELECT column_name COUNT(*) FROM table_name GROUP BY column_name;

SELECT year COUNT(*) FROM Sales GROUP BY year;
```

Groups data by multiple columns.

```sql
SELECT column_1, column_2, COUNT(*) FROM table_name GROUP BY column_1, column_2;

SELECT year, month, COUNT(*) FROM Sales GROUP BY year, month;
```

Groups data by column numbers.

```sql
SELECT column_1, column_2, COUNT(*) FROM table_name GROUP By 1, 2;

SELECT year, month, COUNT(*) FROM Sales GROUP By 1, 2;
```

Combines `GROUP BY` with `ORDER BY`.

```sql
SELECT column_1, column_2, COUNT(*) FROM table_name GROUP BY column_1, column_2 ORDER BY column_1, column_2;

SELECT year, month, COUNT(*) FROM Sales GROUP BY year, month ORDER BY month, year;
```

Combines `GROUP BY` with `LIMIT`.

```sql
SELECT column_name FROM table_name WHERE condition GROUP BY column_name LIMIT number;

SELECT year FROM Sales WHERE west > 10000 GROUP BY year LIMIT 1;
```

Filters grouped data using `HAVING`.

```sql
SELECT column_name(s) FROM table_name WHERE condition GROUP BY column_name(s) HAVING condition ORDER BY column_name(s);

SELECT Country, COUNT(*) FROM Sales GROUP BY Country HAVING COUNT(*) > 5;
```

Example of `HAVING` clause.

```sql
SELECT column_1, MAX(column_2) FROM table_name GROUP BY column_1 HAVING MAX(column_2) > value ORDER BY column_1;

SELECT year, month, MAX(sale_amount) AS month_high FROM Sales GROUP BY year, month HAVING MAX(sale_amount) > 400000 ORDER BY year, month;
```

Orders results by one or more columns.

```sql
SELECT * FROM table_name ORDER By column_1, column_2;

SELECT * FROM Sales ORDER BY Country, CustomerName;
```

Orders results in ascending and descending order.

```sql
SELECT * FROM table_name ORDER By column_1 ASC, column_2 DESC;

SELECT * FROM Sales ORDER BY Country ASC, CustomerName DESC;
```