# `LIMIT`

- `LIMIT` is used in SQL to restrict the number of rows returned by a query.

**`Example SQL Table`:**

Consider an `employees` table with columns `emp_id`, `fname` (first name), `lname` (last name), `dept` (department), and `salary`.

| emp_id | fname   | lname    | dept         | salary |
|--------|---------|----------|--------------|--------|
| 1      | John    | Doe      | Accounting   | 50000  |
| 2      | Jane    | Smith    | Marketing    | 60000  |
| 3      | Robert  | Johnson  | HR           | 55000  |
| 4      | Mary    | Johnson  | Finance      | 70000  |
| 5      | Rachel  | Adams    | IT           | 65000  |
| 6      | Shwanty | Glenn    | IT           | 65000  |

**1. Using `LIMIT 3;`**

This query retrieves the first 3 rows from the `employees` table.

```sql
SELECT * FROM employees LIMIT 3;
```

**Output:**
```
| emp_id | fname   | lname   | dept        | salary |
|--------|---------|---------|-------------|--------|
| 1      | John    | Doe     | Accounting  | 50000  |
| 2      | Jane    | Smith   | Marketing   | 60000  |
| 3      | Robert  | Johnson | HR          | 55000  |
```

Explanation: The `LIMIT 3` clause limits the result set to the first 3 rows of the `employees` table.

**2. Using `LIMIT 3, 3;`**

This query skips the first 3 rows and then retrieves the next 3 rows from the `employees` table.

```sql
SELECT * FROM employees LIMIT 3, 3;
```

**Output:**
```
| emp_id | fname   | lname   | dept       | salary |
|--------|---------|---------|------------|--------|
| 4      | Mary    | Johnson | Finance    | 70000  |
| 5      | Rachel  | Adams   | IT         | 65000  |
| 6      | Shwanty | Glenn   | IT         | 65000  |
```

Explanation: The `LIMIT 3, 3` clause skips the first 3 rows and then retrieves the next 3 rows from the `employees` table.

**3. Using `ORDER BY salary DESC LIMIT 1;`**

This query retrieves the employee with the highest salary from the `employees` table.

```sql
SELECT * FROM employees ORDER BY salary DESC LIMIT 1;
```

**Output:**
```
| emp_id | fname   | lname   | dept    | salary |
|--------|---------|---------|---------|--------|
| 4      | Mary    | Johnson | Finance | 70000  |
```

**Explanation**: The `ORDER BY salary DESC LIMIT 1` clause orders the rows by `salary` in descending order and then limits the result to only 1 row, which corresponds to the employee with the highest salary (`70000` in this case).
