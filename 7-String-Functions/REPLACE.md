# `REPLACE` function
The `REPLACE` function in SQL is used to replace all occurrences of a substring (from_string) with another substring (to_string) within original string (original_string).

**`Syntax`:**
```sql
REPLACE(original_string, from_string, to_string)
```
- `original_string`: The input string where replacements will be made.
- `from_string`: The substring to be replaced.
- `to_string`: The substring that will replace occurrences of `from_string`.

### `Examples`:

1. **`Replacing a Substring in a String`**
    ```sql
    SELECT REPLACE('Hey Buddy', 'Hey', 'Hello');
    ```
    **Output:**
    ```
    Hello Buddy
    ```

2. **`Replacing a Substring in a String`**
    ```sql
    SELECT REPLACE('ABCDPQR', 'PQR', 'XYZ');
    ```
    **Output:**
    ```
    ABCDXYZ
    ```

3. **`Replacing a Numeric Value with Another Numeric Value`**
    ```sql
    SELECT REPLACE(emp_id, 10, 999) AS NewEmpID, fname FROM employees;
    ```
    **Output:**
    ```
    NewEmpID   |   fname
    -----------|-----------
    239994     |   John
    349995     |   Jane
    459996     |   Michael
    ```

4. **`Replacing a Numeric Value with a String`**
    ```sql
    SELECT REPLACE(emp_id, 10, 'EMP') AS IDs, fname FROM employees;
    ```
    **Output:**
    ```
    IDs        |   fname
    -----------|---------
    23EMP4     |   John
    34EMP5     |   Jane
    45EMP6     |   Michael
    ```

### `Explanation`:
- **`Example 1`:** Replaces the substring 'Hey' with 'Hello' in the string 'Hey Buddy', resulting in 'Hello Buddy'.
- **`Example 2`:** Replaces the substring 'PQR' with 'XYZ' in the string 'ABCDPQR', resulting in 'ABCDXYZ'.
- **`Example 3`:** Replaces occurrences of the number 10 (presumably in `emp_id` column) with 999, and aliases the result as `NewEmpID`. This example assumes `emp_id` is a string column (as numeric columns typically do not support replacement).
- **`Example 4`:** Replaces occurrences of the number 10 with the string 'EMP' in the `emp_id` column, and aliases the result as `IDs`. This example again assumes `emp_id` is a string column.
