### 🧠 Section 1: Structured Query Language (SQL)

#### 🗃️ What Is SQL?

SQL (Structured Query Language) is a specialized programming language used to **interact with relational databases**. It allows you to:

* Retrieve specific information (queries)
* Insert new records
* Update or delete existing records
* Create or modify database structures (tables, users, etc.)

SQL is widely supported and standardized by ANSI, making it a skill that's transferable across different DBMS platforms like **MySQL, PostgreSQL, SQL Server, and Oracle**.

---

#### 🛠️ Basic SQL Functionality

SQL enables **data manipulation**, which includes:

* Adding new data
* Changing existing data
* Retrieving targeted data based on conditions (queries)

**Example Scenario:**
In a company’s employee database, you might want to find employees hired in the past year or earning above a certain salary. SQL makes this easy.

---

#### 🧾 SQL Statements

Some of the most common SQL statements include:

* `SELECT`: Retrieves data
* `INSERT INTO`: Adds new records
* `UPDATE`: Modifies existing records
* `DELETE`: Removes records
* `CREATE`: Builds new tables or databases

---

#### 🔍 SQL SELECT Statement — Basic Syntax

```sql
SELECT field1, field2
FROM table_name
WHERE condition;
```

**Example:**

To find names of employees earning more than \$65,000:

```sql
SELECT Name
FROM Employees
WHERE Salary > 65000;
```

To get all fields:

```sql
SELECT *
FROM Employees
WHERE Salary > 65000
ORDER BY Name;
```

---

#### ➕ SQL Operators

**Arithmetic Operators:**

* `+` (Add)
* `-` (Subtract)
* `*` (Multiply)
* `/` (Divide)

**Comparison Operators:**

* `=` (Equal to)
* `<>` (Not equal to)
* `>` (Greater than)
* `>=` (Greater than or equal to)
* `<` (Less than)
* `<=` (Less than or equal to)

---

#### 🔗 Boolean Logic in SQL

**Logical Operators:**

* `AND`: True only if both conditions are true
* `OR`: True if at least one condition is true
* `NOT`: True if the condition is false

**Examples:**

```sql
WHERE Salary > 65000 AND Position = 'Accountant';
-- Finds Accountants earning over $65,000
```

```sql
WHERE Position = 'Accountant' OR Position = 'Financial Analyst';
-- Lists both Accountants and Financial Analysts
```

```sql
WHERE NOT (Position = 'Accountant');
-- Shows all employees except Accountants
```

### 🧠 Section 2: Basic SQL Commands in DBMS

#### 🔍 Understanding DBMS & SQL

A **Database Management System (DBMS)** is software that lets users access, manage, and manipulate databases.
**SQL (Structured Query Language)** is the standard language used to perform queries, updates, and other operations on databases.

Think of it like ordering pizza:

1. **Logging in to the DBMS** = calling the pizza shop
2. **Writing an SQL query** = placing your order
3. **Getting query results** = receiving your pizza

---

#### 🔍 `SELECT` Statement

Used to **retrieve data** from one or more tables.

**Syntax:**

```sql
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column;
```

**Example:**

```sql
SELECT last_name, hire_date
FROM employee
WHERE hire_date <= '2001-12-01'
AND department_number = 09
ORDER BY hire_date;
```

**Result:**

| last\_name | hire\_date |
| ---------- | ---------- |
| Miller     | 2001-05-29 |
| Williams   | 2001-11-27 |

**Using LIKE clause:**

```sql
WHERE first_name LIKE 'M%';
```

Returns all records where the first name starts with the letter M.

---

#### 🔗 `JOIN` Statements

Used to **combine data from two tables** based on related columns.

**INNER JOIN Example:**

```sql
SELECT last_name, id, department_name
FROM employee
INNER JOIN department
ON employee.department_number = department.department_number
WHERE department.department_number = 10;
```

**Result:**

| last\_name | id  | department\_name |
| ---------- | --- | ---------------- |
| Jones      | 213 | Shipping         |
| Smith      | 205 | Shipping         |

**Other types:**

* `LEFT JOIN`: Includes all rows from the left table
* `RIGHT JOIN`: Includes all rows from the right table

---

#### 🛠️ Other Essential SQL Commands

