# `LIKE`

- `LIKE` is a powerful operator in SQL used to filter rows based on patterns within string columns. 
- It supports wildcard characters (`%` for zero or more characters, `_` for a single character) to perform flexible matching.
- The `LIKE` operator is often used in conjunction with `SELECT` statements to retrieve specific data based on textual patterns.

**`Example SQL Table`:**

Consider an `employees` table with columns `emp_id`, `fname` (first name), `lname` (last name), `dept` (department), `desig` (designation), and `salary`.

| emp_id | fname   | lname    | dept         | desig          | salary |
|--------|---------|----------|--------------|----------------|--------|
| 1      | John    | Doe      | Accounting   | Accountant     | 50000  |
| 2      | Jane    | Smith    | Marketing    | Sales Manager  | 60000  |
| 3      | Robert  | Johnson  | HR           | HR Assistant   | 55000  |
| 4      | Mary    | Johnson  | Finance      | Cashier        | 70000  |
| 5      | Rachel  | Adams    | IT           | Programmer     | 65000  |
| 6      | Rock    | Martin   | IT           | Programmer     | 95000  |

**1. Using `LIKE "%Acc%";`**

This query retrieves all rows from the `employees` table where the `dept` column contains the substring "`Acc`" anywhere within the department name.

```sql
SELECT * FROM employees WHERE dept LIKE "%Acc%";
```

**Output:**
```
| emp_id | fname | lname   | dept       | desig      | salary |
|--------|-------|---------|------------|------------|--------|
| 1      | John  | Doe     | Accounting | Accountant | 50000  |
```

Explanation: The `LIKE "%Acc%"` condition matches any department (`dept`) containing "Acc" anywhere in its name. This includes "Accounting".

**2. Using `LIKE "%Cash%";`**

This query retrieves all rows from the `employees` table where the `desig` column contains the substring "Cash" anywhere within the designation.

```sql
SELECT * FROM employees WHERE desig LIKE "%Cash%";
```

**Output:**
```
| emp_id | fname | lname   | dept    | desig   | salary |
|--------|-------|---------|---------|---------|--------|
| 4      | Mary  | Johnson | Finance | Cashier | 70000  |
```

Explanation: The `LIKE "%Cash%"` condition matches any designation (`desig`) containing "Cash" anywhere in its name. This includes "`Cashier`".

**3. Using `LIKE "____";`**

This query retrieves all rows from the `employees` table where the `fname` column has exactly four characters (each underscore represents a single character).

```sql
SELECT * FROM employees WHERE fname LIKE "____";
```

**Output:**
```
| emp_id | fname  | lname   | dept       | desig          | salary |
|--------|--------|---------|------------|----------------|--------|
| 1      | John   | Doe     | Accounting | Accountant     | 50000  |
| 2      | Jane   | Smith   | Marketing  | Sales Manager  | 60000  |
| 4      | Mary   | Johnson | Finance    | Cashier        | 70000  |
```

Explanation: The `LIKE "____"` condition matches any `fname` value that exactly consists of four characters.

**4. Using `LIKE "R___";`**

This query retrieves all rows from the `employees` table where the `fname` column starts with "R" followed by exactly three more characters.

```sql
SELECT * FROM employees WHERE fname LIKE "R___";
```

**Output:**
```
| emp_id | fname  | lname  | dept  | desig         | salary |
|--------|--------|--------|-------|---------------|--------|
| 6      | Rock   | Martin | IT    | Programmer    | 95000  |
```

Explanation: The `LIKE "R___"` condition matches any `fname` value that starts with "`R`" and is followed by three more characters.

**Additional Examples:**

You can use `LIKE` with other patterns such as:

- `LIKE "J%"`: Matches all `fname` values that start with "J".
- `LIKE "%s"`: Matches all `fname` values that end with "s".
- `LIKE "_a%"`: Matches all `fname` values that have "a" as the second character.
