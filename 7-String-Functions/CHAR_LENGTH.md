# `CHAR_LENGTH` function

- The `CHAR_LENGTH` function in SQL is used to determine the number of characters in a string. It counts characters based on their Unicode code points, making it useful for various text-related operations.

## `Example 1: Using CHAR_LENGTH with a String Literal`
```sql
SELECT CHAR_LENGTH('Hello world') AS Length;
```

**Output:**
```
Length
-------
11
```

Here, `CHAR_LENGTH('Hello world')` returns the number of characters in the string 'Hello world', which is 11.

## `Example 2: Applying CHAR_LENGTH in a Query with a Table`
Suppose we have a table named `employees` with a `fname` column (first name). We can use `CHAR_LENGTH` to calculate the length of each first name.

```sql
SELECT fname, CHAR_LENGTH(fname) AS Length
FROM employees;
```

**Output:**
```
fname  |  Length
-------|--------
Alice  |  5
Bob    |  3
Carol  |  5
```

In this query, `CHAR_LENGTH(fname)` computes the length (number of characters) of each `fname` value in the `employees` table.

## `Example 3: Using CHAR_LENGTH in a WHERE Clause`
We can also use `CHAR_LENGTH` to filter rows based on the length of a string.

```sql
SELECT *
FROM employees
WHERE CHAR_LENGTH(fname) > 5;
```

**Output (hypothetical):**
```
emp_id  |  fname
--------|---------
4       |  Samantha
5       |  Christopher
```

This query retrieves employees whose first names have more than 5 characters, using `CHAR_LENGTH(fname) > 5` as the filtering condition.
