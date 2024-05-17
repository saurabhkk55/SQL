# `DATE`, `TIME` Functions

MySQL provides several functions for extracting specific date, time, month, year, minute, etc components from datetime values. Here are some commonly used functions:

- **`DAYNAME(date)`:** Returns the name of the day for a given date.
- **`DAYOFMONTH(date)`:** Returns the day of the month for a given date.
- **`DAYOFWEEK(date)`:** Returns the day of the week for a given date (1 = Sunday, 2 = Monday, ..., 7 = Saturday).
- **`MONTHNAME(date)`:** Returns the name of the month for a given date.
- **`YEAR(date)`:** Returns the year for a given date.
- **`HOUR(time)`:** Returns the hour for a given time.
- **`MINUTE(time)`:** Returns the minute for a given time.

## `Examples`:
```sql
SELECT DAYNAME('2024-05-17');
SELECT DAYOFMONTH('2024-05-17');
SELECT DAYOFWEEK('2024-05-17');
SELECT DAYNAME(CURDATE());
SELECT MONTHNAME(CURDATE());
SELECT YEAR(CURDATE());
SELECT HOUR(CURTIME());
SELECT MINUTE(CURTIME());
```

```sql
SELECT DAYNAME('2024-05-17');

-- Output
+-----------------------+
| DAYNAME('2024-05-17') |
+-----------------------+
| Friday                |
+-----------------------+
1 row in set (0.00 sec)
```

```sql
SELECT DAYOFMONTH('2024-05-17');

-- Output
+--------------------------+
| DAYOFMONTH('2024-05-17') |
+--------------------------+
|                       17 |
+--------------------------+
1 row in set (0.00 sec)
```

```sql
SELECT DAYOFWEEK('2024-05-17');

-- Output
+-------------------------+
| DAYOFWEEK('2024-05-17') |
+-------------------------+
|                       6 |
+-------------------------+
1 row in set (0.00 sec)
```


```sql
SELECT DAYNAME(CURDATE());

-- output
+--------------------+
| DAYNAME(CURDATE()) |
+--------------------+
| Friday             |
+--------------------+
1 row in set (0.00 sec)
```

```sql
SELECT MONTHNAME(CURDATE());

-- Output
+----------------------+
| MONTHNAME(CURDATE()) |
+----------------------+
| May                  |
+----------------------+
1 row in set (0.00 sec)
```

```sql
SELECT YEAR(CURDATE());

-- Output
+-----------------+
| YEAR(CURDATE()) |
+-----------------+
|            2024 |
+-----------------+
1 row in set (0.00 sec)
```

```sql
SELECT HOUR(CURTIME());

-- Output
+-----------------+
| HOUR(CURTIME()) |
+-----------------+
|              17 |
+-----------------+
1 row in set (0.00 sec)
```

```sql
SELECT MINUTE(CURTIME());

-- Output
+-------------------+
| MINUTE(CURTIME()) |
+-------------------+
|                28 |
+-------------------+
1 row in set (0.00 sec)
```

```sql
SELECT joining_date, MONTHNAME(joining_date) FROM person;

-- Output
+--------------+-------------------------+
| joining_date | MONTHNAME(joining_date) |
+--------------+-------------------------+
| 2024-05-17   | May                     |
| 2024-05-17   | May                     |
| 2024-05-17   | May                     |
+--------------+-------------------------+
3 rows in set (0.00 sec)
```


```sql
SELECT joining_date, YEAR(joining_date) FROM person;

-- Output
+--------------+--------------------+
| joining_date | YEAR(joining_date) |
+--------------+--------------------+
| 2024-05-17   |               2024 |
| 2024-05-17   |               2024 |
| 2024-05-17   |               2024 |
+--------------+--------------------+
3 rows in set (0.00 sec)
```
