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

Numeric Data Types

- `` - 
- `` - 
- `` - 
- `` - 

Date and Time Data Types

- `DATE` - 	A Date / YYYY-MM-DD / The supported range is from '1000-01-01' to '9999-12-31'
- `DATETIME(fsp)` - A Date and Time combination. / YYYY-MM-DD hh:mm:ss / The supported range is from '1000-01-01 00:00:00' to '9999-12-31 23:59:59' / 
- `TIMESTAMP(fsp)` - A Timestamp / YYYY-MM-DD hh:mm:ss / The supported range is from '1970-01-01 00:00:01' UTC to '2038-01-09 03:14:07' UTC
- `TIME(fsp)` - A Time. / hh:mm:ss / The supported range is from '-838:59:59' to '838:59:59'
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

- 

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