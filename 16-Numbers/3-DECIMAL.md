# `DECIMAL`

The `DECIMAL` data type in MySQL is used to store exact numeric values, where precision (total number of digits) and scale (number of digits after the decimal point) can be specified. It is commonly used for monetary values or other precise numeric data that requires exact representation.

**Size**: Based on how many total digits (precision) you choose.

### Syntax

```sql
DECIMAL(precision, scale)
```

- `precision`: Total number of digits (both to the left and right of the decimal point). This includes both the significant digits and the digits after the decimal point.
- `scale`: Number of digits after the decimal point.

### Example

Create a table with a `DECIMAL` column:

```sql
CREATE TABLE my_table (
    id INT AUTO_INCREMENT PRIMARY KEY,
    value DECIMAL(5, 2)
);
```

Describe the table structure:

```sql
DESC my_table;
```

This will show the table structure including the `value` column defined as `DECIMAL(5, 2)`:

```sql
+-------+--------------+------+-----+---------+----------------+
| Field | Type         | Null | Key | Default | Extra          |
+-------+--------------+------+-----+---------+----------------+
| id    | int          | NO   | PRI | NULL    | auto_increment |
| value | decimal(5,2) | YES  |     | NULL    |                |
+-------+--------------+------+-----+---------+----------------+
```

Inserting values into the `my_table`:

```sql
INSERT INTO my_table (value) VALUES (123.45);
INSERT INTO my_table (value) VALUES (123.4);
INSERT INTO my_table (value) VALUES (123);
INSERT INTO my_table (value) VALUES (12.345); -- will be store as 12.35
INSERT INTO my_table (value) VALUES (1.2345); -- will be store as 1.23
INSERT INTO my_table (value) VALUES (.12345); -- will be store as 0.12
INSERT INTO my_table (value) VALUES (.1);     -- will be store as 0.10
```

Attempting to insert values that exceed the defined precision or scale will result in errors:

```sql
INSERT INTO my_table (value) VALUES (1234.4);   -- Error: Out of range value
INSERT INTO my_table (value) VALUES (1234.456); -- Error: Out of range value
INSERT INTO my_table (value) VALUES (12345);    -- Error: Out of range value
```

The successful inserts will result in the following table data:

```sql
SELECT * FROM my_table;

+----+--------+
| id | value  |
+----+--------+
|  1 | 123.45 |
|  2 | 123.40 |
|  3 | 123.00 |
|  4 | 12.35  |
|  5 | 1.23   |
|  6 | 0.12   |
|  7 | 0.10   |
+----+--------+
```
