# `MIN` & `MAX` functions

In SQL, `MIN` and `MAX` are aggregate functions used to find the `minimum` and `maximum` values within a selected column, respectively. Here's a breakdown of their definitions:

### `MIN` Function:
- Returns the smallest value in a specified column.
- Can be used with numerical columns (integers, decimals) as well as character columns (strings).
- For character columns, it returns the value that comes first alphabetically.

    Syntax:
    ```
    SELECT MIN(column_name) FROM table_name;
    ```

### `MAX` Function:
- Returns the largest value in a specified column.
- Can be used with numerical columns (integers, decimals) as well as character columns (strings).
- For character columns, it returns the value that comes last alphabetically.

    Syntax:
    ```
    SELECT MAX(column_name) FROM table_name;
    ```

## `Table Creation and Sample Data`
```sql
CREATE TABLE employees (
    emp_id INT,
    fname VARCHAR(50),
    lname VARCHAR(50),
    salary DECIMAL(10, 2)
);

INSERT INTO employees (emp_id, fname, lname, salary)
VALUES
    (1, 'Alice', 'Smith', 50000.00),
    (2, 'Bob', 'Johnson', 60000.00),
    (3, 'Charlie', 'Brown', 70000.00),
    (4, 'David', 'Lee', 80000.00),
    (5, 'Eve', 'Taylor', 90000.00);
```

## `Query 1: Find the Maximum and Minimum Salary`
```sql
SELECT MAX(salary) AS MaxSalary FROM employees;
-- Output: 
-- +-----------+
-- | MaxSalary |
-- +-----------+
-- | 90000.00  |
-- +-----------+

SELECT MIN(salary) AS MinSalary FROM employees;
-- Output:
-- +-----------+
-- | MinSalary |
-- +-----------+
-- | 50000.00  |
-- +-----------+
```

## `Query 2: Retrieve fname and Maximum Salary`
```sql
SELECT fname, MAX(salary) AS MaxSalary FROM employees;
-- Output: 
-- +-------+-----------+
-- | fname | MaxSalary |
-- +-------+-----------+
-- | Alice | 90000.00  |
-- +-------+-----------+
```
> **`NOTE`**: This query returns the `first name` in the `fname column` alongside the `maximum salary`, `not the employee with the maximum salary`.

## `Query 3: Retrieve emp_id, fname, Salary of the Employee with the Maximum Salary`
```sql
SELECT emp_id, fname, salary
FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees);
-- Output:
-- +--------+-------+---------+
-- | emp_id | fname | salary  |
-- +--------+-------+---------+
-- | 5      | Eve   | 90000.00|
-- +--------+-------+---------+
```

## `Query 4: Retrieve All Columns for the Employee with Maximum Salary`
```sql
SELECT *
FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees);
-- Output:
-- +--------+-------+--------+---------+
-- | emp_id | fname | lname  | salary  |
-- +--------+-------+--------+---------+
-- | 5      | Eve   | Taylor | 90000.00|
-- +--------+-------+--------+---------+
-- This query returns all columns for the employee(s) with the maximum salary.
```

## `Query 5: Find the Maximum fname and Minimum lname`
```sql
SELECT MAX(fname) AS MaxFname FROM employees;
-- Output:
-- +---------+
-- | MaxFname|
-- +---------+
-- | Eve     |
-- +---------+

SELECT MIN(lname) AS MinLname FROM employees;
-- Output:
-- +---------+
-- | MinLname|
-- +---------+
-- | Brown   |
-- +---------+
```
