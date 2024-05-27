Logical operators in SQL are used to combine multiple conditions in a query. Here are the main logical operators in SQL along with examples and expected output in MySQL:

## 1. `AND`:
Combines two conditions and returns true if both conditions are true.

```sql
SELECT * FROM employees WHERE salary > 45000 AND salary < 60000;
```

**Output**:
```plaintext
+----+----------+--------+
| id | name     | salary |
+----+----------+--------+
|  2 | Jane Doe |  50000 |
|  3 | Mike Lee |  55000 |
+----+----------+--------+
```

**Explanation of Output**:
- The query retrieves employees whose salary is greater than 45000 and less than 60000.
- Expected result: Employees Jane Doe and Mike Lee.

## 2. `OR`:
Combines two conditions and returns true if at least one of the conditions is true.

```sql
SELECT * FROM employees WHERE salary < 45000 OR salary > 55000;
```

**Output**:
```sql
+----+----------+--------+
| id | name     | salary |
+----+----------+--------+
|  1 | John Doe |  60000 |
+----+----------+--------+
```

**Explanation of Output**:
- The query retrieves employees whose salary is either less than 45000 or greater than 55000.
- Expected result: Employee John Doe.

## 3. `NOT`:

Returns true if the condition is false.

```sql
SELECT * FROM employees WHERE NOT (salary = 50000);
```

**Output**:
```plaintext
+----+----------+--------+
| id | name     | salary |
+----+----------+--------+
|  1 | John Doe |  60000 |
|  3 | Mike Lee |  55000 |
|  4 | Sarah Con|  45000 |
+----+----------+--------+
```

**Explanation of Output**:
- The query retrieves employees whose salary is not equal to 50000.
- Expected result: Employees John Doe, Mike Lee, and Sarah Con.

## 4. `Combining AND, OR, and NOT`:
You can combine these logical operators to form complex queries.

```sql
SELECT * FROM employees WHERE (salary > 45000 AND salary < 60000) OR NOT (name = 'John Doe');
```

**Output**:
```plaintext
+----+----------+--------+
| id | name     | salary |
+----+----------+--------+
|  2 | Jane Doe |  50000 |
|  3 | Mike Lee |  55000 |
|  4 | Sarah Con|  45000 |
+----+----------+--------+
```

**Explanation of Output**:
- The query retrieves employees whose salary is between 45000 and 60000 or whose name is not 'John Doe'.
- Expected result: Employees Jane Doe, Mike Lee, and Sarah Con. (John Doe is excluded because his salary does not fall within the specified range and his name is 'John Doe').

## `Example Data Setup`

Here is how the sample `employees` table can be created and populated with data for the examples above:

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
