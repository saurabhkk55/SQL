# `COUNT`

- `COUNT` is a SQL aggregate function used to calculate the number of rows or non-NULL values in a column. 
- It can be used with `*` to count all rows, with a specific column name to count non-NULL values in that column, or with `DISTINCT` to count distinct (unique) values. 
- `COUNT` can also be combined with conditional expressions (`WHERE` clause) to count rows based on certain conditions.

**`Example SQL Table`:**

Consider an `employees` table with columns `emp_id`, `fname` (first name), `lname` (last name), `dept` (department), `desig` (designation), and `salary`.

| emp_id | fname   | lname    | dept         | desig          | salary |
|--------|---------|----------|--------------|----------------|--------|
| 1      | John    | Doe      | Accounting   | Accountant     | 50000  |
| 2      | Jane    | Smith    | Marketing    | Sales Manager  | 60000  |
| 3      | Robert  | Johnson  | HR           | HR Assistant   | 55000  |
| 4      | Mary    | Johnson  | Finance      | Cashier        | 70000  |
| 5      | Rachel  | Adams    | IT           | Programmer     | 65000  |
| 6      | Jane    | Flenn    | Marketing    | Sales Manager  | 60000  |

**1. Using `COUNT(*)`:**

This query counts the total number of rows in the `employees` table.

```sql
SELECT COUNT(*) FROM employees;
```

**Output:**
```
| COUNT(*) |
|----------|
| 6        |
```

Explanation: The `COUNT(*)` function returns the total number of rows in the `employees` table, which is `5` in this case.

**2. Using `COUNT(fname)`:**

This query counts the number of non-NULL values in the `fname` column of the `employees` table.

```sql
SELECT COUNT(fname) FROM employees;
```

**Output:**
```
| COUNT(fname) |
|--------------|
| 6            |
```

Explanation: The `COUNT(fname)` function counts the number of non-NULL values in the `fname` column of the `employees` table. Since all `fname` values are non-NULL, the result is `5`.

**3. Using `COUNT(DISTINCT fname)`:**

This query counts the number of distinct (unique) values in the `fname` column of the `employees` table.

```sql
SELECT COUNT(DISTINCT fname) FROM employees;
```

**Output:**
```
| COUNT(DISTINCT fname)  |
|------------------------|
| 5                      |
```

Explanation: The `COUNT(DISTINCT fname)` function counts the number of distinct (unique) values in the `fname` column of the `employees` table.

**4. Using `COUNT(emp_id)`:**

This query counts the number of non-NULL values in the `emp_id` column for rows where the `dept` column is equal to "`Marketing`".

```sql
SELECT COUNT(emp_id) FROM employees WHERE dept = 'Marketing';
```

**Output:**
```
| COUNT(emp_id) |
|---------------|
| 2             |
```

Explanation: The `COUNT(emp_id)` function counts the number of non-NULL values in the `emp_id` column of rows where the `dept` column is equal to "`Marketing`". In this case, there is `2` employee with the dept "`Marketing`".

**`Additional Example`:**

You can also use `COUNT` with conditional expressions to count specific rows based on certain criteria.

```sql
SELECT COUNT(*) FROM employees WHERE salary > 60000;
```

**Output:**
```
| COUNT(*) |
|----------|
| 2        |
```

Explanation: This query counts the number of rows in the `employees` table where the `salary` is greater than `60000`, which results in `2` employees (`Mary` and `Rachel`).
