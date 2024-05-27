# `Relational operators`

**Relational operators** in SQL are used to compare values in queries. Here are the main relational operators and examples of their usage in MySQL:

1. **Equal To (`=`)**:
    - Used to check if two values are equal.

    ```sql
    SELECT * FROM employees WHERE salary = 50000;
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  2 | Jane Doe |  50000 |
    +----+----------+--------+
    ```

2. **Not Equal To (`!=` or `<>)**:
    - Used to check if two values are not equal.

    ```sql
    SELECT * FROM employees WHERE salary != 50000;
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  1 | John Doe |  60000 |
    |  3 | Mike Lee |  55000 |
    +----+----------+--------+
    ```

3. **Greater Than (`>`)**:
    - Used to check if a value is greater than another value.

    ```sql
    SELECT * FROM employees WHERE salary > 50000;
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  1 | John Doe |  60000 |
    |  3 | Mike Lee |  55000 |
    +----+----------+--------+
    ```

4. **Less Than (`<`)**:
    - Used to check if a value is less than another value.

    ```sql
    SELECT * FROM employees WHERE salary < 50000;
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  4 | Sarah Con|  45000 |
    +----+----------+--------+
    ```

5. **Greater Than or Equal To (`>=`)**:
    - Used to check if a value is greater than or equal to another value.

    ```sql
    SELECT * FROM employees WHERE salary >= 50000;
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  1 | John Doe |  60000 |
    |  2 | Jane Doe |  50000 |
    |  3 | Mike Lee |  55000 |
    +----+----------+--------+
    ```

6. **Less Than or Equal To (`<=`)**:
    - Used to check if a value is less than or equal to another value.

    ```sql
    SELECT * FROM employees WHERE salary <= 50000;
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  2 | Jane Doe |  50000 |
    |  4 | Sarah Con|  45000 |
    +----+----------+--------+
    ```

7. **BETWEEN**:
    - Used to check if a value is within a range.

    ```sql
    SELECT * FROM employees WHERE salary BETWEEN 45000 AND 55000;
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  2 | Jane Doe |  50000 |
    |  3 | Mike Lee |  55000 |
    |  4 | Sarah Con|  45000 |
    +----+----------+--------+
    ```

8. **IN**:
    - Used to check if a value is within a list of values.

    ```sql
    SELECT * FROM employees WHERE salary IN (45000, 55000);
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  3 | Mike Lee |  55000 |
    |  4 | Sarah Con|  45000 |
    +----+----------+--------+
    ```
9. **NOT IN**:
    - Used to filter results that do not match any value in a specified list.

    ```sql
    SELECT * FROM employees WHERE salary NOT IN (45000, 55000);
    ```

    **Output**:
    ```sql
    +----+----------+--------+
    | id | name     | salary |
    +----+----------+--------+
    |  3 | John Doe |  60000 |
    |  4 | Jane Doe |  50000 |
    +----+----------+--------+
    ```

### Example Data Setup

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
