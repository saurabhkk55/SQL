# `Tables`

## `What is a Table?`
A table is a collection of related data stored in a structured format within a database.

### `Creating a New Table`
Before creating a table, ensure you're working within your desired database using `USE <db_name>`.

To create a new table:
```sql
CREATE TABLE <table_name> (
    id INT,
    name VARCHAR(100)
);
```
Or with different columns:
```sql
CREATE TABLE <table_name> (
    name VARCHAR(100),
    age INT
);
```

### `Verifying Table Structure`
To view the structure of a table:
```sql
DESC <table_name>;
```
`DESC` stands for Describe.

### `Tips`
- **`Database Switching`**: Always switch to the correct database (`USE <db_name>`) before creating or interacting with tables.
- **`Table Structure`**: Plan the structure of your tables (column names, data types) before creating them.
- **`Verification`**: Use `SHOW DATABASES;` and `DESC <table_name>;` to verify database and table status.
- **`Data Types`**: Choose appropriate data types (e.g., `INT`, `VARCHAR`, `DATE`) for columns based on the type of data you need to store.


### `Inserting Data into a Table`

#### Inserting Single Data
To insert a single row of data into a table:
```sql
INSERT INTO <table_name> (id, name)
VALUES (101, "Rahul");
```
Alternatively, if you're inserting values in the same order as the table columns, you can omit specifying column names:
```sql
INSERT INTO <table_name>
VALUES (101, "Rahul");
```
**Note:** It's essential that `<table_name>` already exists before inserting data.

### `Inserting Multiple Data`
To insert multiple rows of data into a table:
```sql
INSERT INTO <table_name> (id, name)
VALUES (103, "Raju"), (104, "Sham");
```

### `Reading Data from a Table`

#### Reading Entire Table
To retrieve all data from a table:
```sql
SELECT * FROM <table_name>;
```
This query will return all columns and rows from `<table_name>`.

#### Reading Specific Columns
To retrieve data from specific columns of a table:
```sql
SELECT <column_name> FROM <table_name>;
```
Replace `<column_name>` with the name of the column you want to retrieve.

#### Reading Multiple Columns
To retrieve data from multiple columns of a table:
```sql
SELECT <column_1_name>, <column_2_name> FROM <table_name>;
```
Specify the names of the columns you want to retrieve separated by commas.

### `Tips`

- **`Column Order`**: When inserting data, if you're specifying column names, ensure the order matches the sequence in the `INSERT INTO` statement.
- **`Data Integrity`**: Verify the data types and constraints (if any) of the columns to ensure compatibility during data insertion.
- **`Reading Data`**: Use `SELECT` queries to retrieve specific information from tables, either entire rows (`*` for all columns) or specific columns.

### `Example Usage`

```sql
-- Inserting a single row
INSERT INTO students (id, name) VALUES (101, "Rahul");

-- Inserting multiple rows
INSERT INTO students (id, name) VALUES (103, "Raju"), (104, "Sham");

-- Reading all data from the students table
SELECT * FROM students;

-- Reading only the names of students
SELECT name FROM students;

-- Reading ID and name of students
SELECT id, name FROM students;
```

---

### `Printing Data Based on Conditions`

#### Printing Entire Data Based on a Condition
To retrieve all data from a table where a specific condition is met (e.g., `id = 103`):
```sql
SELECT * FROM <table_name> WHERE id = 103;
```
This query will return all columns (`*`) for rows where the `id` column equals `103`.

### `Modifying Data in a Table`

#### Modifying/Updating Data
To update existing data in a table:
```sql
UPDATE <table_name>
SET contact = 9789456512
WHERE id = 103;
```
This query updates the `contact` column to `9789456512` for the row where `id` equals `103`.

**Tip:** Use a unique key (e.g., primary key) in the `WHERE` clause to ensure you're updating the correct row.

### `Deleting Data from a Table`

#### Deleting Specific Data
To delete data from a table based on a condition:
```sql
DELETE FROM students
WHERE id = 103;
```
This query deletes the row where `id` equals `103` from the `students` table.

**Tip:** Always use a unique key in the `WHERE` clause to target specific rows for deletion.

### `Dropping a Table`

#### Dropping (Deleting) an Entire Table
To delete an entire table (including all its data):
```sql
DROP TABLE <table_name>;
```
**Caution:** Dropping a table is a permanent action and cannot be undone. Ensure you have a backup or confirm your intention before executing this command.

### `Tips`

- **`Data Conditions`**: Use the `WHERE` clause to filter data based on specific conditions when selecting, updating, or deleting rows.
- **`Unique Keys`**: Utilize unique keys (like primary keys) in `WHERE` clauses to pinpoint the exact rows you want to modify or delete.
- **`Safety Measures`**: Double-check the conditions and verify the impact (especially with `DELETE` and `DROP TABLE` operations) before executing SQL commands.

### `Example Usage`

```sql
-- Printing data based on a condition
SELECT * FROM students WHERE id = 103;

-- Modifying contact number for a specific student
UPDATE students SET contact = 9789456512 WHERE id = 103;

-- Deleting a student record
DELETE FROM students WHERE id = 103;

-- Dropping (deleting) the entire students table
DROP TABLE students;
```
