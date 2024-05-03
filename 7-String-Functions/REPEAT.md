# `REPEAT` function
- `REPEAT` function is used to repeat a string a specified number of times. This is useful for generating repeated sequences of characters within a string.

## `Example 1: Using REPEAT Function`
Let's use the `REPEAT` function to repeat the string `'hi '` five times.

```sql
SELECT REPEAT('hi ', 5) AS RepeatedString;
```

**Output:**
```
RepeatedString
--------------
hi hi hi hi hi
```

In this example:
- `'hi '` is the string that will be repeated.
- `5` is the number of times the string `'hi '` will be repeated.
- The result is `'hi hi hi hi hi'`, where `'hi '` is repeated 5 times with spaces in between.

## `Example 2: Using REPEAT in a Query with a Table`
Suppose we want to generate a repeated sequence of characters based on a column value in a table. Let's consider a table named `numbers` with a `num` column that specifies the number of times a string should be repeated.

```sql
-- Create a sample table
CREATE TABLE numbers (
    id INT,
    num INT
);

-- Insert some sample data
INSERT INTO numbers (id, num) VALUES (1, 3), (2, 5), (3, 2);

-- Use REPEAT in a query
SELECT id, num, REPEAT('abc ', num) AS RepeatedString
FROM numbers;
```

**Output (hypothetical):**
```
id  |  num  |  RepeatedString
----|-------|-----------------
1   |  3    |  abc abc abc 
2   |  5    |  abc abc abc abc abc 
3   |  2    |  abc abc
```

In this example:
- `REPEAT('abc ', num)` generates a repeated sequence of `'abc '` based on the `num` value for each row in the `numbers` table.
- The result is a column `RepeatedString` where the string `'abc '` is repeated `num` times for each row.