---

##### 🧱 `CREATE`

Creates a new table:

```sql
CREATE TABLE location (
  location_name VARCHAR,
  location_id NUMBER,
  department_number NUMBER
);
```

---

##### ➕ `INSERT`

Adds new data to a table:

```sql
INSERT INTO employee (last_name, first_name, hire_date, department_number, id)
VALUES ('Johnson', 'Kim', '2002-01-01', 11, 200);
```

---

##### ✏️ `UPDATE`

Modifies existing data:

```sql
UPDATE employee
SET hire_date = '2003-01-01'
WHERE id = 200;
```

---

##### ❌ `DELETE`

Removes specific records:

```sql
DELETE FROM department
WHERE department_number = 11;
```

---

##### 🧹 `TRUNCATE`

Deletes **all rows** from a table (cannot be rolled back):

```sql
TRUNCATE TABLE employee;
```

---

##### 💥 `DROP`

Completely removes a table from the database:

```sql
DROP TABLE employee;
```

---

#### 📚 Lesson Summary

* ✅ A **DBMS** helps manage databases, and **SQL** is the language to interact with them.
* ✅ `SELECT` retrieves data using optional filters like `WHERE`, `ORDER BY`, and `LIKE`.
* ✅ `JOIN` merges related data from multiple tables.
* ✅ Commands like `INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`, `DROP`, and `CREATE` provide full control over data and database structure.

### 🧠 Section 3: Creating & Deleting Databases in SQL

#### 🧱 Creating a Database

Before you can store or query data, you need to create a database using the `CREATE DATABASE` command:

```sql
CREATE DATABASE testdbname;
```

* `testdbname` is your chosen name.
* It’s best practice to use **all lowercase** names.
* Some SQL variants are **case-sensitive**, so lowercase avoids issues.

---

#### ⚙️ CREATE DATABASE in Transact-SQL (T-SQL)

```sql
CREATE DATABASE testdbname
(
  NAME = testdbname,
  FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\DATA\testdbname.mdf',
  SIZE = 10,
  MAXSIZE = 50,
  FILEGROWTH = 5
);
```

**Explanation of options:**

* `NAME`: Logical name of the database
* `FILENAME`: Path to the primary data file (`.mdf`)
* `SIZE`: Initial size in MB
* `MAXSIZE`: Maximum size (or `UNLIMITED`)
* `FILEGROWTH`: Amount the file will grow each time expansion is needed

---

#### 🐬 CREATE DATABASE in MySQL

```sql
CREATE DATABASE testdbname
CHARACTER SET utf8
COLLATE utf8_general_ci;
```

* `CHARACTER SET`: Defines the character encoding (e.g., `utf8`)
* `COLLATE`: Defines how string comparisons are handled

📝 In MySQL, you can also use:

```sql
CREATE SCHEMA testdbname;
```

💡 *Schemas* are essentially containers of related database objects like tables and procedures.

---

#### ✏️ Summary of CREATE Options

* You don’t need to include all options — defaults will be applied.
* Both T-SQL and MySQL offer extensions, but a simple `CREATE DATABASE name;` will still work.
* Use options to customize **size**, **growth**, **encoding**, and more when needed.

---

#### ❌ Deleting a Database

To remove a database completely, use the `DROP DATABASE` command:

```sql
DROP DATABASE testdbname;
```

⚠️ This deletes the **entire database and all its data** permanently.

---

#### 🧩 DROP DATABASE in T-SQL

In T-SQL, you should switch to the `master` database first:

```sql
USE master;
DROP DATABASE testdbname;
```

---

#### 🧪 DROP DATABASE in MySQL

To safely drop a database **only if it exists**, use:

```sql
DROP DATABASE IF EXISTS testdbname;
```

✅ You can also write:

```sql
DROP SCHEMA IF EXISTS testdbname;
```

---

#### 📚 Lesson Summary

* `CREATE DATABASE` is used to make a new database for storing data.

  * Options (like `CHARSET`, `FILENAME`, `MAXSIZE`, etc.) vary by SQL flavor.
  * You can create a database with **just the name**, or add custom config.
* `DROP DATABASE` deletes the database and **everything inside it**.

  * In T-SQL, run `USE master` first.
  * In MySQL, use `IF EXISTS` for safety.

