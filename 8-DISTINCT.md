# `DISTINCT`

`SELECT DISTINCT` is useful for filtering out duplicate rows in the result set based on specified columns, allowing you to focus on unique values within those columns.

**`Example SQL Table`:**

Consider an `employees` table with columns `fname` (first name), `lname` (last name), `dept` (department), and `salary`.

| emp_id | fname   | lname    | dept      | salary |
|--------|---------|----------|-----------|--------|
| 1      | John    | Doe      | Sales     | 50000  |
| 2      | Jane    | Smith    | Marketing | 60000  |
| 3      | John    | Johnson  | HR        | 55000  |
| 4      | Mary    | Johnson  | Finance   | 70000  |
| 5      | John    | Doe      | IT        | 65000  |

**1. Using `SELECT DISTINCT fname FROM employees;`**

This query retrieves all distinct first names (`fname`) from the `employees` table.

```sql
SELECT DISTINCT fname FROM employees;
```

**Output:**
```
| fname |
|-------|
| John  |
| Jane  |
| Mary  |
```

Explanation: This query selects unique first names from the `fname` column in the `employees` table. Duplicate names are eliminated, so each name appears only once in the result set.

**2. Using `SELECT DISTINCT fname, lname FROM employees;`**

This query retrieves distinct combinations of first names (`fname`) and last names (`lname`) from the `employees` table.

```sql
SELECT DISTINCT fname, lname FROM employees;
```

**Output:**
```
| fname | lname    |
|-------|----------|
| John  | Doe      |
| Jane  | Smith    |
| John  | Johnson  |
| Mary  | Johnson  |
```

Explanation: Here, the query selects unique combinations of `fname` and `lname` from the `employees` table. Each combination of first and last name appears only once in the result set.

**3 `Additional Example`:**

Let's say you want to retrieve unique departments (`dept`) from the `employees` table:

```sql
SELECT DISTINCT dept FROM employees;
```

**Output:**
```
| dept      |
|-----------|
| Sales     |
| Marketing |
| HR        |
| Finance   |
| IT        |
```

Explanation: This query selects distinct department names (`dept`) from the `employees` table. Each department name appears only once in the result set, even if multiple employees are in the same department.
