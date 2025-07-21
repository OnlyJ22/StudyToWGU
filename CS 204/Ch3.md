### Section 1: Query Concepts in SQL

**High-Yield Buzzwords:** `SELECT`, `FROM`, `WHERE`, `ORDER BY`, *syntax sensitivity*, *relational database*, *SQL clauses*

---

#### What is Syntax in SQL?

* **Definition:** Syntax refers to the structured format required to write valid SQL queries.
* **Importance:** Errors in syntax (like incorrect clause order or missing delimiters) prevent successful query execution.
* **Tip:** SQL syntax is database-dependent—check for platform compatibility (e.g., MySQL vs. SQL Server).

---

#### Relational Database Overview

* **Structure:** Composed of *tables (files)* → *records (rows)* → *fields (columns)*.
* **Benefit:** Allows for linking data across multiple tables using keys.
* **Examples:** Oracle, MySQL, SQL Server, DB2.

---

#### Structured Query Language (SQL)

* **Purpose:** Interacts with and retrieves data from relational databases.
* **Key Function:** Executes precise queries using a set of defined clauses.
* **Requires:** Strict syntax and understanding of data structure and location.

---

#### SQL Clauses Breakdown

| Clause       | Function                                          |
| ------------ | ------------------------------------------------- |
| `SELECT`     | Specifies which fields to retrieve                |
| `FROM`       | Identifies the table(s) containing those fields   |
| `WHERE`\*    | Filters results based on a condition              |
| `ORDER BY`\* | Sorts the output in ascending or descending order |

* *Clauses marked with an asterisk (*) are optional.\*

---

#### SQL Statement Structure

**Example:**

```sql
SELECT Movie_Title
FROM Movies
WHERE Title = 'Rocky';
```

**Explanation:**

* `SELECT`: Retrieves the column `Movie_Title`
* `FROM`: Queries the `Movies` table
* `WHERE`: Filters for rows where the `Title` equals 'Rocky'

---

#### SQL Syntax Rules

* `SELECT` **must** precede `FROM`
* Enclose field names with spaces/special characters in **square brackets**
* Use commas to separate multiple columns
* Optional clauses:

  * `WHERE`: Filters results
  * `ORDER BY`: Sorts results

---

#### Additional Example:

```sql
SELECT Phone, Address
FROM Associates
WHERE Company = 'Study.com';
```

| Clause   | Function                                          |
| -------- | ------------------------------------------------- |
| `SELECT` | Retrieves the `Phone` and `Address` fields        |
| `FROM`   | Searches in the `Associates` table                |
| `WHERE`  | Filters for records where `Company` = 'Study.com' |

---

#### Lesson Summary

* **SQL queries** must follow strict **syntax rules**.
* Use the correct order: `SELECT` → `FROM` → (`WHERE`) → (`ORDER BY`).
* Know your **table structure**, **column names**, and **desired result**.
* Use brackets for field names with **spaces/special characters**.
* Clauses like `WHERE` and `ORDER BY` are **optional** but useful for precision.

### Section 2: Advanced SQL SELECT Statements

**High-Yield Buzzwords:** `SELECT`, `DISTINCT`, `ORDER BY`, `WHERE`, `GROUP BY`, `HAVING`, `LEFT`, `LIKE`, `UPPER`, `TRIM`, `CONCAT`, `SUM`, `COUNT`, `AVG`, *scalar functions*, *aggregate functions*, *wildcards*

---

#### Basic SELECT and Sorting

```sql
SELECT productVendor, productLine
FROM products
ORDER BY productVendor; -- Ascending by default
```

```sql
ORDER BY productVendor DESC; -- Descending order
```

---

#### DISTINCT for Unique Values

```sql
SELECT DISTINCT vendorName
FROM products;
```

---

#### Filtering with WHERE Clause

```sql
SELECT productCode, productName, productLine, productVendor
FROM products
WHERE productLine = 'Classic Cars'
ORDER BY productCode;
```

##### Multiple Conditions with OR

```sql
SELECT productCode, productName, productLine, productVendor
FROM products
WHERE productCode = 'S12_1099'
   OR productCode = 'S18_2238'
   OR productCode = 'S18_1129'
ORDER BY productName;
```

