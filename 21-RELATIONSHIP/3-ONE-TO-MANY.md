# `One-to-Many (1:N)`

Let's walk through a practical example of a One-to-Many (1:N) relationship in SQL. We will cover the following steps:

1. **Setting up the database and tables**
2. **Inserting data**
3. **Querying data**
4. **Demonstrating failure cases**

We'll use a scenario where we have two tables: `Authors` and `Books`. One author can write multiple books, but each book has only one author.

## Step 1: `Setting up the Database and Tables`

First, create the database and the two tables:

```sql
CREATE DATABASE Library;

USE Library;

CREATE TABLE Authors (
    AuthorID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL
);

CREATE TABLE Books (
    BookID INT PRIMARY KEY AUTO_INCREMENT,
    Title VARCHAR(100) NOT NULL,
    AuthorID INT,
    FOREIGN KEY (AuthorID) REFERENCES Authors(AuthorID)
);
```

## Step 2: `Inserting Data`

Insert some data into the `Authors` and `Books` tables:

```sql
-- Insert data into Authors
INSERT INTO Authors (Name) 
VALUES
('J.K. Rowling'), ('George R.R. Martin'), ('J.R.R. Tolkien');

-- Insert data into Books
INSERT INTO Books (Title, AuthorID) 
VALUES 
('Harry Potter and the Philosopher\'s Stone', 1), 
('Harry Potter and the Chamber of Secrets', 1),
('A Game of Thrones', 2), 
('A Clash of Kings', 2),
('The Hobbit', 3), 
('The Lord of the Rings', 3);
```

## Step 3: `Querying Data`

Retrieve data to show the One-to-Many relationship:

```sql
-- Join Authors and Books to see the relationship
SELECT Authors.Name, Books.Title 
FROM Authors
JOIN Books ON Authors.AuthorID = Books.AuthorID
ORDER BY Authors.Name;
```

This query will display the authors along with their respective books.

## Step 4: `Demonstrating Failure Cases`

#### 4.1. Inserting a Book with a Non-existent Author

Attempt to insert a book with an `AuthorID` that doesn't exist in the `Authors` table:

```sql
-- Attempt to insert a book with an invalid AuthorID
INSERT INTO Books (Title, AuthorID) VALUES ('Non-existent Author Book', 99);
```

This will fail with an error due to the foreign key constraint:

```sql
Error Code: 1452. Cannot add or update a child row: a foreign key constraint fails (`Library`.`Books`, CONSTRAINT `Books_ibfk_1` FOREIGN KEY (`AuthorID`) REFERENCES `Authors` (`AuthorID`))
```

#### 4.2. Deleting an Author who has Books

Attempt to delete an author who has books:

```sql
-- Attempt to delete an author with books
DELETE FROM Authors WHERE AuthorID = 1;
```

This will also fail due to the foreign key constraint:

```sql
Error Code: 1451. Cannot delete or update a parent row: a foreign key constraint fails (`Library`.`Books`, CONSTRAINT `Books_ibfk_1` FOREIGN KEY (`AuthorID`) REFERENCES `Authors` (`AuthorID`))
```
