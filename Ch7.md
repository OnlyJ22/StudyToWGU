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
