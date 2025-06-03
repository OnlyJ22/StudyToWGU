# SQL Cheatsheet

## Create
Used to create a new database or table:
```sql
CREATE DATABASE <DATABASE NAME>;
CREATE TABLE <TABLE NAME>;
```

## Drop
Used to delete an existing database or table:
```sql
DROP DATABASE <DATABASE NAME>;
DROP TABLE <TABLE NAME>;
```

## Truncate
Used to delete information in the table but doesn’t remove the table itself:
```sql
TRUNCATE TABLE <TABLE NAME>;
```

## Alter
Used to delete, add or modify constraints or columns in a table:
```sql
ALTER TABLE <TABLE NAME>
ADD <COLUMN NAME> <DATA TYPE>;

ALTER TABLE <TABLE NAME>
DROP COLUMN <COLUMN NAME>;

ALTER TABLE <TABLE NAME>
MODIFY <COLUMN NAME> <NEW DATA TYPE>;
```

## Backup
Used to create a backup on an existing database:
```sql
BACKUP DATABASE <DATABASE NAME>
TO DISK = '<PATH>';
```

## Insert
Used to insert new tuples (rows) in a table:
```sql
INSERT INTO <TABLE NAME> (<COLUMNS>,...)
VALUES (<VALUES>,...);
```

## Delete
Used to delete tuples (rows) from a table:
```sql
DELETE FROM <TABLE NAME>
WHERE <CONDITION>;
```

## Update
Used to modify existing records in a table:
```sql
UPDATE <TABLE NAME>
SET <COLUMN NAME> = <NEW VALUE>
WHERE <CONDITION>;
```

## Select
Used to select data from a table:
```sql
SELECT <ATTRIBUTE LIST>
FROM <TABLE NAME>
WHERE <CONDITION>;
```

## Union, Intersect, Except
Equivalent to set operations: union, intersection and difference:
```sql
SELECT <ATTRIBUTE LIST>
FROM <TABLE 1>
UNION / INTERSECT / EXCEPT
SELECT <ATTRIBUTE LIST>
FROM <TABLE 2>;
```

## In
Compares a value with a set of values, returns true if the value is one of the elements of the set:
```sql
SELECT <ATTRIBUTE LIST>
FROM <TABLE NAME>
WHERE <VALUE> IN (<ANOTHER SELECT QUERY>);
```

## Null
Used to check whether a value is NULL:
```sql
<ATTRIBUTE NAME> IS (NOT) NULL;
```

## Join
Used to join two tables based on a related column between them:
```sql
SELECT <ATTRIBUTES LIST>
FROM <TABLE 1> JOIN <TABLE 2>
ON <JOIN CONDITION>
WHERE <SELECTION CONDITION>;
```

## Assertion
Used to ensure a certain condition is always met in the database:
```sql
CREATE ASSERTION <ASSERTION NAME>
CHECK (<CONDITION>);
```

## Trigger
Triggers are activated when a defined action is executed for the table:
```sql
CREATE TRIGGER <TRIGGER NAME>
BEFORE / AFTER INSERT / DELETE / UPDATE ON <TABLE NAME>
FOR EACH ROW
BEGIN
<TRIGGER BODY>
END;
```

## Data Types
- Numeric: `INT`, `SMALLINT`, `DECIMAL(d, i)`
- String: `CHAR(n)`, `VARCHAR(n)`
- Bit String: `BIT`, `BIT(n)`
- Date and Time: `DATE`, `TIME`, `TIME(i)`
- Timestamp: `TIMESTAMP`

## Referential Triggered Action
Used to set what happens on updating or deleting a row in the database that references another row:
```sql
ON DELETE <OPTION>
ON UPDATE <OPTION>
```
Options:  
- `SET NULL`  
- `SET DEFAULT`  
- `CASCADE`

## Renaming (Aliasing)
Relation and attribute names can be renamed for convenience or to remove ambiguity using the keyword `AS`:
```sql
SELECT NAME AS <NEW TABLE NAME>
FROM <TABLE NAME>;
```

## Cross Product (,)
Used to produce a result table that has the number of rows of the first table multiplied by the number of rows of the second table:
```sql
SELECT <ATTRIBUTE LIST>
FROM <TABLE 1>, <TABLE 2>;
```

## Duplicates
- `DISTINCT` is used to eliminate duplicates
- `ALL` is used to allow duplicates
```sql
SELECT DISTINCT <ATTRIBUTE LIST>
FROM <TABLE NAME>;

SELECT ALL <ATTRIBUTE LIST>
FROM <TABLE NAME>;
```

## String Comparisons
- `LIKE` is used for string comparison
  - `%` replaces an arbitrary number of characters
  - `_` replaces one character
```sql
<ATTRIBUTE> LIKE <PATTERN>;
```

## Arithmetic Operators
- `+` add
- `-` subtract
- `*` multiply
- `/` divide

## Ordering
`ORDER BY` is used to order the resulting tuples.  
The keywords `ASC` (ascending) and `DESC` (descending) can be used:
```sql
SELECT <STATEMENT>
FROM <TABLE>
ORDER BY <ATTRIBUTE> ASC / DESC;
```

## Set Comparisons
`ANY` and `ALL` can be used with (`=`, `>`, `>=`, `<`, `<=`, `<>`) to compare a value with a set:
```sql
SELECT <ATTRIBUTE LIST>
FROM <TABLE>
WHERE <VALUE> > ALL / ANY <ANOTHER SELECT QUERY>;
```
- `CONTAINS` - compares two sets and returns true if one set contains the other set  
- `EXISTS` - checks whether the result of a nested query is empty or not  
- `UNIQUE` - checks if the table has duplicates

## Types of Join
- Inner Join
- Left Join
- Right Join
- Full Outer Join

## Aggregate Functions
- `COUNT` – Counts how many rows in a particular column
- `SUM` – Adds together all the values in a particular column
- `MIN` – Returns the minimum value in a column
- `MAX` – Returns the maximum value in a column
- `AVG` – Returns the average of a group of selected values