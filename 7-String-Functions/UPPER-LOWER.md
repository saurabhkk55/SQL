# `UPPER` and `LOWER` functions

- `UPPER` and `LOWER` functions are used to convert characters within a string to uppercase and lowercase, respectively.

## `Example 1: Using UPPER to Convert a String to Uppercase`
```sql
SELECT UPPER('abcdxyz') AS UppercaseString;
```

**Output:**
```
UppercaseString
----------------
ABCDXYZ
```

In this query, `UPPER('abcdxyz')` converts the string 'abcdxyz' to uppercase, resulting in 'ABCDXYZ'.

## `Example 2: Using LOWER to Convert a String to Lowercase`
```sql
SELECT LOWER('ABCDXYZ') AS LowercaseString;
```

**Output:**
```
LowercaseString
----------------
abcdxyz
```

Here, `LOWER('ABCDXYZ')` converts the string 'ABCDXYZ' to lowercase, resulting in 'abcdxyz'.

## `Example 3: Equivalent Functions UCASE and LCASE`
In some SQL dialects like MySQL, `UCASE` and `LCASE` can also be used as aliases for `UPPER` and `LOWER` respectively. Below are examples using these functions:

```sql
SELECT UCASE('abcdxyz') AS UppercaseString;
SELECT LCASE('ABCDXYZ') AS LowercaseString;
```

**Outputs:**
```
UppercaseString
----------------
ABCDXYZ

LowercaseString
----------------
abcdxyz
```

### `Example 4: Applying UPPER in a Query with a Table`
Suppose we have a table named `employees` with columns `emp_id` and `fname` (first name). We can use `UPPER` to convert the `fname` values to uppercase while retrieving data.

```sql
SELECT emp_id, UPPER(fname) AS uppercase_fname
FROM employees;
```

**Output:**
```
emp_id  |  uppercase_fname
--------|------------------
1       |  ALICE
2       |  BOB
3       |  CAROL
```

In this query, `UPPER(fname)` converts each `fname` value to uppercase as it's being retrieved, showing the uppercase version in the `uppercase_fname` column.
