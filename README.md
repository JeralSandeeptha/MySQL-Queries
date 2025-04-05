# SQL

## Table of Contents

- [Basic Keywords](#basic-keywords)
- [Data Types](#data-types)
- [With Databases](#with-databases)
- [With Tables](#with-tables)
- [Table Constraints](#table-constraints)
- [CRUD Operations](#crud-operations)
- [Relationships](#relationships)
- [Functions](#Functions)
- [Joins](#Joins) 

## Basic Keywords

- `WHERE` - for logic
- `ASC` vs `DESC` - for ascending and descending
- `LIMIT` - can select specific number of records
- `IN` - To select multiple records shorthand
- `BETWEEN` - to select records between two points
- `LIKE` - for search
- `AND` - all the logics must be true 
- `OR` - at least one logic must be true
- `FROM` - get data from a specific something

## Data Types

String Data Types

- `CHAR` - 	A FIXED length string (can contain letters, numbers, and special characters). The size parameter specifies the column length in characters - can be from 0 to 255. Default is 1
- `VARCHAR` - A VARIABLE length string (can contain letters, numbers, and special characters). The size parameter specifies the maximum column length in characters - can be from 0 to 65535
- `TEXT` - Holds a string with a maximum length of 65,535 bytes
- `BLOB` - For BLOBs (Binary Large OBjects). Holds up to 65,535 bytes of data
- `LONGTEXT` - Holds a string with a maximum length of 4,294,967,295 characters
- `LONGBLOB` - For BLOBs (Binary Large OBjects). Holds up to 4,294,967,295 bytes of data

Numeric Data Types
- `TINYINT` - A very small integer. Signed range: `-128 to 127`. Unsigned range: `0 to 255`. The `size` parameter specifies the maximum display width (up to 255).
- `INT` - A medium integer. Signed range: `-2,147,483,648` to `2,147,483,647`. Unsigned range: `0 to 4,294,967,295`. The `size` parameter specifies the maximum display width (up to 255).
- `FLOAT` - A floating point number. The total number of digits is specified in size. The number of digits after the decimal point is specified in d. Deprecated in MySQL 8.0.17 and will be removed in future versions.
- `DOUBLE` - A normal-size floating point number. The total number of digits is specified in size, and the number of digits after the decimal point is specified in d.
- `BOOLEAN` - Zero is considered `false`, nonzero values are considered `true`.

Date and Time Data Types

- `DATE` - 	A Date / YYYY-MM-DD / The supported range is from '1000-01-01' to '9999-12-31'
- `DATETIME` - A Date and Time combination. / YYYY-MM-DD hh:mm:ss / The supported range is from '1000-01-01 00:00:00' to '9999-12-31 23:59:59' / 
- `TIMESTAMP` - A Timestamp / YYYY-MM-DD hh:mm:ss / The supported range is from '1970-01-01 00:00:01' UTC to '2038-01-09 03:14:07' UTC
- `TIME` - A Time. / hh:mm:ss / The supported range is from '-838:59:59' to '838:59:59'
- `YEAR` - Year in four-digit format / 1901 to 2155, and 0000.

## With Databases

- Create Database
```sql
CREATE DATABASE Bootcamp;
```

- Create a Database if not exist
```sql
CREATE DATABASE IF NOT EXIST Bootcamp;
```

- Get all Databases
```sql
SHOW DATABASES;
```

-  Select a Database
```sql
USE Bootcamp;
```

-  Drop a Database
```sql
DROP DATABASE Bootcamp;
```

## With Tables

- Get all tables
``sql
SHOW TABLES;
```

- Create a table
```sql
CREATE TABLE student (
name VARCHAR(45) 
age INT
);
```

- Create a table if not exist
```sql
CREATE TABLE IF NOT EXIST student (
name VARCHAR(45) 
age INT
);
```

- Get a description about a table
```sql
DESCRIBE student;
DESC student;
```

## Table Constraints

SQL constraints are used to specify rules for the data in a table. Limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted. 

Constraints can be column level or table level. Column level constraints apply to a column, and table level constraints apply to the whole table.

- `NOT NULL` - Ensures that a column cannot have a NULL value
- `UNIQUE` - Ensures that all values in a column are different
- `PRIMARY KEY` - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
- `FOREIGN KEY` - Prevents actions that would destroy links between tables
- `CHECK` - Ensures that the values in a column satisfies a specific condition
- `DEFAULT` - Sets a default value for a column if no value is specified
- `CREATE INDEX` - Used to create and retrieve data from the database very quickly

## CRUD Operations

- Create Records
```sql
INSERT INTO student ( name, age) VALUES ( ‘Nimal’, ‘17’ );

INSERT INTO student VALUES ( ‘Bandara’, ‘17 );

INSERT INTO student VALUES ( ‘Bandara’, ‘17 ), ( Saman, ‘12’ ), ( Jeral, ‘22’ );

CREATE TABLE IF NOT EXIST student (
name VARCHAR(45),
age INT,
Nic VARCHAR(15) PRIMARY KEY
);
```

- Read Records
```sql
SELECT name FROM student;

SELECT name, age FROM student;  //select by specific columns

SELECT * FROM student;      //select all columns

SELECT * FROM student LIMIT 2;                        //Limit

SELECT * FROM student ORDER BY age DESC;          //Descending Order

SELECT * FROM student ORDER BY age ASC;            //Ascending Order

SELECT * FROM student ORDER BY name ASC, age DESC;    //select by order
//first try to name, if can’t then use age

SELECT * FROM student WHERE name=’Kamal’;  //select by specific column

SELECT * FROM student WHERE name LIKE ‘%l’;       //LIKE(search)

SELECT * FROM student WHERE BETWEEN age>= 18 AND 30;    //BETWEEN

SELECT * FROM student WHERE id IN (1,2,3,4,5);           //IN

SELECT * FROM student WHERE name=’Kamal’ AND age=’12’;
//select by specific two logics

SELECT * FROM student WHERE name=’Kamal’ OR age=’12’;
//select by specific two logics

SELECT name AS student_name FROM student; 		//Alias

SELECT age AS `student age` FROM student; 		//Alias

SELECT age+3 AS `after three years` FROM student;
//get records and modify it
```

- Update Records
```sql
UPDATE student SET name=’Kamal’;      //don’t do like this

UPDATE student SET name=’Kamal’ WHERE nic=’200015003010’; 
```

- Delete Records
```sql
DELETE FROM student;     		   //don’t do like this

DELETE student SET name=’Kamal’ WHERE nic=’200015003010’;
```

## Relationships

A relationship in SQL defines how tables connect based on keys (Primary Key and Foreign Key). Relationships help maintain data integrity and prevent duplication.

1. One-to-One (1:1) - Each row in Table A is related to one row in Table B.

```sql
CREATE TABLE Users (
    UserID INT PRIMARY KEY,
    UserName VARCHAR(100) NOT NULL
);

CREATE TABLE Profiles (
    ProfileID INT PRIMARY KEY,
    UserID INT UNIQUE,  -- Ensures one-to-one relationship
    Bio TEXT,
    FOREIGN KEY (UserID) REFERENCES Users(UserID) ON DELETE CASCADE
);
```

✔ The `UserID` in `Profiles` is unique, ensuring only one profile per user.
✔ `ON DELETE CASCADE` ensures that if a user is deleted, their profile is also deleted.

2. One-to-Many (1:M) – Each row in Table A can be related to multiple rows in Table B, but each row in Table B is related to only one row in Table A.

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE NOT NULL,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID) ON DELETE CASCADE
);
```

✔ The `CustomerID` in `Orders` is a Foreign Key, linking it to Customers.
✔ One customer can have multiple orders, but each order belongs to only one customer.

3. Many-to-Many (M:M) – Multiple rows in Table A relate to multiple rows in Table B using a junction table.

```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    StudentName VARCHAR(100) NOT NULL
);

CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(100) NOT NULL
);

-- Junction Table (Bridges Many-to-Many Relationship)
CREATE TABLE StudentCourses (
    StudentID INT,
    CourseID INT,
    PRIMARY KEY (StudentID, CourseID),
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID) ON DELETE CASCADE,
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID) ON DELETE CASCADE
);
```

✔ `StudentCourses` bridges the relationship between `Students` and `Courses`.
✔ It uses a composite primary key (`StudentID`, `CourseID`).
✔ A student can enroll in multiple courses, and a course can have multiple students.

## Functions

In SQL Functions we have 2 types of functions
- Predefined Functions
- User defined Functions

**Predefined Functions**

- `AVG()` - Get Average Value
```sql
SELECT AVG(salary) FROM student;  
```

- `SUM()` - Get all the additions of data
```sql
SELECT SUM(salary) FROM student;    
```

- `MAX()` - Get max value
```sql
SELECT MAX(salary) FROM student; 
```

- `MIN()` - Get min value
```sql
SELECT MIN(salary) FROM student; 
```

- `COUNT()` - To get unique data / without repeat data
```sql
SELECT COUNT(id) FROM student;

SELECT COUNT(DISTINCT city) FROM student; 
```

- `VERSION()` - Give version
```sql
SELECT VERSION;
```

- `NOW()` - Give today date
```sql
SELECT NOW;
```

**User Defiened Functions**

✔ Cannot modify database state (No INSERT, UPDATE, DELETE, or EXEC statements).
✔ Deterministic (Same input always returns the same output).
✔ Can be used in SELECT, WHERE, and JOIN clauses.

Scalar Functions – Returns a single value.

```sql
CREATE FUNCTION GetFullName(@FirstName VARCHAR(50), @LastName VARCHAR(50))
RETURNS VARCHAR(100)
AS
BEGIN
    RETURN @FirstName + ' ' + @LastName
END;
```

```sql
SELECT dbo.GetFullName('John', 'Doe') AS FullName;
```

Table-Valued Functions – Returns a table.

```sql
CREATE FUNCTION GetActiveUsers()
RETURNS TABLE
AS
RETURN
(
    SELECT Id, Name, Email
    FROM Users
    WHERE IsActive = 1
);
```

```sql
SELECT * FROM dbo.GetActiveUsers();
```

## Joins

1. INNER JOIN – Returns only matching rows from both tables.

- Returns only the matching rows from both tables based on a common column.
```sql
SELECT Customers.CustomerID, Customers.Name, Orders.OrderID, Orders.Product
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

2. LEFT JOIN (LEFT OUTER JOIN) – Returns all rows from the left table and matching rows from the right table. If no match, NULLs are returned.

- Returns all rows from the left table and matching rows from the right table. If no match is found, NULLs are returned for right table columns.
```sql
SELECT Customers.CustomerID, Customers.Name, Orders.OrderID, Orders.Product
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

3. RIGHT JOIN (RIGHT OUTER JOIN) – Returns all rows from the right table and matching rows from the left table. If no match, NULLs are returned.

- Returns all rows from the right table and matching rows from the left table. If no match is found, NULLs are returned for left table columns.
```sql
SELECT Customers.CustomerID, Customers.Name, Orders.OrderID, Orders.Product
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

4. FULL JOIN (FULL OUTER JOIN) – Returns all rows from both tables. If there’s no match, NULLs are returned in columns from the missing table.

- Returns all rows from both tables, with NULLs where there is no match.
```sql
SELECT Customers.CustomerID, Customers.Name, Orders.OrderID, Orders.Product
FROM Customers
FULL JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```