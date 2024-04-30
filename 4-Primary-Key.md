# `Primary Keys`
- Primary key is a special column or a combination of columns that uniquely identifies each row (record) in a table. 
- The primary key constraint ensures that the values in this column (or columns) are `unique` and `not null`, meaning no two rows can have the same primary key value
- Primary keys are automatically indexed for quick data retrieval.

## 1. `Example of Creating a Table with a Primary Key`:
Let's create a simple table named `students` with a primary key `student_id`:

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT
);
```

In this SQL statement:
- `student_id INT PRIMARY KEY` specifies that `student_id` is the primary key column of type integer.
- `first_name VARCHAR(50)` and `last_name VARCHAR(50)` are columns to store the student's first name and last name, respectively.
- `age INT` is a column to store the student's age.

# 2. `Insert a duplicate primary key value into a table`:
In SQL, it is not possible to directly insert a duplicate primary key value into a table. The primary key constraint ensures that each value in the primary key column (or columns) must be unique. Attempting to insert a duplicate primary key value will result in an error and the insertion will fail.

However, I can demonstrate how you might encounter an error when trying to insert a duplicate primary key value. Let's assume we have a table named `students` with a `student_id` column as the primary key:

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT
);
```

Now, let's try to insert two rows where both rows have the same `student_id` value:

```sql
-- Attempt to insert a duplicate primary key value
INSERT INTO students (student_id, first_name, last_name, age) VALUES (1, 'John', 'Doe', 20);
INSERT INTO students (student_id, first_name, last_name, age) VALUES (1, 'Jane', 'Smith', 22);
```

### `Resulting Error`:
When you attempt to execute the above SQL statements, the second `INSERT` statement will fail with an error similar to the following:

- **MySQL Error**:
  ```
  Error Code: 1062. Duplicate entry '1' for key 'PRIMARY'
  ```

### `Explanation`:
The error occurs because the database detects a violation of the primary key constraint. The `student_id` value `1` is already present in the table from the first `INSERT` statement, and therefore, inserting another row with the same `student_id` violates the uniqueness requirement of the primary key.

## 3. `Inserting Data Without Specifying Primary Key`:
If you attempt to insert data into a table that has a primary key column but you do not specify a value for the primary key column, the database operation will result in an error or warning, depending on the database system and its configuration.

Let's consider a scenario where we have a table `students` with a primary key column `student_id`. Here's what might happen:

```sql
-- Create students table with a primary key
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT
);

-- Attempt to insert data without specifying student_id
INSERT INTO students (first_name, last_name, age) VALUES ('John', 'Doe', 20);
```

**`ERROR`**: 
when you attempt to execute the INSERT statement without specifying a value for the student_id column, the operation will result in an error. This is because the student_id column is defined as a primary key and is not set to allow NULL values (NOT NULL constraint).

## 4. `Inserting Data into the Table`:
Now, let's insert some data into the `students` table:

```sql
-- Inserting data into the students table
INSERT INTO students (student_id, first_name, last_name, age) VALUES (1, 'John', 'Doe', 20);
INSERT INTO students (student_id, first_name, last_name, age) VALUES (2, 'Jane', 'Smith', 22);
```

## 5. `Querying Data Using the Primary Key`:
We can use the primary key `student_id` to retrieve specific rows from the `students` table:

```sql
-- Retrieve a student record based on the primary key
SELECT * FROM students WHERE student_id = 1;
```

## 6. `Updating Data Using the Primary Key`:
The primary key can also be used to update specific rows:

```sql
-- Update a student's age based on the primary key
UPDATE students SET age = 21 WHERE student_id = 1;
```

## 7. `Deleting Data Using the Primary Key`:
The primary key can be used to delete specific rows:

```sql
-- Delete a student record based on the primary key
DELETE FROM students WHERE student_id = 2;
```

## 8. `Composite Primary Key`:
A table can also have a composite primary key, which consists of multiple columns. For example:

```sql
CREATE TABLE orders (
    order_id INT,
    product_id INT,
    quantity INT,
    PRIMARY KEY (order_id, product_id)
);
```

In this case, the combination of `order_id` and `product_id` uniquely identifies each order item.

## Summary:
In SQL, a primary key is essential for maintaining data integrity and facilitating efficient data retrieval and manipulation. It uniquely identifies each row in a table and plays a critical role in database design and normalization.
