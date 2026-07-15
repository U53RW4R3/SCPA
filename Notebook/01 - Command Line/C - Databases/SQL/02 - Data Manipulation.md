# 02 - Data Manipulation

Creates a new table.

```sql
CREATE TABLE table_name(column_1 datatype, column_2 datatype, ...);

CREATE TABLE person(Person ID int, LastName varchar(255), FristName varchar(255), Address varchar (255) City varchar (255));
```

Inserts new records by specifying column names and values.

```sql
INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);

INSERT INTO table_name(column1, column2, column3,...) VALUES (value 1, value 2, value 3,....);
```

Inserts new records for all columns without specifying column names.

```sql
INSERT INTO table_name VALUES (value1, value2, ...);

INSERT INTO table_name VALUES (value1, value2, value ,....);
```

Modifies existing records.

```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;

UPDATE Sales SET contactName = "Alan", city = "Goa" WHERE customer ID = 1;
```

Updates multiple records.

```sql
UPDATE table_name SET column_name = value WHERE condition;

UPDATE sales SET Postal code = 00000 WHERE Country = "India";
```

Deletes existing records.

```sql
DELETE FROM table_name WHERE condition;

DELETE FROM sales WHERE customerName = "Bob";
```

Deletes all rows in a table without deleting the table structure.

```sql
DELETE FROM table_name;

DELETE FROM person;
```

Copies data from one table to another.

```sql
INSERT INTO target_table SELECT * FROM source_table WHERE condition;

INSERT INTO table_2 SELECT * FROM table_1 WHERE Condition;
```

Copies specific columns from one table to another.

```sql
INSERT INTO target_table (column_1, column_2, ...) SELECT column_1, column_2, ... FROM source_table WHERE condition;

INSERT INTO table2 (column_1, column_2, column_3, ...) SELECT column_1, column_2, column_3 , ... FROM table1 WHERE condition;
```