# `INSERT` function

- `INSERT` function is used to insert a substring into a string at a specified position. The syntax for `INSERT` varies slightly across different database systems, so it's important to refer to the documentation for your specific database.

## `Example 1: Using INSERT Function`
The `INSERT` function typically has the following syntax:
```
INSERT(original_string, start_position, num_chars_to_replace, new_string)
```
- `original_string`: The original string where the insertion will occur.
- `start_position`: The position in the `original_string` where the insertion will start (1-based index).
- `num_chars_to_replace`: The number of characters to replace starting from `start_position`.
- `new_string`: The substring that will be inserted into the `original_string`.

Let's illustrate this with an example:

```sql
SELECT INSERT('Hello wassup', 6, 0, 'Raju') AS ModifiedString;
```

**Output:**
```
ModifiedString
---------------
Hello Rajuwassup
```

In this example:
- `original_string` is `'Hello wassup'`.
- `start_position` is `6`, indicating the insertion point after the 5th character ('o').
- `num_chars_to_replace` is `0`, meaning no characters are replaced; insertion occurs before the specified position.
- `new_string` is `'Raju'`, which is inserted into `original_string` starting at the 6th position.

The resulting string is `'Hello Rajuwassup'`, where `'Raju'` has been inserted after the 5th character.

## `Example 2: Using INSERT in a Query with a Table`
Suppose we have a table named `employees` with columns `emp_id` and `fname` (first name). We can use `INSERT` to insert a substring into each `fname` value.

```sql
SELECT emp_id, INSERT(fname, 3, 0, 'XYZ') AS ModifiedName
FROM employees;
```

**Output (hypothetical):**
```
emp_id  |  ModifiedName
--------|----------------
1       |  AlXYZice
2       |  BoXYZb
3       |  CaXYZrol
```

In this query:
- `INSERT(fname, 3, 0, 'XYZ')` inserts `'XYZ'` into each `fname` at the 3rd position without replacing any characters.