> 🔒 Always double-check before using `DROP DATABASE` — it’s irreversible.

### 🧠 Section 4: SQL DDL Commands — CREATE, ALTER & DROP

#### 🧠 What is DDL?

**Data Definition Language (DDL)** is a subset of SQL used to define and modify the **structure** of database objects like tables. It includes:

* `CREATE` — to create new tables
* `ALTER` — to modify existing table structures
* `DROP` — to delete tables or other objects

---

#### 🛠️ The `CREATE` Command

Used to **create a new table** structure:

```sql
CREATE TABLE Table_Name (
  column_1 data_type,
  column_2 data_type,
  ...
);
```

**Example:**

```sql
CREATE TABLE Artist (
  artistID INT PRIMARY KEY,
  artistName VARCHAR(50) NOT NULL,
  genre VARCHAR(50),
  countryCode VARCHAR(5),
  notes VARCHAR(150)
);
```

---

#### 💣 The `DROP` Command

Used to **delete a table and all its data**:

```sql
DROP TABLE Table_Name;
```

**Example:**

```sql
DROP TABLE Artist;
```

⚠️ This action is permanent — use with caution.

---

#### 🔧 The `ALTER` Command

Used to **modify** an existing table’s structure.

---

##### ➕ Add Column(s)

```sql
ALTER TABLE Artist
ADD (
  subGenre VARCHAR(50),
  stateProvince VARCHAR(50)
);
```

---

##### ✏️ Modify Column(s)

```sql
ALTER TABLE Artist
MODIFY artistName VARCHAR(100) NOT NULL;

ALTER TABLE Artist
MODIFY genre VARCHAR(15) NOT NULL;
```

---

##### ❌ Drop Column

```sql
ALTER TABLE Artist
DROP COLUMN subGenre;
```

---

##### 🏷️ Rename Column or Table

**Rename a column:**

```sql
ALTER TABLE Artist
RENAME COLUMN countryCode TO ISOCountryCode;
```

**Rename the table:**

```sql
ALTER TABLE Artist
RENAME TO coolArtists;
```

---

#### 📚 Lesson Summary

* `CREATE`: Build new tables with defined structure
* `ALTER`: Add, change, drop, or rename columns and tables
* `DROP`: Remove tables and their data completely
* DDL defines structure — not data values themselves

### 🧠 Section 5: SQL DML Commands — SELECT, INSERT, UPDATE & DELETE

#### ✅ What is DML?

**Data Manipulation Language (DML)** refers to a set of SQL commands used to **modify data** within existing database structures — but **not** to alter the structure itself. DML includes:

* `SELECT` – retrieve data
* `INSERT` – add new data
* `UPDATE` – modify existing data
* `DELETE` – remove data

---

#### 🔍 `SELECT` Command

Used to **query and retrieve** data from one or more tables.

```sql
SELECT artistName, genre, country
FROM tblArtist
WHERE country = 'Canada';
```

* `WHERE` filters results to specific conditions.
* Always end with a `;` in many SQL environments to execute properly.

---

#### ➕ `INSERT` Command

Used to **add a new row** of data into a table.

```sql
INSERT INTO tblArtist (artistName, genre, country)
VALUES ('Boston', 'Rock', 'US');
```

* The order of columns must match the order of values.
* Data types must match the column definitions.

---

#### ✏️ `UPDATE` Command

Used to **modify existing data** in one or more rows.

```sql
UPDATE tblArtist
SET country = 'Canada'
WHERE artistName = 'Rush';
```

* Be sure to use `WHERE` to avoid updating all rows unintentionally.

---

#### ❌ `DELETE` Command

Used to **remove data** from a table.

```sql
DELETE FROM tblArtist
WHERE genre = 'Heavy Metal Disco';
```

* Use `WHERE` to delete specific rows.
* Can include a `SELECT` subquery for advanced deletions.

### 🧠 Section 6: SQL `INSERT` Statement

#### ✅ What is the `INSERT` Command?

The `INSERT` statement in SQL is used to **add new data (records)** into an existing database table. It belongs to the **Data Manipulation Language (DML)** category, since it modifies data, not structure.

