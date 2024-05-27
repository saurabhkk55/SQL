# `Named constraint`
- A `named constraint` in MySQL is a constraint that is given a specific name at the time of its definition.
- This name helps in identifying the constraint uniquely within the database schema.
- Named constraints provide better manageability, as they can be easily referenced for modification or deletion later.
- By assigning a name to a constraint, you can explicitly identify it in SQL statements, making it easier to understand and maintain the database schema.

### Example: `Using Named Constraint`

Let's create a table to store employee information where the salary should be greater than or equal to 30000, and the department ID should be between 1 and 10. We'll name these constraints for easier management.

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(50),
    salary DECIMAL(10, 2),
    department_id INT,
    CONSTRAINT chk_salary CHECK (salary >= 30000),
    CONSTRAINT chk_department_id CHECK (department_id BETWEEN 1 AND 10)
);
```

In this example:
- We've defined two constraints: one for checking the salary (`chk_salary`) and another for the department ID (`chk_department_id`).
- Each constraint is named using the `CONSTRAINT` keyword followed by the name and the `CHECK` condition.

### `Inserting Data`

Let's insert some sample data into the `employees` table:

```sql
INSERT INTO employees (employee_id, employee_name, salary, department_id) VALUES
(1, 'John Doe', 50000.00, 5),
(2, 'Jane Smith', 40000.00, 12); -- This will violate the chk_department_id constraint
```

### `Output`

After inserting the data, the `employees` table would look like this:

```plaintext
+-------------+--------------+--------+---------------+
| employee_id | employee_name| salary | department_id |
+-------------+--------------+--------+---------------+
| 1           | John Doe     | 50000.00| 5             |
+-------------+--------------+--------+---------------+
```

### `Inserting Data with Violation`

As mentioned, the insertion of data with department ID 12 violates the `chk_department_id` constraint:

```sql
INSERT INTO employees (employee_id, employee_name, salary, department_id) VALUES
(2, 'Jane Smith', 40000.00, 12); -- This will violate the chk_department_id constraint
```

This will result in a MySQL error because the department ID 12 is outside the allowed range specified by the `chk_department_id` constraint.

### `Dropping or Modifying Constraints`

Using named constraints makes it easier to manage constraints later. For example, you can drop or modify a constraint by its name:

```sql
ALTER TABLE employees DROP CONSTRAINT chk_department_id;
```

Or you can modify the constraint condition:

```sql
ALTER TABLE employees MODIFY CONSTRAINT chk_salary CHECK (salary >= 35000);
```

### `Conclusion`

In summary, named constraints provide a convenient way to manage constraints in MySQL databases. They allow you to easily identify and manipulate constraints during table creation or modification.