---

#### LEFT and LIKE Functions for Pattern Matching

**LEFT Function:**

```sql
SELECT productCode, productName
FROM products
WHERE LEFT(productName, 4) = '1957'
   OR LEFT(productName, 4) = '1960'
ORDER BY productName;
```

**LIKE and Wildcards:**

```sql
SELECT productCode, productName
FROM products
WHERE productName LIKE '195%'
   OR productName LIKE '193%'
ORDER BY productName;
```

**Wildcard Operators:**

* `%` — any sequence
* `_` — single character
* `[ab]` — a or b
* `[^ab]` — not a or b

---

#### Transformation Functions

**UPPER + TRIM:**

```sql
SELECT productVendor,
       UPPER(productName) AS productName,
       UPPER(productDescription) AS productDescription
FROM products
WHERE TRIM(UPPER(productVendor)) = 'AUTOART STUDIO DESIGN'
ORDER BY productVendor;
```

**CONCAT:**

```sql
SELECT CONCAT(productCode, ' - ', productLine) AS 'Product Code Line',
       productName,
       productVendor
FROM products;
```

---

#### Aggregate Functions with GROUP BY

**SUM:**

```sql
SELECT SUM(amount) AS 'Total Amount'
FROM payments;
```

**AVG:**

```sql
SELECT AVG(amount) AS 'Average'
FROM payments;
```

**Group Aggregates:**

```sql
SELECT customerNumber,
       SUM(amount) AS 'Total Amt'
FROM payments
GROUP BY customerNumber
ORDER BY customerNumber;
```

**Date Filtering:**

```sql
SELECT customerNumber,
       paymentDate,
       SUM(amount) AS 'Total Amt'
FROM payments
WHERE paymentDate BETWEEN '2005-01-01' AND '2005-12-31'
GROUP BY customerNumber, paymentDate
ORDER BY customerNumber;
```

---

#### COUNT and HAVING

**COUNT by Customer:**

```sql
SELECT customerNumber,
       COUNT(*) AS 'Total Orders by Customer'
FROM payments
GROUP BY customerNumber
ORDER BY customerNumber;
```

**HAVING to Filter Groups:**

```sql
SELECT customerNumber,
       COUNT(*) AS 'Total Orders by Customer'
FROM payments
GROUP BY customerNumber
HAVING COUNT(customerNumber) > 5
ORDER BY customerNumber;
```

---

#### Lesson Summary

* `DISTINCT` filters duplicates.
* `ORDER BY` sorts data (ASC/DESC).
* `WHERE` filters rows (can include wildcards).
* Scalar functions (`LEFT`, `UPPER`, `TRIM`, `CONCAT`) manipulate string data.
* Aggregate functions (`SUM`, `COUNT`, `AVG`) analyze numeric data.
* `GROUP BY` organizes data for aggregates.
* `HAVING` filters group-level results.

### Section 3: SQL INSERT Statement

**INSERT Syntax**

```sql
INSERT INTO table (column_name1, column_name2, ...)
VALUES (value_1, value_2, ...);
```

* Inserts new records into a table.
* Column order must match the value order.
* Each value must match the corresponding data type.

---

**Insert Single Record**

```sql
INSERT INTO tblAlbum(artistName, albumTitle, genre)
VALUES ('Journey', 'Raised on Radio', 'Rock');
```

Resulting table:

| artistName | albumTitle      | genre |
| ---------- | --------------- | ----- |
| Journey    | Raised on Radio | Rock  |

---

**Insert Without All Columns**

```sql
INSERT INTO tblAlbum(artistName, albumTitle)
VALUES('Meat Loaf', 'Bat out of Hell');
```

* `genre` field will be `NULL` if not required.

---

**Auto-Generated Fields**

* Auto-numbered fields (e.g. Primary Keys) are automatically filled.
* Manually setting them causes errors.

---

**Insert Multiple Records from Another Table**

```sql
INSERT INTO tblBackup(artist, albumTitle, genre)
SELECT artist, albumTitle, genre
FROM customer
WHERE tblBackup.customerID = customer.customerID;
```

