# `ORDER BY`

`ORDER BY` is used in SQL to sort the result set based on specified columns or expressions either in ascending (default) or descending order. It can be combined with various SQL statements to arrange and present data in a desired order.

**`Example SQL Table`:**

Consider an `employees` table with columns `emp_id`, `fname` (first name), `lname` (last name), `dept` (department), and `salary`.

| emp_id | fname   | lname    | dept      | salary |
|--------|---------|----------|-----------|--------|
| 1      | John    | Doe      | Sales     | 50000  |
| 2      | Jane    | Smith    | Marketing | 60000  |
| 3      | John    | Johnson  | HR        | 55000  |
| 4      | Mary    | Johnson  | Finance   | 70000  |
| 5      | John    | Doe      | IT        | 65000  |

**1. Using `ORDER BY fname;`**

This query retrieves all rows from the `employees` table and orders them by the `fname` column in ascending alphabetical order.

```sql
SELECT * FROM employees ORDER BY fname;
```

**Output:**
```
| emp_id | fname | lname    | dept      | salary |
|--------|-------|----------|-----------|--------|
| 2      | Jane  | Smith    | Marketing | 60000  |
| 1      | John  | Doe      | Sales     | 50000  |
| 3      | John  | Johnson  | HR        | 55000  |
| 5      | John  | Doe      | IT        | 65000  |
| 4      | Mary  | Johnson  | Finance   | 70000  |
```

Explanation: This query orders the rows of the `employees` table by the `fname` column in ascending order (A-Z). Rows with the same `fname` are ordered by their primary key (`emp_id` in this case).

**2. Using `ORDER BY fname DESC;`**

This query retrieves all rows from the `employees` table and orders them by the `fname` column in descending alphabetical order.

```sql
SELECT * FROM employees ORDER BY fname DESC;
```

**Output:**
```
| emp_id | fname | lname    | dept      | salary |
|--------|-------|----------|-----------|--------|
| 4      | Mary  | Johnson  | Finance   | 70000  |
| 5      | John  | Doe      | IT        | 65000  |
| 3      | John  | Johnson  | HR        | 55000  |
| 1      | John  | Doe      | Sales     | 50000  |
| 2      | Jane  | Smith    | Marketing | 60000  |
```

Explanation: This query orders the rows of the `employees` table by the `fname` column in descending order (Z-A).

**3. Using `ORDER BY dept, fname;`**

This query retrieves specific columns (`dept` and `fname`) from the `employees` table and orders the results first by `dept` in ascending order, then by `fname` in ascending order within each department.

```sql
SELECT dept, fname FROM employees ORDER BY dept, fname;
```

**Output:**
```
| dept      | fname |
|-----------|-------|
| Finance   | Mary  |
| HR        | John  |
| HR        | John  |
| IT        | John  |
| Marketing | Jane  |
| Sales     | John  |
```

Explanation: This query orders the selected rows by `dept` first (in alphabetical order) and then by `fname` within each department.

**`Additional Example`:**

You can also use `ORDER BY` with aggregate functions. For example, to find the highest salary (`MAX`) in each department and order the results by department:

```sql
SELECT dept, MAX(salary) AS max_salary
FROM employees
GROUP BY dept
ORDER BY max_salary DESC;
```

**Output:**
```
| dept      | max_salary |
|-----------|------------|
| Finance   | 70000      |
| IT        | 65000      |
| HR        | 55000      |
| Marketing | 60000      |
| Sales     | 50000      |
```

**Explanation**: This query calculates the maximum salary (`MAX(salary)`) for each department, groups the results by department (`GROUP BY dept`), and then orders the departments by their maximum salary in descending order (`ORDER BY max_salary DESC`).
