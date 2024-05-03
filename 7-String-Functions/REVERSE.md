# `REVERSE` function

- `REVERSE` function in SQL is used to reverse the characters within a string.
- `REVERSE` works with string types (e.g., `VARCHAR`, `CHAR`) and can handle Unicode characters.
- It's important to note that `REVERSE` does not modify the original string value stored in the table; it only affects the output of the query.

## `Example 1: Basic Usage`
Let's start with a simple example of using `REVERSE` with a string literal.

```sql
SELECT REVERSE('HELLO') AS ReversedString;
```

**Output:**
```
ReversedString
--------------
OLLEH
```

In this query, `REVERSE('HELLO')` reverses the characters in the string 'HELLO', resulting in 'OLLEH'.

## `Example 2: Reversing a Column in a Table`
Suppose we have a table named `employees` with columns `emp_id` and `fname` (first name). We can use `REVERSE` to reverse the characters in the `fname` column while retrieving data.

```sql
SELECT emp_id, fname, REVERSE(fname) AS reversed_fname
FROM employees;
```

**Output:**
```
emp_id  |  fname  |  reversed_fname
--------|---------|----------------
1       |  Alice  |  ecilA
2       |  Bob    |  boB
3       |  Carol  |  loraC
```

In this query, `REVERSE(fname)` reverses the characters in each value of the `fname` column and returns it as `reversed_fname`.

## `Example 3: Using REVERSE in a WHERE Clause`
You can also use `REVERSE` in a `WHERE` clause for specific conditions.

```sql
SELECT emp_id, fname
FROM employees
WHERE REVERSE(fname) = 'nahtanoj'; -- Searching for names that reverse to 'Jonathan'
```

**Output (hypothetical):**
```
emp_id  |  fname
--------|---------
4       |  Jonathan
```

This query would find and return employees whose first name, when reversed, matches 'nahtanoJ'.
