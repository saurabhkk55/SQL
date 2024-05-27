# `CASE` statement

- The `CASE` statement in MySQL is used to add conditional logic to SQL queries. 
- It allows you to create complex queries that can return different values based on different conditions. 
- Here is an example using the `employees` table.

### Example Data Setup

Let's use the same `employees` table as before:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    salary INT
);

INSERT INTO employees (id, name, salary) VALUES
(1, 'John Doe', 60000),
(2, 'Jane Doe', 50000),
(3, 'Mike Lee', 55000),
(4, 'Sarah Con', 45000);
```

### CASE Statement Example

Here is an example query using the `CASE` statement to categorize employees based on their salary:

```sql
SELECT 
    id, 
    name, 
    salary,
    CASE 
        WHEN salary >= 60000 THEN 'High Salary'
        WHEN salary >= 50000 AND salary < 60000 THEN 'Medium Salary'
        ELSE 'Low Salary'
    END AS salary_category
FROM employees;
```

**Output**:
```plaintext
+----+----------+--------+----------------+
| id | name     | salary | salary_category|
+----+----------+--------+----------------+
|  1 | John Doe |  60000 | High Salary    |
|  2 | Jane Doe |  50000 | Medium Salary  |
|  3 | Mike Lee |  55000 | Medium Salary  |
|  4 | Sarah Con|  45000 | Low Salary     |
+----+----------+--------+----------------+
```

### Explanation

- **id**: The ID of the employee.
- **name**: The name of the employee.
- **salary**: The salary of the employee.
- **salary_category**: The category of the salary determined by the `CASE` statement.

#### CASE Statement Logic:

1. **WHEN salary >= 60000 THEN 'High Salary'**:
    - If the salary is greater than or equal to 60000, the category is 'High Salary'.
    - Employee John Doe falls into this category.

2. **WHEN salary >= 50000 AND salary < 60000 THEN 'Medium Salary'**:
    - If the salary is between 50000 and 59999, the category is 'Medium Salary'.
    - Employees Jane Doe and Mike Lee fall into this category.

3. **ELSE 'Low Salary'**:
    - If none of the above conditions are met, the category is 'Low Salary'.
    - Employee Sarah Con falls into this category.

### Another Example: Using CASE in ORDER BY

You can also use the `CASE` statement in the `ORDER BY` clause to sort results based on conditional logic. For example, to sort employees by salary category:

```sql
SELECT 
    id, 
    name, 
    salary,
    CASE 
        WHEN salary >= 60000 THEN 'High Salary'
        WHEN salary >= 50000 AND salary < 60000 THEN 'Medium Salary'
        ELSE 'Low Salary'
    END AS salary_category
FROM employees
ORDER BY 
    CASE 
        WHEN salary >= 60000 THEN 1
        WHEN salary >= 50000 AND salary < 60000 THEN 2
        ELSE 3
    END;
```

**Output**:
```plaintext
+----+----------+--------+----------------+
| id | name     | salary | salary_category|
+----+----------+--------+----------------+
|  1 | John Doe |  60000 | High Salary    |
|  2 | Jane Doe |  50000 | Medium Salary  |
|  3 | Mike Lee |  55000 | Medium Salary  |
|  4 | Sarah Con|  45000 | Low Salary     |
+----+----------+--------+----------------+
```

### Explanation

- The `ORDER BY` clause uses the `CASE` statement to assign a sorting order based on the salary category.
- Employees are sorted with 'High Salary' first, 'Medium Salary' second, and 'Low Salary' last.