* Copies records conditionally from one table to another.

---

**Lesson Summary**

* The `INSERT` statement adds records to a table.
* `INSERT ... VALUES` is for single record entries.
* `INSERT ... SELECT` allows for batch inserts from other tables.
* Always ensure column order and data type consistency.

### Section 4: SQL SELECT Statement

**Basic SELECT Syntax**

```sql
SELECT column1, column2 FROM table;
```

To select all columns:

```sql
SELECT * FROM Actors;
```

---

**WHERE Clause**

Filters records based on a condition:

```sql
SELECT * FROM Actors WHERE Sex = 'Male';
```

---

**LIKE Operator**

Pattern-based search using wildcards:

* Starts with 'E':

```sql
SELECT * FROM Actors WHERE FirstName LIKE 'E%';
```

* Contains 'an':

```sql
SELECT * FROM Actors WHERE LastName LIKE '%an%';
```

---

**IN Operator**

Searches for multiple exact values:

```sql
SELECT * FROM Actors WHERE LastName IN ('Rudd', 'Robbie');
```

---

**BETWEEN Operator**

Selects values within a specified range (inclusive):

```sql
SELECT * FROM Actors WHERE Age BETWEEN '25' AND '39';
```

---

**TOP Operator (SQL Server)**

Limits number of rows returned:

```sql
SELECT TOP 3 * FROM Actors;
```

To get last 3 rows:

```sql
SELECT TOP 3 * FROM Actors ORDER BY ActorID DESC;
```

---

**LIMIT Operator (MySQL)**

Used in MySQL to limit result set:

```sql
SELECT * FROM Actors LIMIT 3;
```

To get last 3 records:

```sql
SELECT * FROM Actors ORDER BY ActorID DESC LIMIT 3;
```

---

**Lesson Summary**

* `SELECT` retrieves data.
* `WHERE` filters records.
* `LIKE` searches patterns.
* `IN` matches multiple values.
* `BETWEEN` filters within a range.
* `TOP` (SQL Server) and `LIMIT` (MySQL) control result set size.
* `ORDER BY` determines sort order.

### Section 5: SQL ISNULL Function

**ISNULL Syntax (SQL Server)**

```sql
ISNULL(expression, alternate_value)
```

* `expression`: the field or value being evaluated
* `alternate_value`: what to return if `expression` is NULL

---

**Use Case: Multiplication with NULL**

```sql
SELECT itemName, cost * ISNULL(qty, 0)
FROM tblInventory;
```

Ensures that missing quantity values (`NULL`) are treated as 0 to allow valid calculations.

---

**Use Case: Addition with NULL**

```sql
SELECT 
  q1.payCode, 
  q2.payCode,
  ISNULL(q1.wageAmount, 0) + ISNULL(q2.wageAmount, 0)
FROM tblQuarterlyWage;
```

Adds wage amounts across quarters, defaulting missing values to 0.

---

**Use Case: Averages with NULL**

```sql
SELECT AVG(ISNULL(rating, 50))
FROM tblAlbum;
```

Replaces NULL ratings with 50 (a median score) before computing the average.

---

**Use Case: Replacing NULLs in the Table Permanently**

```sql
UPDATE tblAlbum
SET rating = 50
WHERE ISNULL(rating, NULL) IS NULL;
```

Updates all `NULL` values in the `rating` field to `50`.

---

**Lesson Summary**

* `ISNULL` replaces NULL with a specified value, crucial for calculations.
* Commonly used in multiplication, addition, averages, and update statements.
* Ensures robust query execution and accurate reporting by handling incomplete data.
* Specifically used in **SQL Server**; different behavior in **MySQL**.

### Section 6: ORDER BY Clause in SQL

**Default Sorting Behavior**

```sql
SELECT * FROM employees;
```

* Returns rows in unspecified order.

---

**Sort by One Column (Ascending Order)**

```sql
SELECT * FROM employees ORDER BY last_name;
-- or explicitly:
SELECT * FROM employees ORDER BY last_name ASC;
```

* Sorts rows A–Z by `last_name`.

---

**Sort by One Column (Descending Order)**

