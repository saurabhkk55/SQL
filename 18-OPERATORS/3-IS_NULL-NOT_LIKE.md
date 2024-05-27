# `IS NULL` and `NOT LIKE` operators

The `IS NULL` and `NOT LIKE` operators in MySQL are used to filter results based on the `presence of null values` and `patterns in text data`, respectively. 

Here are examples demonstrating their usage along with expected outputs.

## `Example Data Setup`

First, let's set up the `employees` table with some additional data to illustrate the use of `IS NULL` and `NOT LIKE`:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    salary INT,
    department VARCHAR(50)
);

INSERT INTO employees (id, name, salary, department) VALUES
(1, 'John Doe', 60000, 'Sales'),
(2, 'Jane Doe', 50000, NULL),
(3, 'Mike Lee', 55000, 'Marketing'),
(4, 'Sarah Con', 45000, 'Sales'),
(5, 'Tom Smith', 50000, 'IT'),
(6, 'Ann Taylor', 60000, NULL);
```

### 1. `IS NULL Example`

The `IS NULL` operator is used to check for null values in a column.

```sql
SELECT * FROM employees WHERE department IS NULL;
```

**Output**:
```plaintext
+----+-----------+--------+------------+
| id | name      | salary | department |
+----+-----------+--------+------------+
|  2 | Jane Doe  | 50000  | NULL       |
|  6 | Ann Taylor| 60000  | NULL       |
+----+-----------+--------+------------+
```

### Explanation

- The query retrieves employees whose `department` column has a `NULL` value.
- Employees Jane Doe and Ann Taylor are selected because their department is `NULL`.

### 2. `NOT LIKE Example`

The `NOT LIKE` operator is used to filter results that do not match a specified pattern. The pattern can include wildcards such as `%` (any sequence of characters) and `_` (a single character).

```sql
SELECT * FROM employees WHERE department NOT LIKE 'S%';
```

**Output**:
```plaintext
+----+----------+--------+------------+
| id | name     | salary | department |
+----+----------+--------+------------+
|  3 | Mike Lee | 55000  | Marketing  |
|  5 | Tom Smith| 50000  | IT         |
|  2 | Jane Doe | 50000  | NULL       |
|  6 | Ann Taylor| 60000 | NULL       |
+----+----------+--------+------------+
```

### Explanation

- The query retrieves employees whose `department` does not start with the letter 'S'.
- Employees Mike Lee and Tom Smith are selected because their departments (`Marketing` and `IT`, respectively) do not start with 'S'.
- Employees Jane Doe and Ann Taylor are also selected because their department is `NULL`, and `NULL` values do not match any pattern.

### 3. `Another Example Using NOT LIKE with Wildcards`

Here is an example using a different pattern with the `NOT LIKE` operator:

```sql
SELECT * FROM employees WHERE name NOT LIKE '%Doe';
```

**Output**:
```plaintext
+----+-----------+--------+------------+
| id | name      | salary | department |
+----+-----------+--------+------------+
|  3 | Mike Lee  | 55000  | Marketing  |
|  4 | Sarah Con | 45000  | Sales      |
|  5 | Tom Smith | 50000  | IT         |
|  6 | Ann Taylor| 60000  | NULL       |
+----+-----------+--------+------------+
```

### Explanation

- The query retrieves employees whose `name` does not end with 'Doe'.
- Employees Mike Lee, Sarah Con, Tom Smith, and Ann Taylor are selected because their names do not end with 'Doe'.

### 4. `Combining IS NULL and NOT LIKE`

You can combine `IS NULL` and `NOT LIKE` in a single query to apply multiple conditions:

```sql
SELECT * FROM employees WHERE department IS NULL OR department NOT LIKE 'S%';
```

**Output**:
```plaintext
+----+-----------+--------+------------+
| id | name      | salary | department |
+----+-----------+--------+------------+
|  2 | Jane Doe  | 50000  | NULL       |
|  3 | Mike Lee  | 55000  | Marketing  |
|  5 | Tom Smith | 50000  | IT         |
|  6 | Ann Taylor| 60000  | NULL       |
+----+-----------+--------+------------+
```

### Explanation

- The query retrieves employees whose `department` is `NULL` or does not start with 'S'.
- Employees Jane Doe and Ann Taylor are selected because their department is `NULL`.
- Employees Mike Lee and Tom Smith are selected because their departments (`Marketing` and `IT`, respectively) do not start with 'S'.
