# 03 - Arithmetic Operations

Performs addition across columns in the same row.

```sql
SELECT column1, column2, column1 + column2 AS new_column FROM table_name;

SELECT year, month, west, South, west + south AS south_plus_west FROM sales;
```

Performs multiple arithmetic operations.

```sql
SELECT column1, column2, column1 + column2 - value * column3 AS new_column FROM table_name;

SELECT year, month, west, South, west + south - 4 * year AS south_plus_west FROM sales;
```

Performs division with parentheses.

```sql
SELECT column1, column2, (column1 + column2) / value AS new_column FROM table_name;

SELECT year, month, west, South, (west + south) / 2 AS south_west_avg FROM sales;
```