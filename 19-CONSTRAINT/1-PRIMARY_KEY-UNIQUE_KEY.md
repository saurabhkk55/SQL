# 1. `Primary Key Column`: 
Only one primary key column (or combination of columns) is allowed per table, and it must have unique and non-null values. It serves as the main identifier for each record in the table.

**Syntax**:
```sql
CREATE TABLE table_name (
    column1 datatype PRIMARY KEY,
    column2 datatype,
    ...
);
```

**Example**:
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(50),
    ...
);
```

# 2. `UNIQUE Column(s)`:
A table can have multiple columns with UNIQUE constraints, each ensuring that the values in that column (or combination of columns) are unique. These columns can contain NULL values, but only one NULL value is allowed per column (if the constraint is defined at the column level).

**Syntax**:
```sql
CREATE TABLE table_name (
    column1 datatype UNIQUE,
    column2 datatype,
    ...
);
```

**Example**:
```sql
CREATE TABLE students (
    student_id INT UNIQUE,
    student_name VARCHAR(50) UNIQUE,
    ...
);
```

In essence, while a table can have only one primary key, it can have multiple columns with UNIQUE constraints, providing flexibility in enforcing uniqueness across various columns within the table.

# `EXERCISE`:

### `Example: Creating a Table with Primary Key and UNIQUE Constraints`

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    email VARCHAR(100) UNIQUE,
    phone_number VARCHAR(15) UNIQUE
);
```

In this example:
- `student_id` is the primary key column, ensuring each student has a unique identifier.
- `email` and `phone_number` columns have UNIQUE constraints, ensuring that each email address and phone number is unique within the table.

### `Inserting Data`

Let's insert some sample data into the `students` table:

```sql
INSERT INTO students (student_id, student_name, email, phone_number) VALUES
(1, 'John Doe', 'john@example.com', '123-456-7890'),
(2, 'Jane Smith', 'jane@example.com', '234-567-8901'),
(3, 'Mike Johnson', 'mike@example.com', '345-678-9012');
```

### `Output`

After inserting the data, the `students` table would look like this:

```sql
+------------+--------------+-------------------+-----------------+
| student_id | student_name | email             | phone_number    |
+------------+--------------+-------------------+-----------------+
| 1          | John Doe     | john@example.com  | 123-456-7890    |
| 2          | Jane Smith   | jane@example.com  | 234-567-8901    |
| 3          | Mike Johnson | mike@example.com  | 345-678-9012    |
+------------+--------------+-------------------+-----------------+
```

### `Inserting Data with Violation`

Let's try to insert data that violates the UNIQUE constraints:

```sql
INSERT INTO students (student_id, student_name, email, phone_number) VALUES
(4, 'Tom Brown', 'john@example.com', '456-789-0123');
```

This will result in a MySQL `error` because the email address `'john@example.com'` is already present in the table and violates the UNIQUE constraint on the `email` column.

### `Conclusion`

In summary, the `students` table has one primary key column (`student_id`) and two columns (`email` and `phone_number`) with UNIQUE constraints. This ensures that each student has a unique identifier, and each email address and phone number within the table is unique.
