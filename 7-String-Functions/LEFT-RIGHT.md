# `LEFT` and `RIGHT` functions
- `LEFT` and `RIGHT` functions are used to extract a specified number of characters from the beginning (`LEFT`) or end (`RIGHT`) of a string respectively.

## `Example 1: Using LEFT Function`
The `LEFT` function retrieves a specified number of characters from the beginning (left) of a string.

```sql
SELECT LEFT('Hey buddy raju', 3) AS LeftSubstring;
```

**Output:**
```
LeftSubstring
-------------
Hey
```

In this example:
- `'Hey buddy raju'` is the input string.
- `3` specifies the number of characters to extract from the left.
- The result is `'Hey'`, which consists of the first 3 characters from the left of the input string.

## `Example 2: Using RIGHT Function`
The `RIGHT` function retrieves a specified number of characters from the end (right) of a string.

```sql
SELECT RIGHT('Hey buddy raju', 4) AS RightSubstring;
```

**Output:**
```
RightSubstring
--------------
raju
```

Here:
- `'Hey buddy raju'` is the input string.
- `4` specifies the number of characters to extract from the right.
- The result is `'raju'`, which consists of the last 4 characters from the right of the input string.

## `Example 3: Using LEFT and RIGHT in a Query with a Table`
Suppose we have a table named `employees` with a `fname` column (first name). We can use `LEFT` and `RIGHT` to extract substrings from the `fname` values.

```sql
SELECT emp_id, fname, LEFT(fname, 3) AS FirstThreeChars, RIGHT(fname, 2) AS LastTwoChars
FROM employees;
```

**Output (hypothetical):**
```
emp_id  |  fname      |  FirstThreeChars  |  LastTwoChars
--------|-------------|-------------------|----------------
1       |  Alice      |  Ali              |  ce
2       |  Bob        |  Bob              |  ob
3       |  Carol      |  Car              |  ol
```

In this query:
- `LEFT(fname, 3)` extracts the first three characters from each `fname`.
- `RIGHT(fname, 2)` extracts the last two characters from each `fname`.
