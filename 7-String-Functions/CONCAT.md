# `CONCAT` function:

In SQL, the `CONCAT` function is used to concatenate strings together. It can concatenate multiple strings or columns with optional separator strings. This function is particularly useful for combining textual data from different columns or adding constant strings to column values.

### 1. `Concatenating Two Strings`
**Syntax:**
```sql
SELECT CONCAT('string1', 'string2');
```
**Example:**
```sql
SELECT CONCAT('Hey', ' buddy');
```
**Output:**
```
Hey buddy
```

### 2. `Concatenating Multiple Strings`
**Syntax:**
```sql
SELECT CONCAT('string1', 'string2', 'string3', ...);
```
**Example:**
```sql
SELECT CONCAT('Hey', ' buddy', ' Hello');
```
**Output:**
```
Hey buddy Hello
```

### 3. `Concatenating Columns with Alias`
**Syntax:**
```sql
SELECT column1, CONCAT(column2, ' ', column3) AS concatenated_column_name FROM table_name;
```
**Example:**
```sql
SELECT emp_id, CONCAT(fname, ' ', lname) AS FullName FROM employees;
```
**Output:**
```
emp_id   |   FullName
---------|--------------
1        |   John Doe
2        |   Jane Smith
3        |   Michael Johnson
```

### 4. `Concatenating a String with a Column`
**Syntax:**
```sql
SELECT column1, CONCAT(column2, 'constant_string') AS concatenated_column_name FROM table_name;
```
**Example:**
```sql
SELECT emp_id, CONCAT(fname, 'ABCD') AS FullName FROM employees;
```
**Output:**
```
emp_id   |   FullName
---------|--------------
1        |   JohnABCD
2        |   JaneABCD
3        |   MichaelABCD
```

### `Explanation`:
- **Example 1:** Concatenates 'Hey' and ' buddy' to form 'Hey buddy'.
- **Example 2:** Concatenates 'Hey', ' buddy', and ' Hello' to form 'Hey buddy Hello'.
- **Example 3:** Concatenates the `fname` and `lname` columns with a space in between, aliased as `FullName`.
- **Example 4:** Concatenates the `fname` column with the constant string 'ABCD', aliased as `FullName`.
