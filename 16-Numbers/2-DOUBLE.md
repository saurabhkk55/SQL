# `DOUBLE`
- Stores decimal number same as Float
- Size: 8 byte (double size than Float)
- Can store upto 17 digits in total (with or without the decimal).
- Real world example: Latitude & Longitude
	-	Latitude: 52.796119005678506
	-	Longitude: -7.811279296875001

```sql
--- Create a table
create table float_test(
	column_1 float
);

-- INSERT into table
insert into double_test (column_1) values(-20.5678912345);
insert into double_test (column_1) values(52.796119005678506);
insert into double_test (column_1) values(0.12345678901234567890);
insert into double_test (column_1) values(1.12345678901234567890); 
--- If inserted digits are more than 17 then round off will be done upto 17 digits only.

--- View the table
select * from double_test;

+---------------------+
| column_1            |
+---------------------+
|      -20.5678912345 |
|  52.796119005678506 |
| 0.12345678901234568 | --- total 17 digits, 0.xxxxx... is same as .xxxxx...
| 1.12345678901234567 | --- total 17 digits
+---------------------+
```
