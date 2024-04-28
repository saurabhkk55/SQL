# `Databases`

## `List Existing Databases`
To see a list of all existing databases in your MySQL server:
```sql
SHOW DATABASES;
```

## `Create a New Database`
To create a new database:
```sql
CREATE DATABASE <db_name>;
```

## `Switching Databases`
To work with a specific database:
```sql
USE <db_name>;
```

## `Verify Current Database`
To verify the current database you're working in:
```sql
SELECT DATABASE();
```

## `Deleting a Database`
To delete a database (be careful, as this action permanently removes the database and its contents):
```sql
DROP DATABASE <db_name>;
```

