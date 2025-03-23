# SQL

## Table of Contents

- [Basic Keywords](#basic-keywords)
- [Table Constraints](#table-constraints)
- [With Databases](#with-databases)
- [With Tables](#with-tables)

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