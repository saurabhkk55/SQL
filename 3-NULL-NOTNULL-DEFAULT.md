# `NULL`

In SQL databases, columns generally allow `NULL` values by default unless you explicitly define them as `NOT NULL`. This default behavior means that when you create a table and specify column definitions without specifying `NOT NULL`, those columns will accept `NULL` values.

### Default Behavior of Columns:

- **NULL Values Allowed**: When you create a table without specifying `NOT NULL` for a column, that column will allow `NULL` values.
  
- **Flexibility in Data Entry**: Allowing `NULL` values provides flexibility during data entry. It allows for scenarios where certain information might not be known or applicable.

- **Implicit Default**: If a column is not explicitly defined as `NOT NULL`, the database assumes that `NULL` is an acceptable value for that column.

### `Example`:

Let's illustrate how `NULL` values can be inserted into a table in SQL.

### Example: Inserting NULL Values into a Table

Suppose we have a table named `employees` with columns that allow `NULL` values (`emp_name` and `hire_date`), and we want to insert rows containing `NULL` values for these columns.

#### Table Definition:
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    hire_date DATE
);
```

#### Inserting Rows with NULL Values:
```sql
-- Inserting a row with NULL emp_name and hire_date
INSERT INTO employees (emp_id, emp_name, hire_date)
VALUES (1, NULL, '2023-01-15');

-- Inserting a row with NULL emp_name
INSERT INTO employees (emp_id, emp_name, hire_date)
VALUES (2, NULL, NULL);

-- Inserting a row with NULL hire_date
INSERT INTO employees (emp_id, emp_name, hire_date)
VALUES (3, 'John Doe', NULL);
```

In these examples:
- We're inserting rows into the `employees` table.
- The first row inserts a `NULL` value for `emp_name` and a specific date for `hire_date`.
- The second row inserts `NULL` values for both `emp_name` and `hire_date`.
- The third row inserts a specific `emp_name` but leaves `hire_date` as `NULL`.

### Querying Data to Verify NULL Values:

You can query the `employees` table to verify the inserted `NULL` values:

```sql
-- Retrieve all data from the employees table
SELECT * FROM employees;
```

This query will display the contents of the `employees` table, including rows with `NULL` values for columns where `NULL` is allowed (`emp_name` and `hire_date`).

### `Result`:
```
+--------+----------+------------+
| emp_id | emp_name | hire_date  |
+--------+----------+------------+
|   1    | NULL     | 2023-01-15 |
|   2    | NULL     | NULL       |
|   3    | John Doe | NULL       |
+--------+----------+------------+
```

In this result:
- Row 1 has `NULL` for `emp_name` and a specific date for `hire_date`.
- Row 2 has `NULL` for both `emp_name` and `hire_date`.
- Row 3 has a specific value (`John Doe`) for `emp_name` and `NULL` for `hire_date`.

This example demonstrates how `NULL` values can be inserted into a table for columns that allow `NULL`, providing flexibility in data entry when certain information is not available or applicable.

By leveraging `NULL` values appropriately, you can handle missing or unknown data within your database tables while maintaining data integrity and consistency according to your application's requirements.

# `Explicitly Specifying NOT NULL`:

If you want to enforce the requirement that certain columns must always have a value (i.e., not allow `NULL`), you can explicitly specify `NOT NULL` for those columns during table creation.

```sql
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100),
    birth_date DATE NOT NULL
);
```

In this `customers` table:
- `first_name`, `last_name`, and `birth_date` columns must have non-`NULL` values.
- The `email` column allows `NULL` values because it's not specified as `NOT NULL`.

### `Reasons for Using NOT NULL`:

- **Data Integrity**: Ensures that critical information is always provided and not left blank.
  
- **Query Performance**: Columns defined as `NOT NULL` can be indexed more efficiently for faster query performance.

- **Clarity in Data Requirements**: Clearly communicates data requirements to developers and database users.

By understanding the default behavior of columns in SQL databases and leveraging `NOT NULL` constraints where necessary, we can design database schemas that maintain data integrity and support your application's requirements effectively.


# `Default value`
We can specify a default value for a column in a table, which means if a new row is inserted and that column's value is not provided explicitly, the default value will be used instead. This is useful for ensuring consistency and handling cases where certain data might not be provided during insertion.

Here's an example of how to set a default value for a column in an SQL table:

Let's create a simple table named `employees` with some columns including `name`, `age`, and `department`. We'll set a default value for the `department` column to be 'Unknown' if no value is specified during insertion.

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    age INT NOT NULL,
    department VARCHAR(50) NOT NULL DEFAULT 'Unknown'
);
```

In this SQL statement:
- `id INT PRIMARY KEY AUTO_INCREMENT` specifies an integer primary key which auto-increments.
- `name VARCHAR(50) NOT NULL` specifies a required `name` column with a maximum length of 50 characters.
- `age INT` specifies an optional `age` column (can be `NULL`).
- `department VARCHAR(50) DEFAULT 'Unknown'` specifies the `department` column with a default value of `'Unknown'` if not specified during insertion.

Now let's insert some rows into this `employees` table:

```sql
-- Inserting a row without specifying department
INSERT INTO employees (name, age) VALUES ('John Doe', 30);

-- Inserting a row with a specified department
INSERT INTO employees (name, age, department) VALUES ('Jane Smith', 25, 'Marketing');
```

After these insertions, the data in the `employees` table would look like this:
```
| id | name       | age | department |
|----|------------|-----|------------|
| 1  | John Doe   | 30  | Unknown    |
| 2  | Jane Smith | 25  | Marketing  |
```

In the first `INSERT` statement, since the `department` column was not specified, the default value `'Unknown'` was used. In the second `INSERT` statement, we explicitly specified the `department` value as `'Marketing'`, so that value was used instead.

Setting default values can help maintain data integrity and simplify data insertion processes, especially when certain columns have common default values across most records.