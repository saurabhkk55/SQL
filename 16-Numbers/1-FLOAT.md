# `Float`:
- Stores decimal number
- Size: **4 byte** (Occupies less space as compared to Double & Decimal)
- Can **store upto 6 digits in total** (with or without the decimal).
- Real world example:
  - Product price
  - Temperature

## `Practical`:

```sql
--- Create a table
create table float_test(
	column_1 float
);

-- INSERT into table
insert into float_test (column_float) values(20.55);
insert into float_test (column_float) values(-20.55);
insert into float_test (column_float) values(-20.5678912345);
--- If inserted digits are more than 6 then round off will be done upto 6 digits only.

--- View the table
select * from float_test;

+--------------+
| column_float |
+--------------+
|    20.55     |
|   -20.55     |
| -20.5679     |
+--------------+
```
