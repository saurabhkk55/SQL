# `ALTER TABLE`

- The SQL `ALTER TABLE` statement is used to modify the structure of an existing table. 
- This can include adding, removing, or renaming columns, as well as changing column data types and adding default values. 
- Below are some examples to illustrate these operations.

## 1. `Adding a Column`

When you add a new column, SQL by default will keep `NULL` values in the new column unless a default value is specified.

**Syntax:**

```sql
ALTER TABLE table_name ADD column_name data_type;
```

**Example:**

```sql
-- Original table
CREATE TABLE Employees (
    EmployeeID INT,
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);

-- Adding a new column 'Email' to the 'Employees' table
ALTER TABLE Employees ADD Email VARCHAR(100);

-- The 'Employees' table now has an 'Email' column with NULL values by default.
```

**Resulting Table:**

| EmployeeID | FirstName | LastName | Email |
|------------|-----------|----------|-------|
| 1          | John      | Doe      | NULL  |
| 2          | Jane      | Smith    | NULL  |

## 2. `Removing a Column`

To remove an existing column from a table.

**Syntax:**

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```

**Example:**

```sql
-- Removing the 'Email' column from the 'Employees' table
ALTER TABLE Employees DROP COLUMN Email;

-- The 'Employees' table no longer has the 'Email' column.
```

**Resulting Table:**

| EmployeeID | FirstName | LastName |
|------------|-----------|----------|
| 1          | John      | Doe      |
| 2          | Jane      | Smith    |

## 3. `Renaming a Column`

To rename an existing column in a table.

**Syntax (SQL Server, MySQL 8.0+):**

```sql
ALTER TABLE table_name RENAME COLUMN old_column_name TO new_column_name;
```

**Example:**

```sql
-- Renaming the 'LastName' column to 'Surname' in the 'Employees' table
ALTER TABLE Employees RENAME COLUMN LastName TO Surname;

-- The 'Employees' table now has 'Surname' instead of 'LastName'.
```

**Resulting Table:**

| EmployeeID | FirstName | Surname |
|------------|-----------|---------|
| 1          | John      | Doe     |
| 2          | Jane      | Smith   |

## 4. `Renaming a Table`

To rename an existing table.

**Syntax:**

```sql
ALTER TABLE old_table_name RENAME TO new_table_name;
```

**Example:**

```sql
-- Renaming the 'Employees' table to 'Staff'
ALTER TABLE Employees RENAME TO Staff;

-- The table is now named 'Staff'.
```

## 5. `Modifying a Column`

To change the data type of an existing column or to add a default value.

**Syntax:**

```sql
ALTER TABLE table_name MODIFY COLUMN column_name new_data_type [DEFAULT default_value];
```

**Example:**

```sql
-- Changing the data type of 'EmployeeID' from INT to BIGINT and adding a default value for 'FirstName'
ALTER TABLE Staff MODIFY COLUMN EmployeeID BIGINT;
ALTER TABLE Staff MODIFY COLUMN FirstName VARCHAR(50) DEFAULT 'Unknown';

-- The 'Staff' table now has 'EmployeeID' as BIGINT and 'FirstName' with a default value of 'Unknown'.
```

**Resulting Table:**

| EmployeeID | FirstName | Surname |
|------------|-----------|---------|
| 1          | John      | Doe     |
| 2          | Jane      | Smith   |
| (default)  | Unknown   |         |

## `Summary of SQL Operations`:

1. **Add a Column:**
    ```sql
    ALTER TABLE table_name ADD column_name data_type;
    ```
2. **Remove a Column:**
    ```sql
    ALTER TABLE table_name DROP COLUMN column_name;
    ```
3. **Rename a Column:**
    ```sql
    ALTER TABLE table_name RENAME COLUMN old_column_name TO new_column_name;
    ```
4. **Rename a Table:**
    ```sql
    ALTER TABLE old_table_name RENAME TO new_table_name;
    ```
5. **Modify a Column:**
    ```sql
    ALTER TABLE table_name MODIFY COLUMN column_name new_data_type [DEFAULT default_value];
    ```
