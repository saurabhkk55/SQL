# `DATE_FORMAT` Function

`DATE_FORMAT` is used to format a date as specified by the format string. 

**Syntax:**
```sql
DATE_FORMAT(date, format)
```

## `Example`:
```sql
SELECT DATE_FORMAT('2024-05-17', '%W, %M %d, %Y') AS formatted_date;
```

**Output:**
```
+---------------------------+
| formatted_date            |
+---------------------------+
| Friday, May 17, 2024      |
+---------------------------+
```

**Common Format Specifiers:**
- `%W` - Weekday name (Sunday..Saturday)
- `%M` - Month name (January..December)
- `%d` - Day of the month (00..31)
- `%Y` - Year (four digits)

**Here are some additional useful format specifiers for `DATE_FORMAT`**:

- `%b` - Abbreviated month name (Jan..Dec)
- `%c` - Month, numeric (0..12)
- `%e` - Day of the month (0..31)
- `%H` - Hour (00..23)
- `%i` - Minutes, numeric (00..59)
- `%s` - Seconds (00..59)

## `Example`:
```sql
SELECT DATE_FORMAT('2024-05-17 14:35:20', '%b %e, %Y at %H:%i:%s') AS formatted_datetime;
```

**Output:**
```
+--------------------------+
| formatted_datetime       |
+--------------------------+
| May 17, 2024 at 14:35:20 |
+--------------------------+
```
