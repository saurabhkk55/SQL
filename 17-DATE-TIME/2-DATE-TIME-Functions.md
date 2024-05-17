# `DATE`, `TIME` Functions

MySQL provides several functions to work with date and time values. Here are some commonly used functions:

- **CURDATE():** Returns the current date in DATE format `yyyy-mm-dd`.
- **CURTIME():** Returns the current time in TIME format `hh:mm:ss`.
- **NOW():** Returns the current date and time in DATETIME format `yyyy-mm-dd hh:mm:ss`.

## Examples

### 1. Using `CURDATE()`

```sql
SELECT CURDATE();
```

**Output:**
```sql
+------------+
| CURDATE()  |
+------------+
| 2024-05-17 |
+------------+
1 row in set (0.00 sec)
```

### 2. Using `CURTIME()`

```sql
SELECT CURTIME();
```

**Output:**
```sql
+-----------+
| CURTIME() |
+-----------+
| 16:57:54  |
+-----------+
1 row in set (0.00 sec)
```

### 3. Using `NOW()`

```sql
SELECT NOW();
```

**Output:**
```sql
+---------------------+
| NOW()               |
+---------------------+
| 2024-05-17 16:58:08 |
+---------------------+
1 row in set (0.00 sec)
```

## 4. `Inserting Current Date and Time into a Table`

We can use these functions to insert the current date and time into a table.

> Hint: person's table has been created in the file named `1-DATE-TIME-DATETIME.md`

```sql
INSERT INTO person VALUES(CURDATE(), CURTIME(), NOW());
```

**Output:**
```sql
Query OK, 1 row affected (0.01 sec)
```

### `Viewing Table Data`

After inserting a record with the current date and time, we can verify it in the `person` table.

```sql
SELECT * FROM person;
```

**Output:**
```sql
+--------------+--------------+---------------------+
| joining_date | joining_time | Joining_datetime    |
+--------------+--------------+---------------------+
| 2024-05-17   | 16:00:00     | 2023-05-17 15:00:00 |
| 2024-05-17   | 16:00:00     | 2023-05-17 15:00:00 |
| 2024-05-17   | 16:58:34     | 2024-05-17 16:58:34 |
+--------------+--------------+---------------------+
3 rows in set (0.00 sec)
```
