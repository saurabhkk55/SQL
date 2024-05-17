# MySQL `DATE`, `TIME`, and `DATETIME` Data Types

- **DATE** format: `yyyy-mm-dd`
- **TIME** format: `HH:MM:SS`
- **DATETIME** format: `yyyy-mm-dd HH:MM:SS`

## 1. `Table Creation`

First, we create a table named `person` with columns for `joining_date`, `joining_time`, and `joining_datetime`.

```sql
CREATE TABLE person (
    joining_date DATE,
    joining_time TIME,
    Joining_datetime DATETIME
);
```

**Output:**
```plaintext
Query OK, 0 rows affected (0.10 sec)
```

## 2. `Describing the Table`

Next, we describe the structure of the `person` table to verify its schema.

```sql
DESC person;
```

**Output:**
```sql
+------------------+----------+------+-----+---------+-------+
| Field            | Type     | Null | Key | Default | Extra |
+------------------+----------+------+-----+---------+-------+
| joining_date     | date     | YES  |     | NULL    |       |
| joining_time     | time     | YES  |     | NULL    |       |
| Joining_datetime | datetime | YES  |     | NULL    |       |
+------------------+----------+------+-----+---------+-------+
3 rows in set (0.01 sec)
```

## 3. `Inserting Records`

### Correct Format

We insert a record with correct date and time formats.

```sql
INSERT INTO person VALUES ('2024-05-17', '16:00:00', '2023-05-17 15:00:00');
```

**Output:**
```plaintext
Query OK, 1 row affected (0.17 sec)
```

### 4. `Selecting Records`

We select all records from the `person` table.

```sql
SELECT * FROM person;
```

**Output:**
```sql
+--------------+--------------+---------------------+
| joining_date | joining_time | Joining_datetime    |
+--------------+--------------+---------------------+
| 2024-05-17   | 16:00:00     | 2023-05-17 15:00:00 |
+--------------+--------------+---------------------+
1 row in set (0.00 sec)
```

### 5. `Incorrect Date Format`

We insert a record with an incorrect date format (`yyyy:mm:dd` instead of `yyyy-mm-dd`). MySQL gives a warning but corrects the format.

```sql
INSERT INTO person VALUES ('2024:05:17', '16:00:00', '2023-05-17 15:00:00');
```

**Output:**
```plaintext
Query OK, 1 row affected, 1 warning (0.01 sec)
```

### 6. `Selecting Records Again`

We select all records from the `person` table to observe the correction.

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
+--------------+--------------+---------------------+
2 rows in set (0.00 sec)
```

## `Summary`

- MySQL allows flexible date and time formats but standard formats should be used.
- Incorrect formats may be auto-corrected by MySQL, generating warnings.
- Always verify the inserted data to ensure accuracy.
