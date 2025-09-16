# 06 - Conditional Logic

Syntax for `CASE` statement.

```sql
CASE WHEN Condition1 THEN Result1 WHEN Condition2 THEN Result2 WHEN Condition N THEN ResultN ELSE Result END;

CASE WHEN Condition1 THEN Result1 WHEN Condition2 THEN Result2 WHEN Condition N THEN ResultN ELSE Result END;
```

Example of `CASE` statement for conditional logic.

```sql
SELECT column_1, CASE WHEN condition1 THEN 'Result 1' WHEN condition2 THEN 'Result 2' ELSE 'Default Result' END AS new_column FROM table_name;

SELECT OrderID CASE WHEN Quantity > 30 THEN 'the quantity is greater' WHEN quantity = 30 THEN 'the quantity equal to 30' ELSE 'The quantity is under 20' END AS Quantity Text FROM Sales s;
```