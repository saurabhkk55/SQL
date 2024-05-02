# `CONCAT_WS` function

- The `CONCAT_WS` function in SQL stands for "Concatenate With Separator". It concatenates multiple strings into a single string using a specified separator.
- In `CONCAT_WS`, the first argument specifies the separator, which is then used to join subsequent string arguments. 
- The `CONCAT_WS` function automatically skips `NULL` values and does not add the separator before or after `NULL` values, unlike `CONCAT`.

**`Syntax`:**
```sql
CONCAT_WS(separator, str1, str2, ...)
```
- `separator`: The separator string used to join the input strings.
- `str1, str2, ...`: The strings or columns to be concatenated.

## `Examples`:

1. **`Concatenating Two Strings with Separator`**
   ```sql
   SELECT CONCAT_WS('-', 'HI', 'Hello');
   ```
   **Output:**
   ```
   HI-Hello
   ```

2. **`Concatenating Multiple Strings with Separator`**
   ```sql
   SELECT CONCAT_WS('-', 'HI', 'Hello', 'Jim', 'Luci');
   ```
   **Output:**
   ```
   HI-Hello-Jim-Luci
   ```

3. **`Concatenating Columns with Separator`**
   ```sql
   SELECT CONCAT_WS(':', emp_id, fname, desig) FROM employees;
   ```
   **Output:**
   ```
   1:John:Manager
   2:Jane:Developer
   3:Michael:Analyst
   ```

### `Explanation`:
- **Example 1:** Concatenates the strings 'HI' and 'Hello' with '-' as the separator, resulting in 'HI-Hello'.
- **Example 2:** Concatenates the strings 'HI', 'Hello', 'Jim', and 'Luci' with '-' as the separator, resulting in 'HI-Hello-Jim-Luci'.
- **Example 3:** Concatenates `emp_id`, `fname`, and `desig` columns from the `employees` table with ':' as the separator. Each record is formatted as `<emp_id>:<fname>:<desig>`.