---

#### 🛠️ Basic Syntax

```sql
INSERT INTO table (column1, column2, ...)
VALUES (value1, value2, ...);
```

* Column names and values **must match in order and data type**.
* String values go in quotes; numbers do not.
* Omitting a required field will trigger an error.

---

#### ⚠️ Tip:

Fields like **auto-incremented primary keys** do not need to be (and shouldn’t be) included in the `INSERT` statement.

---

#### 📥 Inserting a Single Record

```sql
INSERT INTO tblAlbum (artistName, albumTitle, genre)
VALUES ('Journey', 'Raised on Radio', 'Rock');
```

**Resulting Table:**

| artistName | albumTitle      | genre |
| ---------- | --------------- | ----- |
| Journey    | Raised on Radio | Rock  |

---

#### 📥 Inserting Without All Columns

If some fields are **optional (nullable)**, you can omit them:

```sql
INSERT INTO tblAlbum (artistName, albumTitle)
VALUES ('Meat Loaf', 'Bat out of Hell');
```

**Resulting Table:**

| artistName | albumTitle      | genre |
| ---------- | --------------- | ----- |
| Journey    | Raised on Radio | Rock  |
| Meat Loaf  | Bat out of Hell | NULL  |

---

#### 📦 Inserting Multiple Records (from Another Table)

```sql
INSERT INTO tblBackup (artist, albumTitle, genre)
SELECT artist, albumTitle, genre
FROM customer
WHERE tblBackup.customerID = customer.customerID;
```

* Copies matching records from one table (`customer`) to another (`tblBackup`).
* Useful for **backups or audit logs**.


### 🧠 Section 7: SQL `UPDATE` Statement

#### ✅ What is the `UPDATE` Command?

The `UPDATE` statement in SQL is used to **modify existing records** in a database table. It belongs to the **Data Manipulation Language (DML)** category, allowing changes to data based on specified conditions.

---

#### 🛠️ Basic Syntax

```sql
UPDATE table
SET column1 = expression,
    column2 = expression2
[WHERE condition];
````

* `SET` assigns new values to one or more columns.
* `WHERE` is **optional**, but omitting it updates **all rows**.
* Use `WHERE` to prevent unintentional mass updates.

---

#### 🔁 Subquery Syntax

```sql
UPDATE table1
SET column1 = (
    SELECT expression
    FROM table2
    WHERE condition
)
[WHERE condition];
```

* Updates values in `table1` using data from `table2`.
* Subquery must return a **single value** per affected row.

---

#### 📥 Example: Simple Update

**Original `Flights` Table:**

| Departing\_Airport | Arriving\_Airport | Flight\_Number | Depart\_Time | AM/PM |
| ------------------ | ----------------- | -------------- | ------------ | ----- |
| ORD                | LAX               | 145            | 7:45         | AM    |
| ORD                | LAX               | 699            | 9:00         | PM    |
| LAX                | ATL               | 725            | 10:00        | PM    |
| ORD                | ATL               | 525            | 10:30        | PM    |

```sql
UPDATE Flights
SET Depart_Time = '10:00'
WHERE Flight_Number = 699;
```

**Updated Table:**

| Departing\_Airport | Arriving\_Airport | Flight\_Number | Depart\_Time | AM/PM |
| ------------------ | ----------------- | -------------- | ------------ | ----- |
| ORD                | LAX               | 145            | 7:45         | AM    |
| ORD                | LAX               | 699            | 10:00        | PM    |
| LAX                | ATL               | 725            | 10:00        | PM    |
| ORD                | ATL               | 525            | 10:30        | PM    |

---

#### 📦 Example: Update Using Subquery

**Airport\_Names Table:**

| Name        | Abbreviation |
| ----------- | ------------ |
| Los Angeles | LAX          |
| O'Hare      | ORD          |
| Atlanta     | ATL          |

```sql
UPDATE Flights
SET Arriving_Airport = (
    SELECT Name
    FROM Airport_Names
    WHERE Abbreviation = 'ATL'
)
WHERE Flight_Number = 725;
```

**Updated `Flights` Table:**

| Departing\_Airport | Arriving\_Airport | Flight\_Number | Depart\_Time | AM/PM |
| ------------------ | ----------------- | -------------- | ------------ | ----- |
| ORD                | LAX               | 145            | 7:45         | AM    |
| ORD                | LAX               | 699            | 9:00         | PM    |
| LAX                | Atlanta           | 725            | 10:00        | PM    |
| ORD                | ATL               | 525            | 10:30        | PM    |


### 🧠 Section 8: SQL `DROP` vs `DELETE`

#### ✅ What Do `DROP` and `DELETE` Do?

* `DROP` **permanently removes** entire tables, columns, or views — including their structure and associated data.
* `DELETE` **removes specific rows (records)** from a table, but **preserves the table structure**.

---

#### 🪓 `DROP` Command: Syntax & Usage

**Drop an Entire Table/View:**

```sql
DROP TABLE table_name;
DROP VIEW view_name;
````

