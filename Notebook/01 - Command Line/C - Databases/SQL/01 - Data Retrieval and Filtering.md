# 01 - Data Retrieval and Filtering

Selects all columns from the table.

```sql
SELECT * FROM table_name;

SELECT * FROM Sales;
```

Selects specific columns.

```sql
SELECT column_1, column_2, column_n FROM table_name;

SELECT year, month, west FROM Sales;
```

Renames a column using an alias.

```sql
SELECT column_name AS alias_name FROM table_name;

SELECT west AS "west Region" FROM Sales;
```

Limits the number of records returned.

```sql
SELECT * FROM table_name LIMIT number;

SELECT * FROM Sales LIMIT 100;
```

Filters records based on a specified condition.

```sql
SELECT * FROM table_name WHERE column_name = 'value';

SELECT * FROM sales WHERE Country = "Canada";
```

Filters using "equal to" comparison operator.

```sql
SELECT * FROM table_name WHERE column_name = 'value';

SELECT * FROM Sales WHERE city = "kolkata";
```

Filters using "not equal to" comparison operator.

```sql
SELECT * FROM table_name WHERE column_name != 'value';

SELECT * FROM Sales WHERE city != "kolkata";
```

Filters using "greater than" comparison operator.

```sql
SELECT * FROM table_name WHERE column_name > 'value';

SELECT * FROM Sales WHERE Month > "January";
```

Filters using "less than" comparison operator.

```sql
SELECT * FROM table_name WHERE column_name < value;

SELECT * FROM Sales WHERE sale_amount < 50000;
```

Tests for NULL values.

```sql
SELECT column_name(s) FROM table_name WHERE column_name IS NULL;

SELECT customer, contact, address FROM Sales WHERE address IS NULL;
```

Tests for NOT NULL values.

```sql
SELECT column_name(s) FROM table_name WHERE column_name IS NOT NULL;

SELECT customer, contact, address FROM Sales WHERE address IS NOT NULL;
```

Matches similar values using `LIKE`.

```sql
SELECT * FROM table_name WHERE column_name LIKE 'pattern%';

SELECT * FROM Sales WHERE "group" LIKE "New%';
```

Specifies a list of values to include using `IN`.

```sql
SELECT * FROM table_name WHERE column_name IN ('value1', 'value2');

SELECT * FROM Songs WHERE artist IN ('Taylor swift', 'Usher');
```

Selects rows within a certain range using `BETWEEN`.

```sql
SELECT * FROM table_name WHERE column_name BETWEEN value1 AND value2;

SELECT * FROM Songs WHERE year_rank BETWEEN 5 AND 10;
```

Combines conditions using `AND`.

```sql
SELECT * FROM table_name WHERE condition1 AND condition2;

SELECT * FROM Songs WHERE year = 2012 AND year_rank <= 10;
```

Combines conditions using `OR`.

```sql
SELECT * FROM table_name WHERE condition1 OR condition2;

SELECT * FROM Songs WHERE year_rank = 5 OR artist = "Sonu";
```

Selects rows that do not match a certain condition using `NOT`.

```sql
SELECT * FROM table_name WHERE NOT condition;

SELECT * FROM Sales WHERE NOT country = "Japan";
```

Combines `AND`, `OR`, and `NOT` operators.

```sql
SELECT * FROM table_name WHERE condition1 AND (condition2 OR condition3);

SELECT * FROM Sales WHERE Country = 'Japan' AND (City = 'Goa' OR City = 'Puri');
```

Selects only unique values from a particular column.

```sql
SELECT DISTINCT column_name FROM table_name;

SELECT DISTINCT month FROM Sales;
```

Selects unique combinations of values from multiple columns.

```sql
SELECT DISTINCT column_1, column_2 FROM table_name;

SELECT DISTINCT year, month FROM Sales;
```

Uses the `IN` operator for multiple values.

```sql
SELECT * FROM table_name WHERE column_name IN ('value_1', 'value_2', 'value_3');

SELECT * FROM Sales WHERE country IN ('India', 'Nepal', 'UK');
```

Uses the `NOT IN` operator.

```sql
SELECT * FROM table_name WHERE column_name NOT IN ('value_1', 'value_2', 'value_3');

SELECT * FROM Sales WHERE country NOT IN ('India', 'Nepal', 'UK');
```

Uses the `IN` operator with a subquery.

```sql
SELECT * FROM table_name WHERE column_name IN (SELECT column_name FROM other_table);

SELECT * FROM Sales WHERE country IN (SELECT country FROM Suppliers);
```

Tests for the existence of any record in a subquery using `EXISTS`.

```sql
SELECT column_name(s) FROM table_name WHERE EXISTS (SELECT column_name FROM other_table WHERE condition);

SELECT column_name (s) FROM table-name WHERE EXISTS (SELECT column_name FROM table_name WHERE condition);
```

Performs comparison with any value in a range using `ANY`.

```sql
SELECT column_name FROM table_name WHERE column_id = ANY (SELECT column_id FROM other_table WHERE condition);

SELECT ProductName FROM Sales WHERE ProductID = ANY (SELECT ProductID FROM OrderDetails WHERE Quantity > 99);
```

Example using `ALL`.

```sql
SELECT ALL column_name FROM table_name WHERE condition;

SELECT ALL ProductName FROM Sales WHERE TRUE;
```

Returns an alternative value if an expression is `NULL` using `IFNULL()`.

```sql
SELECT column_name, IFNULL (column_with_null, alternative_value) AS alias_name FROM contacts;

SELECT Contactname, IFNULL (bizphone, homephone) AS phone FROM contacts;
```

Another example of `IFNULL()`.

```sql
SELECT column_name, IFNULL (column_with_null, alternative_value) AS alias_name FROM employee;

SELECT name, IFNULL (Officephone , mobilephone) AS contact FROM employee;
```