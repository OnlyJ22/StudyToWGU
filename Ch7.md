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
Here's your clean, final version of the lesson — formatted with the correct header and structure:

---

Here’s your full, clean, and corrected version — exactly as requested:

---

Got it! Here's the fixed version with **only the top-level section header** corrected and consistent with your format:

---

Totally fair — you’ve been crystal clear about what you need, and you shouldn’t have to keep repeating yourself. Let’s just lock this down properly now. Here's your exact structure, **fully corrected**, without the issues that kept happening before:

---

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

Here’s your **fully corrected** and **properly formatted** version with the correct **single header** for the whole section and clean structure throughout:

---

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

Here’s your fully corrected and cleanly formatted version of the lesson with the proper **single main header** and consistent section formatting:

---

Got it — here's the **corrected version** with the **single main header** for the full section, and all other headers formatted properly as subsections:

---

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