```sql
SELECT * FROM employees ORDER BY last_name DESC;
```

* Sorts rows Z–A by `last_name`.

---

**Sort by Multiple Columns**

```sql
SELECT * FROM employees ORDER BY last_name, first_name;
```

* First sorts by `last_name`, and where equal, sorts by `first_name`.

```sql
SELECT * FROM employees ORDER BY last_name DESC, first_name ASC;
```

* `last_name` Z–A, then `first_name` A–Z.

---

**Sort Using Column Positions**

```sql
SELECT emp_no, birth_date, first_name, last_name, gender, hire_date
FROM employees
ORDER BY 4 DESC, 3;
```

* Column 4 (`last_name`) DESC, then column 3 (`first_name`) ASC.

---

**Sort by a Column Not in SELECT List**

```sql
SELECT emp_no, first_name, last_name
FROM employees
ORDER BY hire_date;
```

* Sorted by `hire_date` (not included in SELECT).

---

**Verifying Sort Order**

```sql
SELECT emp_no, first_name, last_name, hire_date
FROM employees
ORDER BY hire_date;
```

* Displays `hire_date` to confirm the order.

---

**Lesson Summary**

* `ORDER BY` sorts result sets.
* Default is ascending (`ASC`), use `DESC` for reverse order.
* Multiple column sorting is allowed.
* Can sort by column positions or even columns not listed in SELECT.

### Section 7: SQL Functions

**Character Functions**

* `UPPER()` / `LOWER()` convert case for consistent matching.

```sql
SELECT UPPER(productName) FROM models WHERE productLine = 'Planes';
SELECT LOWER(productName) AS 'Product' FROM models;
```

* `CONCAT()` joins two strings.

```sql
SELECT CONCAT(productName, productLine) FROM models;
```

* `LENGTH()` returns character count.

```sql
SELECT LENGTH(productName) AS 'Product Length' FROM models ORDER BY LENGTH(productName) ASC;
```

* `SUBSTR()` extracts substring from a given position.

```sql
SELECT SUBSTR(productName, 6) FROM models;      -- Outputs 'Mustang'
SELECT SUBSTR(productName, 1, 4) FROM models;   -- Outputs 'P-51'
```

* `TRIM()` removes leading/trailing spaces.

```sql
SELECT * FROM modelTable, myModelTable
WHERE TRIM(modelTable.productName) = TRIM(myModelTable.productName);
```

* `LEFT()`, `RIGHT()`, and `MID()` extract string segments.

```sql
SELECT * FROM models WHERE LEFT(productName, 4) = 'Ford';
SELECT * FROM models WHERE RIGHT(price, 2) <> '99';
SELECT MID(productName, 4, 4) AS 'MID TEST' FROM models;
```

---

**Numeric Functions**

* `ABS()` returns absolute value.

```sql
SELECT productName, ABS(price) FROM models;
```

* `CEIL()` and `FLOOR()` round values up or down.

```sql
SELECT productName,
       CEIL(price) AS 'Ceiling Price',
       FLOOR(price) AS 'Floor Price'
FROM models;
```

* `ROUND()` rounds to a specific decimal place.

```sql
SELECT productName,
       ROUND(price, 1) AS 'Rounded Price'
FROM models;
```

---

**Date Functions**

* `YEAR()` extracts the year from a date.

```sql
SELECT YEAR('2022-10-31');
```

* `CURDATE()` returns the current date.

```sql
SELECT CURDATE();
```

* `DATEDIFF()` returns the number of days between two dates.

```sql
SELECT DATEDIFF(paidDate, CURDATE()) FROM myTable;
```

---

**Lesson Summary**

SQL functions allow manipulation of character, numeric, and date fields for cleaner queries and formatting. Character functions like `TRIM` and `SUBSTR` refine text; numeric functions like `ABS`, `CEIL`, and `ROUND` adjust numerical output; and date functions like `DATEDIFF` support time-based analysis.


### Section 8: NVL Function in Oracle

**Purpose:**
`NVL` is a substitution function used in Oracle to replace `NULL` values with a specified substitute. It only works in Oracle databases.

```sql
NVL(value, substitute)
```

---

