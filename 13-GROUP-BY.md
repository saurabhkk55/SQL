# `GROUP BY` Clause in SQL

1. It groups the rows based on the specified column(s).
2. Aggregation functions (e.g., `COUNT()`, `SUM()`, `MAX()`, `MIN()`, etc.) are typically used with GROUP BY to provide meaningful summaries of grouped data.
3. The columns in the `SELECT` clause that are not part of the `GROUP BY` clause must be used with an aggregate function.

### `Sample Table: Employees`

| id | fname | lname   | dept | salary |
|----|-------|-------  |------|--------|
| 1  | John  | Doe     | IT   | 50000  |
| 2  | Jane  | Smith   | IT   | 55000  |
| 3  | Bob   | Johnson | HR   | 45000  |
| 4  | Sarah | Lee     | HR   | 48000  |
| 5  | Mike  | Brown   | Sales| 60000  |
| 6  | Emily | Davis   | Sales| 65000  |

The GROUP BY clause in SQL is used to group rows that have the same values into summary rows, like when you want to get the total sales by product or the average salary by department.

Here are the examples you provided:

1. `SELECT dept FROM employees GROUP BY dept;`
   
    **`Output`:**
    | dept |
    |------|
    | IT   |
    | HR   |
    | Sales|

    This query groups the rows by the `dept` column and returns the distinct department names.

2. `SELECT dept, COUNT(fname) FROM employees GROUP BY dept;`
   
    **`Output`:**
    | dept | COUNT(fname) |
    |------|--------------|
    | IT   | 2            |
    | HR   | 2            |
    | Sales| 2            |

    This query groups the rows by the `dept` column and counts the number of first names (using the `COUNT(fname)` function) for each department.

---
## `Statement`
The columns in the `SELECT` clause that are not part of the `GROUP BY` clause must be used with an aggregate function.

When using `GROUP BY` in SQL, any column in the `SELECT` clause that is not part of the `GROUP BY` clause must be used with an aggregate function. This is because `GROUP BY` combines rows into summary rows based on the grouped column(s), and for non-grouped columns, SQL needs instructions on how to aggregate (combine) the values within each group.

Let's illustrate this with an example using a hypothetical `sales` table that contains information about sales transactions, including the `product_id`, `product_name`, `category`, and `sales_amount`.

## `Sample Table Creation`

Consider the following `sales` table:

```sql
CREATE TABLE sales (
    transaction_id INT AUTO_INCREMENT,
    product_id INT,
    product_name VARCHAR(50),
    category VARCHAR(50),
    sales_amount DECIMAL(10, 2),
    PRIMARY KEY (transaction_id)
);

INSERT INTO sales (product_id, product_name, category, sales_amount) VALUES
    (1, 'Laptop', 'Electronics', 1200.00),
    (2, 'Printer', 'Electronics', 300.00),
    (3, 'Desk', 'Furniture', 400.00),
    (4, 'Chair', 'Furniture', 150.00),
    (5, 'Smartphone', 'Electronics', 800.00),
    (6, 'Tablet', 'Electronics', 500.00);
```

## `Example Queries`

Let's look at two different `SELECT` queries involving `GROUP BY` and explain how they work.

### Query 1: Incorrect Usage of `GROUP BY`

```sql
-- Incorrect query: using non-grouped columns without aggregate functions
SELECT category, product_name, SUM(sales_amount)
FROM sales
GROUP BY category;
```

In this query, `category` is used in the `GROUP BY` clause, but `product_name` is not. Additionally, `sales_amount` is being aggregated using `SUM()`. However, `product_name` is not part of the `GROUP BY` clause and is not being aggregated.

**`Output Error`:**
```
Error: SELECT list not in GROUP BY clause and contains nonaggregated column 'product_name' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
```

**`Explanation`**:
- The error message indicates that using `product_name` without an aggregate function (`SUM()`, `MAX()`, `MIN()`, etc.) is not allowed when `category` is used in the `GROUP BY` clause. SQL doesn't know how to combine (aggregate) multiple `product_name` values within each `category` group.

### Query 2: Correct Usage of `GROUP BY`

```sql
-- Correct query: using aggregate functions for non-grouped columns
SELECT category, MAX(product_name) AS max_product_name, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY category;
```

**`Output`:**
```
+------------+-----------------+-------------+
| category   | max_product_name| total_sales |
+------------+-----------------+-------------+
| Electronics| Smartphone      | 2800.00     |
| Furniture  | Desk            | 550.00      |
+------------+-----------------+-------------+
```

`Explanation`:
- In this corrected query:
  - `category` is used in the `GROUP BY` clause.
  - `MAX(product_name)` is used to get the maximum (lexicographically) `product_name` within each `category` group.
  - `SUM(sales_amount)` is used to calculate the total sales amount within each `category` group.

## `Summary`

- When using `GROUP BY` in SQL, any columns in the `SELECT` clause that are not part of the `GROUP BY` clause must be aggregated (e.g., using `SUM()`, `MAX()`, `MIN()`, etc.) to provide meaningful results.
- This ensures that SQL knows how to combine the values of non-grouped columns across rows that belong to the same group specified by the `GROUP BY` clause.