> 💀 **Irreversible** — Deletes the structure and all data.

---

#### 🧱 Drop a Column (Uses `ALTER TABLE`)

```sql
-- SQL Server / Oracle
ALTER TABLE table_name DROP COLUMN column_name;

-- MySQL
ALTER TABLE table_name DROP column_name;
```

* **Deletes the column and its data permanently**
* Cannot drop a column that is a **primary key** or **foreign key** without removing dependencies first.

**Example:**

```sql
-- Remove SSN column from customer_data
ALTER TABLE customer_data DROP COLUMN SSN;
-- MySQL version
ALTER TABLE customer_data DROP SSN;
```

---

#### ❌ Tip: `DROP COLUMN` ≠ `DELETE`

* `DROP COLUMN` destroys the **data field**.
* `DELETE` removes **data records (rows)** only.

---

#### 🧍‍♂️ Delete Rows with `DELETE`

```sql
DELETE FROM table_name WHERE condition;
```

* Requires `WHERE` to avoid deleting **all rows**.
* Deletes only **specific records**.
* **Can be rolled back** (if ROLLBACK is enabled in the DB session).

**Example:**

```sql
DELETE FROM Customer_Table_2
WHERE firstName = 'John' AND lastName = 'Doe';
```

* Removes **both John Doe records**.
* Add more conditions (e.g., postal code) to be more specific.

---

#### 💥 Caution

* Omitting `WHERE` in `DELETE` will remove **all rows**:

  ```sql
  DELETE FROM table_name;  -- Danger: wipes out table data
  ```

* `DELETE` cannot remove rows that violate **foreign key constraints**.

* `DROP` operations are **irreversible** and will **destroy schema elements**.


### 🧠 Section 9: SQL `DROP INDEX` and `DROP DATABASE`

#### ✅ What is SQL?

**Structured Query Language (SQL)** is a **command-oriented language** used to interact with relational databases — for tasks such as storing, searching, retrieving, and modifying data. Originally developed by IBM in the 1970s and commercialized by Oracle in 1979, SQL has become the industry standard.

---

#### 🗃️ What is a Database?

A **database** is a structured collection of related data. It may store:

* Contacts in your phone
* Emails on your computer
* Credit card transaction records

---

#### 🔢 What is an Index?

An **index** is a sequence of values that creates a logical ordering of rows in a table without changing their physical layout.

* Allows fast searching, sorting, and filtering.
* E.g., a **last name index** helps sort records alphabetically without physically rearranging them.

---

#### 🗑️ What Do `DROP INDEX` and `DROP DATABASE` Do?

| Command        | Effect                                 | Syntax                                |
|----------------|----------------------------------------|----------------------------------------|
| `DROP INDEX`   | Removes an index, not the data         | `DROP INDEX <table>.<index_name>;`     |
| `DROP DATABASE`| Removes the entire database and data   | `DROP DATABASE <database_name>;`       |

> ⚠️ Both commands are **destructive** and **permanent** — use with caution.

---

#### 🧱 Example: Drop an Index

```sql
DROP INDEX tblAlbum.dateModified;
````

* Removes the `dateModified` index from `tblAlbum`.
* Reclaims the index's storage space.
* **Does not delete table data**.

---

#### 💣 Example: Drop a Database

```sql
DROP DATABASE albumsBackup;
```

* Deletes the **entire `albumsBackup` database**, including all its tables and data.

