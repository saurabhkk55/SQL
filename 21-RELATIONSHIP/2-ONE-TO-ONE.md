# `One-to-one relationship`

Practical example of a one-to-one relationship in SQL. We'll use a scenario where each employee has one associated personal detail record.

### Step 1: `Create the Database`

First, we'll create a database to work in.

```sql
CREATE DATABASE CompanyDB;
USE CompanyDB;
```

### Step 2: `Create the Tables`

Next, we'll create the `Employees` table and the `PersonalDetails` table.

```sql
-- Create Employees Table
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);

-- Create PersonalDetails Table
CREATE TABLE PersonalDetails (
    PersonalDetailID INT PRIMARY KEY,
    EmployeeID INT UNIQUE,
    Address VARCHAR(255),
    PhoneNumber VARCHAR(20),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

### Step 3: `Insert Data into the Tables`

Now, let's insert some sample data into the `Employees` and `PersonalDetails` tables.

```sql
-- Insert data into Employees table
INSERT INTO Employees (EmployeeID, FirstName, LastName)
VALUES (1, 'John', 'Doe'),
       (2, 'Jane', 'Smith');

-- Insert data into PersonalDetails table
INSERT INTO PersonalDetails (PersonalDetailID, EmployeeID, Address, PhoneNumber)
VALUES (1, 1, '123 Main St, Anytown, USA', '123-456-7890'),
       (2, 2, '456 Maple Ave, Othertown, USA', '987-654-3210');
```

### Step 4: `Query the Tables`

Let's query the tables to see the data we've inserted.

```sql
-- Query Employees table
SELECT * FROM Employees;

-- Query PersonalDetails table
SELECT * FROM PersonalDetails;
```

**Expected Output:**

For `Employees` table:

| EmployeeID | FirstName | LastName |
|------------|-----------|----------|
| 1          | John      | Doe      |
| 2          | Jane      | Smith    |

For `PersonalDetails` table:

| PersonalDetailID | EmployeeID | Address                    | PhoneNumber  |
|------------------|------------|----------------------------|--------------|
| 1                | 1          | 123 Main St, Anytown, USA  | 123-456-7890 |
| 2                | 2          | 456 Maple Ave, Othertown, USA | 987-654-3210 |

### Step 5: `Query with a Join`

To see the one-to-one relationship in action, we'll join the `Employees` table with the `PersonalDetails` table.

```sql
-- Join Employees and PersonalDetails tables
SELECT e.EmployeeID, e.FirstName, e.LastName, p.Address, p.PhoneNumber
FROM Employees e
JOIN PersonalDetails p ON e.EmployeeID = p.EmployeeID;
```

**Expected Output:**

| EmployeeID | FirstName | LastName | Address                    | PhoneNumber  |
|------------|-----------|----------|----------------------------|--------------|
| 1          | John      | Doe      | 123 Main St, Anytown, USA  | 123-456-7890 |
| 2          | Jane      | Smith    | 456 Maple Ave, Othertown, USA | 987-654-3210 |

### Step 6: `Update and Delete Operations`

Let's perform some update and delete operations to further illustrate the one-to-one relationship.

**Update Operation:**

```sql
-- Update the address for John Doe
UPDATE PersonalDetails
SET Address = '789 Oak St, Newcity, USA'
WHERE EmployeeID = 1;

-- Query to see the update
SELECT e.EmployeeID, e.FirstName, e.LastName, p.Address, p.PhoneNumber
FROM Employees e
JOIN PersonalDetails p ON e.EmployeeID = p.EmployeeID;
```

**Expected Output after Update:**

| EmployeeID | FirstName | LastName | Address                    | PhoneNumber  |
|------------|-----------|----------|----------------------------|--------------|
| 1          | John      | Doe      | 789 Oak St, Newcity, USA   | 123-456-7890 |
| 2          | Jane      | Smith    | 456 Maple Ave, Othertown, USA | 987-654-3210 |

**Delete Operation:**

```sql
-- Delete the personal detail for Jane Smith
DELETE FROM PersonalDetails
WHERE EmployeeID = 2;

-- Query to see the delete
SELECT e.EmployeeID, e.FirstName, e.LastName, p.Address, p.PhoneNumber
FROM Employees e
LEFT JOIN PersonalDetails p ON e.EmployeeID = p.EmployeeID;
```

**Expected Output after Delete:**

| EmployeeID | FirstName | LastName | Address                    | PhoneNumber  |
|------------|-----------|----------|----------------------------|--------------|
| 1          | John      | Doe      | 789 Oak St, Newcity, USA   | 123-456-7890 |
| 2          | Jane      | Smith    | NULL                       | NULL         |

This practical example demonstrates how to create, populate, and manipulate tables with a one-to-one relationship in SQL.

## `Potential Failure Cases`

#### 1. Inserting a `PersonalDetails` Record with a Non-Existent `EmployeeID`

If you try to insert a record into the `PersonalDetails` table with an `EmployeeID` that doesn't exist in the `Employees` table, it will fail due to the foreign key constraint.

**Example:**

```sql
-- Attempt to insert a PersonalDetail with a non-existent EmployeeID
INSERT INTO PersonalDetails (PersonalDetailID, EmployeeID, Address, PhoneNumber)
VALUES (3, 3, '789 Pine St, Sometown, USA', '555-555-5555');
```

**Error:**

```
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`CompanyDB`.`PersonalDetails`, CONSTRAINT `PersonalDetails_ibfk_1` FOREIGN KEY (`EmployeeID`) REFERENCES `Employees` (`EmployeeID`))
```

#### 2. Inserting a Duplicate `EmployeeID` in `PersonalDetails`

The `EmployeeID` column in `PersonalDetails` has a `UNIQUE` constraint to ensure the one-to-one relationship. If you try to insert a record with an `EmployeeID` that already exists in the `PersonalDetails` table, it will fail due to the unique constraint.

**Example:**

```sql
-- Attempt to insert a PersonalDetail with an existing EmployeeID
INSERT INTO PersonalDetails (PersonalDetailID, EmployeeID, Address, PhoneNumber)
VALUES (3, 1, '789 Pine St, Sometown, USA', '555-555-5555');
```

**Error:**

```
ERROR 1062 (23000): Duplicate entry '1' for key 'PersonalDetails.EmployeeID'
```

#### 3. Inserting a `NULL` in a `NOT NULL` Column

If any column in the `PersonalDetails` table (or `Employees` table) is defined with a `NOT NULL` constraint and you attempt to insert a `NULL` value, it will fail.

**Example:**

```sql
-- Attempt to insert a PersonalDetail with a NULL Address
INSERT INTO PersonalDetails (PersonalDetailID, EmployeeID, Address, PhoneNumber)
VALUES (3, 1, NULL, '555-555-5555');
```

**Error:**

```
ERROR 1048 (23000): Column 'Address' cannot be null
```

### Summary of Constraints and Potential Failures

1. **Foreign Key Constraint Violation:**
    - **Cause:** Inserting a `PersonalDetails` record with an `EmployeeID` that does not exist in the `Employees` table.
    - **Error Message:** `Cannot add or update a child row: a foreign key constraint fails`

2. **Unique Constraint Violation:**
    - **Cause:** Inserting a `PersonalDetails` record with an `EmployeeID` that already exists in the `PersonalDetails` table.
    - **Error Message:** `Duplicate entry for key 'PersonalDetails.EmployeeID'`

3. **NOT NULL Constraint Violation:**
    - **Cause:** Inserting a `NULL` value into a column defined as `NOT NULL`.
    - **Error Message:** `Column 'ColumnName' cannot be null`
