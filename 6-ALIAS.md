# `Alias`

In SQL, aliases provide a way to assign temporary names to tables or columns within the result set of a query. They are particularly useful for improving the readability and meaning of query output by providing alternative names for columns.

## 1. `Setting Alias for a Single Column`

To assign an alias to a single column in a `SELECT` statement, use the `AS` keyword followed by the desired alias name. This technique is beneficial for making column headers more descriptive or user-friendly.

```sql
SELECT acc_no AS 'Account No.' FROM customers;
```

In this example:
- `acc_no` is the original column name in the `customers` table.
- `AS 'Account No.'` assigns the alias `'Account No.'` to the `acc_no` column in the query result.

## 2. `Setting Alias for Multiple Columns`

You can assign aliases to multiple columns within the same `SELECT` statement by separating each column alias with a comma.

```sql
SELECT acc_no AS 'Account No.', name AS 'Customer Name' FROM customers;
```

Here:
- `acc_no AS 'Account No.'` assigns the alias `'Account No.'` to the `acc_no` column.
- `name AS 'Customer Name'` assigns the alias `'Customer Name'` to the `name` column.

## 3. `Using Aliases with Table Names`

Aliases can also be applied to table names within a query to reference tables with different names temporarily.

```sql
SELECT c.acc_no AS 'Account No.', c.name AS 'Customer Name' FROM customers AS c;
```

Here, `c` is an alias for the `customers` table, allowing convenient referencing of table columns using the shorthand `c`.

## 4. `Alias Scope and Impact`

It's important to note that aliases are effective only within the scope of the specific query in which they are defined. They are primarily used for convenience and readability in query output and do not alter the underlying data or table structure.

### Using `SELECT *` vs. Explicit Column Selection

When using `SELECT *` to retrieve all columns from a table, SQL will display the original column names defined in the table schema, not the aliases assigned in a different query.

For example, if you previously ran:

```sql
SELECT acc_no AS 'Account No.', name AS 'Customer Name' FROM customers;
```

Subsequently running:

```sql
SELECT * FROM customers;
```

will display the original column names (`acc_no`, `name`) rather than the aliases (`'Account No.'`, `'Customer Name'`).

To display data with aliases, explicitly specify columns along with their aliases in the `SELECT` statement.

```sql
SELECT acc_no AS 'Account No.', name AS 'Customer Name' FROM customers;
```

This approach allows precise control over column labeling in query output, providing more meaningful or user-friendly names for presentation purposes.

In summary, SQL aliases are powerful tools for enhancing the readability and clarity of query results, enabling users to create more intuitive and informative data presentations.
