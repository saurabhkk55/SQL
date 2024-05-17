# `Mathematical operations on dates`

- In MySQL, various mathematical operations can be performed on dates to manipulate and calculate date and time values. 
- These operations include adding or subtracting intervals, calculating differences between dates, and extracting specific components of date values. 
- Here are some commonly used functions and operations:

### 1. `ADDDATE / DATE_ADD`

**`ADDDATE`** or **`DATE_ADD`** is used to add an interval to a date.

**Syntax:**
```sql
ADDDATE(date, INTERVAL expr unit);
DATE_ADD(date, INTERVAL expr unit);
```

**Example:**
```sql
SELECT ADDDATE('2024-05-17', INTERVAL 10 DAY) AS new_date;
SELECT DATE_ADD('2024-05-17', INTERVAL 2 MONTH) AS new_date;
```

**Output:**
```
+------------+
| new_date   |
+------------+
| 2024-05-27 |
+------------+

+------------+
| new_date   |
+------------+
| 2024-07-17 |
+------------+
```

### 2. `SUBDATE / DATE_SUB`

**`SUBDATE`** or **`DATE_SUB`** is used to subtract an interval from a date.

**Syntax:**
```sql
SUBDATE(date, INTERVAL expr unit);
DATE_SUB(date, INTERVAL expr unit);
```

**Example:**
```sql
SELECT SUBDATE('2024-05-17', INTERVAL 10 DAY) AS new_date;
SELECT DATE_SUB('2024-05-17', INTERVAL 2 MONTH) AS new_date;
```

**Output:**
```
+------------+
| new_date   |
+------------+
| 2024-05-07 |
+------------+

+------------+
| new_date   |
+------------+
| 2024-03-17 |
+------------+
```

### 3. `DATEDIFF`

**`DATEDIFF`** returns the number of days between two dates.

**Syntax:**
```sql
DATEDIFF(date1, date2);
```

**Example:**
```sql
SELECT DATEDIFF('2024-05-17', '2024-04-17') AS days_difference;
```

**Output:**
```
+-----------------+
| days_difference |
+-----------------+
|              30 |
+-----------------+
```

### 4. `TIMESTAMPDIFF`

**`TIMESTAMPDIFF`** returns the difference between two dates or datetimes in the specified unit.

**Syntax:**
```sql
TIMESTAMPDIFF(unit, datetime_expr1, datetime_expr2);
```

**Example:**
```sql
SELECT TIMESTAMPDIFF(MONTH, '2024-01-01', '2024-05-17') AS months_difference;
```

**Output:**
```
+--------------------+
| months_difference  |
+--------------------+
|                  4 |
+--------------------+
```

### 5. `EXTRACT`

**`EXTRACT`** is used to extract a part of a date or datetime value.

**Syntax:**
```sql
EXTRACT(unit FROM date);
```

**Example:**
```sql
SELECT EXTRACT(YEAR FROM '2024-05-17') AS year_part,
       EXTRACT(MONTH FROM '2024-05-17') AS month_part,
       EXTRACT(DAY FROM '2024-05-17') AS day_part;
```

**Output:**
```
+-----------+------------+----------+
| year_part | month_part | day_part |
+-----------+------------+----------+
|      2024 |          5 |       17 |
+-----------+------------+----------+
```

### 6. `DATE_ADD` and `DATE_SUB` with Various Units

You can use various units like `SECOND`, `MINUTE`, `HOUR`, `DAY`, `WEEK`, `MONTH`, `QUARTER`, and `YEAR`.

**Example:**
```sql
SELECT DATE_ADD('2024-05-17', INTERVAL 15 MINUTE) AS new_datetime;
SELECT DATE_SUB('2024-05-17', INTERVAL 1 WEEK) AS new_date;
```

**Output:**
```
+---------------------+
| new_datetime        |
+---------------------+
| 2024-05-17 00:15:00 |
+---------------------+

+------------+
| new_date   |
+------------+
| 2024-05-10 |
+------------+
```

### 7. `LAST_DAY`

**`LAST_DAY`** returns the last day of the month for a given date.

**Syntax:**
```sql
LAST_DAY(date)
```

**Example:**
```sql
SELECT LAST_DAY('2024-05-17') AS last_day_of_month;
```

**Output:**
```
+--------------------+
| last_day_of_month  |
+--------------------+
| 2024-05-31         |
+--------------------+
```