**Use Case – Replace NULL Rating:**

```sql
SELECT NVL(Rating, 5) FROM tblAlbum;
```

Returns `5` for albums with `NULL` ratings.

---

**Use Case – SUM with NULL Inventory:**

```sql
SELECT SUM(NVL(Inventory, 5)) FROM Inventory;
```

This ensures all `NULL` counts are treated as `5`, allowing aggregation without errors.

---

**Use Case – String Substitution:**
To replace `NULL` rating values with `'Unrated'` in textual output:

```sql
SELECT NVL(TO_CHAR(Rating), 'Unrated') FROM tblAlbum;
```

Ensures correct data type conversion and meaningful display.

---

**Lesson Summary:**

* `NVL()` replaces `NULL` values with specified substitutes.
* Available **only** in Oracle.
* Works with **numeric** and **string** data types.
* Use `TO_CHAR()` when substituting a string for a numeric `NULL`.
* Ensures stability in queries involving aggregation and string handling.

### Section 9: The CASE Statement

**Purpose:**
The `CASE` statement in SQL provides a way to conditionally return values based on column contents, effectively acting like an `if/then/else` control structure embedded within a `SELECT` query.

```sql
CASE expression
WHEN value1 THEN result1
WHEN value2 THEN result2
ELSE default_result
END
```

---

**Example – Genre Classification by ID:**

```sql
SELECT artistID, genreID,
  CASE genreID
    WHEN 1 THEN 'Rock'
    WHEN 2 THEN 'Classical'
    ELSE 'Some Other Genre'
  END AS "Genre Classification"
FROM tblArtist;
```

---

**Multiple Conditions – Region by Office Code:**

```sql
SELECT employeeNumber, officeCode,
  CASE officeCode
    WHEN 7 THEN 'Northeast'
    WHEN 1 THEN 'Southwest'
    ELSE 'Some Other Region'
  END AS "Region"
FROM employees;
```

---

**Improved Range Evaluation:**
Avoid ambiguous overlaps by using `CASE` with conditions in order:

```sql
SELECT employeeNumber, officeCode,
  CASE
    WHEN regionID > 5 THEN 'Northeast'
    WHEN regionID > 3 AND regionID <= 5 THEN 'Southeast'
    WHEN regionID > 2 AND regionID <= 3 THEN 'Midwest'
    WHEN regionID > 1 AND regionID <= 2 THEN 'Northwest'
    ELSE 'Some Other Region'
  END AS "Region"
FROM tblEmployee;
```

---

**Using CASE with Aggregate Functions – Count by Region:**

```sql
SELECT 
  CASE 
    WHEN genreID = 1 THEN 'Southwest'
    WHEN genreID = 7 THEN 'Northeast'
    ELSE 'Some Other Region'
  END AS "Region",
  COUNT(1) AS Count
FROM tblEmployee
GROUP BY 1;
```

---

**Lesson Summary:**

* `CASE` is a cleaner alternative to complex `IF/THEN/ELSE` logic.
* Keywords: `WHEN`, `THEN`, `ELSE`, `END`.
* Always include an `ELSE` to handle unmatched conditions.
* Can be used in combination with aggregate functions like `COUNT`, `SUM`, etc.
* Enhances readability and flexibility of SQL queries.

### Section 10: GROUP BY Clause

**Definition:**
SQL (Structured Query Language) is a specialized language used to interact with relational databases. It retrieves, manipulates, and manages structured data stored in tables. SQL statements can be embedded within languages like Java or C++ to enable data operations.

---

**GROUP BY Clause:**
Used to aggregate data into logical groups based on one or more columns. **Requires** the use of an aggregate function like `COUNT()`, `SUM()`, `AVG()`, `MIN()`, or `MAX()`.

**Syntax:**

```sql
SELECT column1, column2, AGGREGATE_FUNCTION(column3)
FROM table_name
WHERE condition
GROUP BY column1, column2
ORDER BY column1, column2;
```

---

**Example – Grouping Without ORDER BY:**
Given table `Merchandise`:

```
Merchandise_id | Color | Manufacturer_id
459965         | Red   | 678
344789         | Blue  | 725
478346         | Red   | 645
476904         | Red   | 678
476800         | Blue  | 678
```

