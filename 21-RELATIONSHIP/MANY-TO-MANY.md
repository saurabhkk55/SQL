# `Many-to-Many (M:N) relationship`

## Step 1: `Setting up the Database and Tables`

Run the following SQL commands to set up the database and tables:

```sql
CREATE DATABASE School;

USE School;

CREATE TABLE Students (
    StudentID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL
);

CREATE TABLE Courses (
    CourseID INT PRIMARY KEY AUTO_INCREMENT,
    Title VARCHAR(100) NOT NULL
);

-- Junction table for Many-to-Many relationship
CREATE TABLE Enrollments (
    StudentID INT,
    CourseID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID),
    PRIMARY KEY (StudentID, CourseID)
);
```

## Step 2: `Inserting Data`

Insert data into the `Students`, `Courses`, and `Enrollments` tables:

```sql
-- Insert data into Students
INSERT INTO Students (Name) VALUES ('Alice'), ('Bob'), ('Charlie');

-- Insert data into Courses
INSERT INTO Courses (Title) VALUES ('Math'), ('Science'), ('History');

-- Insert data into Enrollments
INSERT INTO Enrollments (StudentID, CourseID)
VALUES (1, 1), (1, 2), (2, 1), (3, 3), (2, 3);
```

## Step 3: `Querying Data`

Run the following query to retrieve data and show the Many-to-Many relationship:

```sql
-- Join Students and Enrollments to see which students are enrolled in which courses
SELECT Students.Name, Courses.Title 
FROM Students
JOIN Enrollments ON Students.StudentID = Enrollments.StudentID
JOIN Courses ON Enrollments.CourseID = Courses.CourseID
ORDER BY Students.Name;
```

**Expected Output:**

| Name    | Title    |
|---------|----------|
| Alice   | Math     |
| Alice   | Science  |
| Bob     | Math     |
| Bob     | History  |
| Charlie | History  |

## Step 4: `Demonstrating Failure Cases`

### 4.1. `Inserting an Enrollment with a Non-existent Student or Course`

Attempt to insert an enrollment with a `StudentID` or `CourseID` that doesn't exist in the respective tables:

```sql
-- Attempt to insert an enrollment with a non-existent StudentID
INSERT INTO Enrollments (StudentID, CourseID) VALUES (99, 1);
```

**Expected Error:**
```sql
Error Code: 1452. Cannot add or update a child row: a foreign key constraint fails (`School`.`Enrollments`, CONSTRAINT `Enrollments_ibfk_1` FOREIGN KEY (`StudentID`) REFERENCES `Students` (`StudentID`))
```

```sql
-- Attempt to insert an enrollment with a non-existent CourseID
INSERT INTO Enrollments (StudentID, CourseID) VALUES (1, 99);
```

**Expected Error:**
```sql
Error Code: 1452. Cannot add or update a child row: a foreign key constraint fails (`School`.`Enrollments`, CONSTRAINT `Enrollments_ibfk_2` FOREIGN KEY (`CourseID`) REFERENCES `Courses` (`CourseID`))
```

### 4.2. `Deleting a Student or Course Referenced in Enrollments`

Attempt to delete a student or a course that is referenced in the `Enrollments` table:

```sql
-- Attempt to delete a student with enrollments
DELETE FROM Students WHERE StudentID = 1;
```

**Expected Error:**
```sql
Error Code: 1451. Cannot delete or update a parent row: a foreign key constraint fails (`School`.`Enrollments`, CONSTRAINT `Enrollments_ibfk_1` FOREIGN KEY (`StudentID`) REFERENCES `Students` (`StudentID`))
```

```sql
-- Attempt to delete a course with enrollments
DELETE FROM Courses WHERE CourseID = 1;
```

**Expected Error:**
```sql
Error Code: 1451. Cannot delete or update a parent row: a foreign key constraint fails (`School`.`Enrollments`, CONSTRAINT `Enrollments_ibfk_2` FOREIGN KEY (`CourseID`) REFERENCES `Courses` (`CourseID`))
```
