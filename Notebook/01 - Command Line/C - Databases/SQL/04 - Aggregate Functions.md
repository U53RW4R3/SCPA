# 04 - Aggregate Functions

Counts how many rows are in a particular column.

```sql
SELECT COUNT(*) FROM table_name;

SELECT COUNT(*) FROM Sales;
```

Counts rows in a specific column based on a condition.

```sql
SELECT COUNT(column_name) FROM table_name WHERE condition;

SELECT COUNT(sale_amount) FROM Sales WHERE Country = 'Canada';
```

Adds together all the values in a particular column.

```sql
SELECT SUM(column_name) FROM table_name WHERE condition;

SELECT SUM(sale_amount) FROM Sales WHERE year = 2020;
```

Returns the lowest value in a particular column.

```sql
SELECT MIN(column_name) FROM table_name WHERE condition;

SELECT MIN(sale_amount) FROM Sales WHERE Month = 'January';
```

Returns the highest value in a particular column.

```sql
SELECT MAX(column_name) FROM table_name WHERE condition;

SELECT MAX(sale_amount) FROM Sales WHERE year = 2021;
```

Calculates the average of a group of selected values.

```sql
SELECT AVG(column_name) FROM table_name WHERE condition;

SELECT AVG(sale_amount) FROM Sales WHERE year = 2020;
```

Counts distinct values within an aggregation.

```sql
SELECT COUNT(DISTINCT column_name) FROM table_name;

SELECT COUNT(DISTINCT month) AS Unique_months FROM Sales;
```