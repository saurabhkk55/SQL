# `CHECK` constraint

- The `CHECK` constraint in MySQL is used to specify a condition that must be met for values inserted or updated in a column.
- If the condition specified in the `CHECK` constraint evaluates to false, the insert or update operation is rejected, ensuring data integrity.

### Example: `Using CHECK Constraint`

Let's create a table to store information about products, where the `price` column must be a positive value:

```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(50),
    price DECIMAL(10, 2) CHECK (price > 0)
);
```

In this example:
- The `products` table has a `price` column with a `CHECK` constraint that ensures the price is greater than 0.
- The `price` column is defined with the `DECIMAL` data type to store decimal numbers with a precision of 10 digits and a scale of 2 digits (i.e., up to 8 digits before the decimal point and 2 digits after).

### `Inserting Data`

Let's insert some sample data into the `products` table:

```sql
INSERT INTO products (product_id, product_name, price) VALUES
(1, 'Laptop', 1200.00),
(2, 'Smartphone', 800.50),
(3, 'Headphones', -50.00);
```

### `Output`

After inserting the data, the `products` table would look like this:

```plaintext
+------------+--------------+--------+
| product_id | product_name | price  |
+------------+--------------+--------+
| 1          | Laptop       | 1200.00|
| 2          | Smartphone   | 800.50 |
+------------+--------------+--------+
```

### `Inserting Data with Violation`

Let's try to insert data that violates the `CHECK` constraint:

```sql
INSERT INTO products (product_id, product_name, price) VALUES
(4, 'Keyboard', 0.00);
```

This will result in a MySQL error because the price `0.00` violates the `CHECK` constraint, which requires the price to be greater than 0.

### `Modifying Data with Violation`

Similarly, updating data that violates the `CHECK` constraint will also be rejected:

```sql
UPDATE products SET price = -100.00 WHERE product_id = 1;
```

This will also result in a MySQL error because the new price `-100.00` violates the `CHECK` constraint.

### `Conclusion`

In summary, the `CHECK` constraint ensures that values inserted or updated in a column meet specific conditions. It is useful for enforcing data integrity rules, such as ensuring that numeric values are within a certain range or meet specific criteria.
