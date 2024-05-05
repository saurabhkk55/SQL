# `SUM` and `AVG` functions
In SQL, `SUM` and `AVG` are aggregate functions used to perform calculations on sets of values in a table.

### 1. `SUM` Function

The `SUM` function is used to calculate the sum (total) of values in a specified column or expression.

**Syntax:**
```sql
SELECT SUM(column_name) FROM table_name;
```
**Example:**
```sql
-- Calculate the total salary sum of all employees
SELECT SUM(salary) FROM employees;
```

### 2. `AVG` Function

The `AVG` function is used to calculate the average (mean) of values in a specified column or expression.

**Syntax:**
```sql
SELECT AVG(column_name) FROM table_name;
```
**Example:**
```sql
-- Calculate the average salary of all employees
SELECT AVG(salary) FROM employees;
```

### `Additional Notes`:

- Both `SUM` and `AVG` are aggregate functions that operate on a set of values and return a single value summarizing that set.
- These functions are often used in conjunction with the `GROUP BY` clause to calculate aggregated values for specific groups within a table (e.g., by department).
- `SUM` is used for adding up numerical values, while `AVG` computes the average of those values.
- If the specified column contains `NULL` values, `SUM` ignores `NULL` values and calculates the sum of non-`NULL` values, while `AVG` also ignores `NULL` values and calculates the average based on non-`NULL` values.

### `Sample Table: employees`

| emp_id | name   | dept   | salary |
|--------|--------|--------|--------|
| 1      | Alice  | Sales  | 5000   |
| 2      | Bob    | IT     | 6000   |
| 3      | Charlie| HR     | 4500   |
| 4      | David  | Sales  | 4800   |
| 5      | Eve    | IT     | 5500   |

### `Examples with Output`:

#### 1. `Total Salary of all Employees`:
```sql
SELECT SUM(salary) FROM employees;
```
Output:
```
SUM(salary)
--------
25800
```

#### 2. `Average Salary of all Employees`:
```sql
SELECT AVG(salary) FROM employees;
```
Output:
```
AVG(salary)
--------
5160
```

#### 3. `Total Salary by Department`:
```sql
SELECT dept, SUM(salary) FROM employees GROUP BY dept;
```
Output:
```
dept   | SUM(salary)
-------|-----------
Sales  | 9800
IT     | 11500
HR     | 4500
```

#### 4. `Count of Employees, Total Salary by Department`:
```sql
SELECT dept, COUNT(emp_id), SUM(salary) FROM employees GROUP BY dept;
```
Output:
```
dept   | COUNT(emp_id) | SUM(salary)
-------|---------------|-----------
Sales  | 2             | 9800
IT     | 2             | 11500
HR     | 1             | 4500
```
