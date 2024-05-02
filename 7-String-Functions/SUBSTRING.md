# `SUBSTRING` function

- In SQL, the `SUBSTRING` function is flexible and allows you to extract specific parts of a string based on start position and length. 
- Negative start positions can be used to count from the end of the string backwards. 
- This function is useful for manipulating and extracting substrings from data stored in tables or literal strings.

**`Syntax`:**
```sql
SUBSTRING(string_expression, start, length)
```
- `string_expression`: The input string from which to extract the substring.
- `start`: The position within the string where extraction should begin. Positions are 1-based.
- `length` (optional): The length of the substring to be extracted. If not specified, the substring extends to the end of the string.

### `Examples`:

1. **`Extracting a Substring with Specific Start and Length`**
    ```sql
    SELECT SUBSTRING('Hey Buddy', 1, 4);
    ```
    **Output:**
    ```
    Hey 
    ```

2. **`Extracting a Substring with Start and End Positions`**
    ```sql
    SELECT SUBSTRING('Hey Buddy', 5, 9);
    ```
    **Output:**
    ```
    Buddy
    ```

3. **`Extracting Substring from a Start Position to End of String`**
    ```sql
    SELECT SUBSTRING('Hey Buddy', 5);
    ```
    **Output:**
    ```
    Buddy
    ```

4. **`Extracting Last N Characters Using Negative Start Position`**
    ```sql
    SELECT SUBSTRING('Hey Buddy, Wassup Raju', -4);
    ```
    **Output:**
    ```
    Raju
    ```

5. **`Extracting Substring from Column`**
    ```sql
    SELECT SUBSTRING(emp_id, 2) AS EmpID, fname FROM employees;
    ```
    **Output:**
    ```
    EmpID   |   fname
    ---------|---------
    234      |   John
    345      |   Jane
    456      |   Michael
    ``` 

### `Explanation`:
- **`Example 1`:** Extracts the substring 'Hey ' from the string 'Hey Buddy' starting from the 1st character (inclusive) and extracting 4 characters.
- **`Example 2`:** Extracts the substring 'Buddy' from the string 'Hey Buddy' starting from the 5th character (inclusive) and extracting up to the 9th character.
- **`Example 3`:** Extracts the substring 'Buddy' from the string 'Hey Buddy' starting from the 5th character (inclusive) to the end of the string because the length is not explicitly specified.
- **`Example 4`:** Extracts the last 4 characters 'Raju' from the string 'Hey Buddy, Wassup Raju' using a negative start position (-4).
- **`Example 5`:** Extracts a substring from the `emp_id` column of the `employees` table starting from the 2nd character to the end of the string, and aliases it as `EmpID`. The `fname` column is also selected alongside the extracted substring.
