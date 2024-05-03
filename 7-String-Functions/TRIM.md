# `TRIM` function

- `TRIM` function is used to remove leading and trailing spaces (or other specified characters) from a string. This function is helpful for cleaning up string data by removing unnecessary whitespace.

## `Example 1: Using TRIM Function`
Let's use the `TRIM` function to remove leading and trailing spaces from the string `'   Alright!    '`.

```sql
SELECT TRIM('   Alright!    ') AS TrimmedString;
```

**Output:**
```
TrimmedString
-------------
Alright!
```

In this example:
- `'   Alright!    '` is the input string containing leading and trailing spaces.
- `TRIM('   Alright!    ')` removes the leading and trailing spaces from the input string.
- The result is `'Alright!'`, where the spaces have been trimmed from both sides of the original string.

## `Example 2: Using TRIM in a Query with a Table`
Let's consider a scenario where we have a table named `users` with a column `username` that may have leading or trailing spaces. We can use `TRIM` to clean up the `username` values.

```sql
-- Create a sample users table
CREATE TABLE users (
    user_id INT,
    username VARCHAR(50)
);

-- Insert sample data with leading/trailing spaces
INSERT INTO users (user_id, username) VALUES
(1, '   JohnDoe   '),
(2, '   AliceSmith'),
(3, 'BobJones   ');

-- Use TRIM in a query to retrieve cleaned usernames
SELECT user_id, username, TRIM(username) AS CleanedUsername
FROM users;
```

**Output (hypothetical):**
```
user_id  |  username        |  CleanedUsername
---------|------------------|-----------------
1        |   JohnDoe        |  JohnDoe
2        |   AliceSmith     |  AliceSmith
3        | BobJones         |  BobJones
```

In this example:
- The `users` table contains `username` values with leading or trailing spaces.
- `TRIM(username)` is used in the query to remove leading and trailing spaces from the `username` column.
- The result includes a column `CleanedUsername` where the `username` values are cleaned (trimmed) of any leading or trailing spaces.
