# SQL

## Table of Contents

- [Basic Keywords](#basic-keywords)
- [Data Types](#data-types)
- [With Databases](#with-databases)
- [With Tables](#with-tables)
- [Table Constraints](#table-constraints)

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
```cmd
CREATE DATABASE Bootcamp;
```

- Create a Database if not exist
```cmd
CREATE DATABASE IF NOT EXIST Bootcamp;
```

- Get all Databases
```cmd
SHOW DATABASES;
```

-  Select a Database
```cmd
USE Bootcamp;
```

-  Drop a Database
```cmd
DROP DATABASE Bootcamp;
```

## With Tables

- Get all tables
``cmd
SHOW TABLES;
```

- Create a table
```cmd
CREATE TABLE student (
name VARCHAR(45) 
age INT
);
```

- Create a table if not exist
```cmd
CREATE TABLE IF NOT EXIST student (
name VARCHAR(45) 
age INT
);
```

- Get a description about a table
```cmd
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