Query:

```sql
SELECT COUNT(Merchandise_id) AS COUNT, Merchandise_id, Color
FROM Merchandise
WHERE Manufacturer_id = 678
GROUP BY Color;
```

**Result:**

```
COUNT | Merchandise_id | Color
1     | 476800         | Blue
1     | 459965         | Red
1     | 476904         | Red
```

---

**Example – Grouping With ORDER BY:**

```sql
SELECT COUNT(Merchandise_id) AS COUNT, Color
FROM Merchandise
WHERE Color = 'Red'
GROUP BY Color
ORDER BY COUNT;
```

**Result:**

```
COUNT | Color
3     | Red
```

---

**Lesson Summary:**

* `SQL` communicates with relational databases to retrieve and manage data.
* `GROUP BY` aggregates rows with the same values in specified columns.
* Always pair `GROUP BY` with an aggregate function.
* Use `ORDER BY` to sort the grouped results.
* `GROUP BY` precedes `ORDER BY` in syntax.



### Section 11: SQL GROUP BY Clause

**Data Aggregation**
The `GROUP BY` clause aggregates data using SQL functions like `COUNT`, `SUM`, `AVG`, `MAX`, and `MIN`, condensing multiple rows into one per group. It’s essential when summarizing large datasets by a specific column or combination of columns.

---

**Sample Table Structure: `Survey`**

| Column Name    | Data Type     |
| -------------- | ------------- |
| FullName       | VARCHAR(50)   |
| BirthDate      | DATE          |
| FavoriteFood   | VARCHAR(20)   |
| DailyAllowance | DECIMAL(10,2) |
| DailySpent     | DECIMAL(10,2) |

Example data includes school children’s names, birth dates, favorite food, and daily allowance/spending.

---

**Create and Populate Table in MySQL**

```sql
CREATE DATABASE Survey;
USE Survey;

CREATE TABLE Survey (
  FullName VARCHAR(50) NOT NULL,
  ZipCode INT(5) NOT NULL,
  BirthDate DATE NOT NULL,
  FavoriteFood VARCHAR(20) NOT NULL,
  DailyAllowance DECIMAL(10,2) NOT NULL,
  DailySpent DECIMAL(10,2) NOT NULL
);

INSERT INTO Survey VALUES 
("Andrew Anderson",55901,'2011-02-14',"Hamburger",6,3),
("Esther East",55906,'2008-05-05',"Pizza",4,4),
... (rest of entries)
("Paul Paulson",55901,'2008-08-01',"Pizza",10,10);
```

---

**Aggregate Function Examples with GROUP BY**

* **SUM**

```sql
SELECT FavoriteFood, SUM(DailyAllowance) AS 'Total Daily Allowance'
FROM Survey
GROUP BY FavoriteFood;
```

* **COUNT**

```sql
SELECT FavoriteFood, COUNT(FavoriteFood) AS 'No Of Occurrences'
FROM Survey
GROUP BY FavoriteFood;
```

* **AVG**

```sql
SELECT ZipCode, AVG(DailyAllowance) AS 'AverageDailyAllowance'
FROM Survey
GROUP BY ZipCode;
```

* **MIN and MAX**

```sql
SELECT FavoriteFood, MIN(DailyAllowance), MAX(DailyAllowance)
FROM Survey
GROUP BY FavoriteFood;
```

---

**Multi-column Grouping**

```sql
SELECT FavoriteFood, ZipCode, SUM(DailyAllowance) AS 'Total Daily Allowance'
FROM Survey
GROUP BY FavoriteFood, ZipCode;
```

**Distinct Grouping Without Aggregation**

```sql
SELECT ZipCode, FavoriteFood
FROM Survey
GROUP BY ZipCode, FavoriteFood;
```

---

**Lesson Summary**
The `GROUP BY` clause organizes rows into groups and allows aggregation with functions like:

* `SUM()` – totals
* `AVG()` – average values
* `COUNT()` – count occurrences
* `MIN()` / `MAX()` – range values

It's a core tool for summarizing data by category or condition in SQL.
