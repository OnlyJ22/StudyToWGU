### 🧠 Section 1: SQL Complex Queries

SQL complex queries are advanced commands used to retrieve or manipulate data across multiple tables or using special logic. These include **joins**, **unions**, and **stored procedures**.

---

#### 🔗 INNER JOIN

Returns records where there is a match in **both** tables.

**Example:**

```sql
SELECT *
FROM tblAlbum
INNER JOIN tblArtist
ON tblAlbum.artistID = tblArtist.artistID;
````

**Result:**
Only rows with matching `artistID` in both tables are shown.

---

#### 🔗 LEFT OUTER JOIN

Returns **all records from the left table** and matching ones from the right.

**Example:**

```sql
SELECT *
FROM tblArtist
LEFT OUTER JOIN tblAlbum
ON tblArtist.artistID = tblAlbum.artistID;
```

**Use Case:** Shows all artists, even if they have no albums yet (e.g., Aerosmith with NULL album data).

---

#### 🔗 RIGHT OUTER JOIN

Returns **all records from the right table** and matching ones from the left.

**Example:**

```sql
SELECT *
FROM tblArtist
RIGHT OUTER JOIN tblAlbum
ON tblArtist.artistID = tblAlbum.artistID;
```

**Use Case:** Useful when some albums exist without an assigned artist (e.g., "Unknown" album).

---

#### 🔗 FULL OUTER JOIN (Non-Matching Rows)

Returns **all records** from both tables; NULLs appear where there's no match.

**Example:**

```sql
SELECT *
FROM tblArtist
FULL OUTER JOIN tblAlbum
ON tblArtist.artistID = tblAlbum.artistID
WHERE tblArtist.artistID IS NULL OR tblAlbum.artistID IS NULL;
```

**Use Case:** Identifies rows in either table that have no match in the other.

---

#### ➕ UNION

Combines the result sets of two or more `SELECT` statements into **new rows**.

```sql
SELECT artistName FROM tblArtist
UNION
SELECT bandName FROM tblBands;
```

* Removes duplicates by default.
* Use `UNION ALL` to include duplicates.

**Key Difference:** UNION stacks rows vertically; JOINs combine columns horizontally.

---

#### ⚙️ Stored Procedures

A **stored procedure** is a pre-written SQL program stored in the database.

**Example:**

```sql
CREATE PROCEDURE uspGetArtist
@artistTable VARCHAR(100),
@artistID INT
AS
DECLARE @SQL VARCHAR(1000)
SELECT @SQL = 'SELECT artistID, artistName FROM ' + @artistTable
SELECT @SQL = @SQL + ' WHERE artistID = ' + CAST(@artistID AS VARCHAR)
EXEC(@SQL)
```

**Run it with:**
EXEC dbo.uspGetArtist @artistID = 155;


### 🧠 Section 2: SQL Views & Materialized Views

#### ✅ What Is an SQL View?

An **SQL View** is a **virtual table** created by a query that pulls specific columns from one or more tables. It **does not store data**, but dynamically rebuilds the result set each time it's queried.

---

#### 🧾 Why Use Views?

* **Simplify complex queries** by encapsulating logic.
* **Control data exposure** (e.g., show only non-sensitive fields).
* **Provide real-time, up-to-date** results.
* **Can be used inside other queries** (nested views).

---

#### 🛠️ SQL View Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
````

* `CREATE VIEW` – defines the view.
* `SELECT` – specifies which columns to include.
* `WHERE` – filters rows as needed.

---

#### 🔗 Views Using JOIN

Views can include `JOIN`s to combine data from multiple tables:

```sql
CREATE VIEW combined_view AS
SELECT a.artistName, b.albumTitle
FROM tblArtist a
JOIN tblAlbum b ON a.artistID = b.artistID;
```

---

#### 📋 Example View

**Original Table: `customer_list`**

| customer\_id | birthdate | location      | age | marital\_status |
| ------------ | --------- | ------------- | --- | --------------- |
| Harry        | 29 Jan    | Portland      | 29  | Single          |
| Jack         | 09 May    | Ohio          | 32  | Married         |
| Jaime        | 20 Sept   | Detroit       | 24  | Single          |
| Rob          | 29 Nov    | San Francisco | 35  | Married         |

**View Definition:**

```sql
CREATE VIEW birthday_list AS
SELECT customer_id, birthdate, location
FROM customer_list;
```

**Querying the View:**

```sql
SELECT * FROM birthday_list;
```

**Result:**

| customer\_id | birthdate | location      |
| ------------ | --------- | ------------- |
| Harry        | 29 Jan    | Portland      |
| Jack         | 09 May    | Ohio          |
| Jaime        | 20 Sept   | Detroit       |
| Rob          | 29 Nov    | San Francisco |

---

#### 🗂️ Materialized Views

A **Materialized View** stores the **actual result** of the query physically on disk. Unlike regular views, they do **not reflect real-time changes** unless refreshed.

**Use Cases:**

* Point-in-time reporting
* Data warehousing
* Performance optimization (heavy queries pre-executed)

**Syntax:**

CREATE MATERIALIZED VIEW lastTransactions AS
SELECT payroll_check_amt, payroll_trans_date
FROM PAYROLL;


### 🧠 Section 3: SQL INNER JOIN

#### ✅ What Is an INNER JOIN?

An **INNER JOIN** (also known as a **simple join**) returns records that have **matching values in both tables** based on a specified condition. It only retrieves data from rows where the **join condition is true**.

---

#### 🔄 INNER JOIN Syntax

```sql
SELECT table1.column1, table2.column2, ...
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;
````

---

#### 📋 Example: Albums and Genres

**Album Table (`tblAlbum`):**

| albumID | artistID | albumTitle             | releaseDate | genreID |
| ------- | -------- | ---------------------- | ----------- | ------- |
| 15      | 30       | Rattle and Hum         | 1988        | 27      |
| 25      | 90       | Folk Favorites         | 1993        | 36      |
| 30      | 95       | Mozart's Greatest Hits | 2005        | 12      |

**Genre Table (`tblGenre`):**

| genreID | genre     |
| ------- | --------- |
| 27      | Rock      |
| 36      | Folk      |
| 12      | Classical |

**Query:**

```sql
SELECT tblAlbum.albumTitle, tblGenre.genre
FROM tblAlbum
INNER JOIN tblGenre
ON tblAlbum.genreID = tblGenre.genreID;
```

**Result:**

| albumTitle             | genre     |
| ---------------------- | --------- |
| Rattle and Hum         | Rock      |
| Folk Favorites         | Folk      |
| Mozart's Greatest Hits | Classical |

---

#### 🛠️ Keyword Breakdown

* **SELECT**: Specify which columns to retrieve (must exist in the referenced tables).
* **FROM**: State the **primary (left)** table in the join.
* **INNER JOIN**: Define the **secondary (right)** table to join.
* **ON**: Specify the **condition** that connects both tables (e.g., shared key fields like `genreID`).


### 🧠 Section 4: SQL LEFT JOIN & RIGHT JOIN

#### ✅ What Are LEFT and RIGHT JOINs?

SQL **JOINs** combine records from two or more tables using related columns. The **LEFT JOIN** returns all records from the left table and matched records from the right table. The **RIGHT JOIN** returns all records from the right table and matched ones from the left.

---

#### 🔄 LEFT JOIN Syntax

```sql
SELECT table1.column, table2.column
FROM table1
LEFT JOIN table2
ON table1.key = table2.key;
````

* Retrieves all rows from **table1** (left), and matching rows from **table2** (right).
* **NULL** values will appear for unmatched rows in the right table.

---

#### 📋 LEFT JOIN Example

**Tables:**

**Students**

| last\_name | first\_name | ID |
| ---------- | ----------- | -- |
| Doe        | John        | 12 |
| Smith      | Joe         | 15 |
| Brown      | Jane        | 18 |
| Johnson    | Jim         | 20 |

**Courses**

| Instructor | ID | course\_name | course\_location |
| ---------- | -- | ------------ | ---------------- |
| Jones      | 12 | Biology      | Main             |
| Jones      | 18 | Chemistry    | Online           |
| Miller     | 15 | English      | Main             |
| Miller     | 20 | Writing      | Online           |

**Query:**

```sql
SELECT students.last_name, courses.course_name
FROM students
LEFT JOIN courses
ON students.id = courses.id;
```

**Result:**

| last\_name | course\_name |
| ---------- | ------------ |
| Doe        | Biology      |
| Smith      | English      |
| Brown      | Chemistry    |
| Johnson    | NULL         |

\*Johnson is not enrolled in a course, hence `NULL`.

---

#### 🔄 RIGHT JOIN Syntax

```sql
SELECT table1.column, table2.column
FROM table1
RIGHT JOIN table2
ON table1.key = table2.key;
```

* Retrieves all rows from **table2** (right), and matching rows from **table1** (left).
* **NULL** values will appear for unmatched rows in the left table.

---

#### 📋 RIGHT JOIN Example

```sql
SELECT students.last_name, courses.course_location
FROM students
RIGHT JOIN courses
ON students.id = courses.id AND courses.course_location = 'Main';
```

**Result:**

| last\_name | course\_location |
| ---------- | ---------------- |
| Doe        | Main             |
| Smith      | Main             |
| Brown      | Main             |

\*Returns students taking courses **on the main campus**.

---

#### ⚠️ Tip:

Choose **LEFT JOIN** if you want **all records from the left table** regardless of matches.
Choose **RIGHT JOIN** if you want **all records from the right table** regardless of matches.


### 🧠 Section 5: SQL FULL OUTER JOIN

#### ✅ What Is a FULL OUTER JOIN?

A **FULL OUTER JOIN** returns **all rows from both tables**, filling in `NULL` where there is no match. It's useful when you want to identify **unmatched data** on either side.

---

#### 🔄 FULL OUTER JOIN Syntax

```sql
SELECT table1.column, table2.column
FROM table1
FULL OUTER JOIN table2
ON table1.common_column = table2.common_column;
````

* Returns **matched rows** plus **unmatched rows** from both tables.
* Unmatched cells are filled with `NULL`.

---

#### 📋 Example: Students and Registration

**Student Table**

| last\_name | first\_name | id  | major   |
| ---------- | ----------- | --- | ------- |
| Doe        | John        | 012 | Biology |
| Smith      | Joe         | 015 | English |
| Brown      | Jane        | 018 | Biology |
| Johnson    | Jim         | 210 | English |
| James      | Peter       | 202 | Biology |
| Jones      | Paul        | 203 | English |

**Registration Table**

| instructor | course\_name | course\_location | id  |
| ---------- | ------------ | ---------------- | --- |
| Jones      | Biology101   | Main             | 012 |
| Jones      | Biology101   | Main             | 202 |
| Jones      | Chemistry101 | Online           | 018 |
| Miller     | English101   | Main             | 015 |
| Miller     | Writing101   | Online           | 210 |

**Query:**

```sql
SELECT student.id, student.major, registration.course_name
FROM student
FULL OUTER JOIN registration
ON student.id = registration.id;
```

**Result:**

| id  | major   | course\_name |
| --- | ------- | ------------ |
| 012 | Biology | Biology101   |
| 015 | English | English101   |
| 018 | Biology | Chemistry101 |
| 210 | English | Writing101   |
| 202 | Biology | Biology101   |
| 203 | English | NULL         |

\*Paul Jones (ID 203) has **not registered** for any course — highlighted by `NULL`.

---

#### ⚙️ FULL OUTER JOIN with WHERE

**Query:**

```sql
SELECT student.id, student.major, registration.course_name
FROM student
FULL OUTER JOIN registration
ON student.id = registration.id
WHERE student.major = 'Biology';
```

**Result:**

| id  | major   | course\_name |
| --- | ------- | ------------ |
| 012 | Biology | Biology101   |
| 018 | Biology | Chemistry101 |
| 202 | Biology | Biology101   |

---

#### ⚠️ Tip:

Use `FULL OUTER JOIN` when you need a **complete picture**, including:

* Who’s **missing data** in either table
* **Unmatched records** for follow-up
* **Combining datasets** with partial overlap


### 🧠 Section 6: SQL CROSS JOIN (Cartesian Product)

#### ✅ What Is a CROSS JOIN?

A **CROSS JOIN** in SQL returns the **Cartesian product** of two tables: every row from the first table is **paired with every row** from the second table.

---

#### 🧮 Cartesian Product Explained

Given:

**A** = (4, 5, 6)  
**B** = (7, 8)

**A × B** =  
{(4,7), (4,8), (5,7), (5,8), (6,7), (6,8)}

*Total Rows = rows_A × rows_B*

---

#### 🔁 CROSS JOIN Syntax

```sql
-- Explicit CROSS JOIN
SELECT * FROM TableA
CROSS JOIN TableB;

-- Implicit CROSS JOIN (not recommended for clarity)
SELECT * FROM TableA, TableB;
````

> 🧠 Use `CROSS JOIN` explicitly to avoid confusion.

---

#### 📋 Example: Customers and Orders

**Customer Table**

| CustomerName | CustomerEmail                                   |
| ------------ | ----------------------------------------------- |
| John Doe     | [doe.john@mail.com](mailto:doe.john@mail.com)   |
| Jane Doe     | [doe.jane@mail.com](mailto:doe.jane@mail.com)   |
| Sally Doe    | [doe.sally@mail.com](mailto:doe.sally@mail.com) |

**Order Table**

| OrderId | ItemId |
| ------- | ------ |
| 12345   | 738    |
| 98255   | 906    |
| 55556   | 329    |

**Query:**

```sql
SELECT *
FROM Customer
CROSS JOIN Orders;
```

**Result:**

| CustomerName | CustomerEmail                                   | OrderId | ItemId |
| ------------ | ----------------------------------------------- | ------- | ------ |
| John Doe     | [doe.john@mail.com](mailto:doe.john@mail.com)   | 12345   | 738    |
| Jane Doe     | [doe.jane@mail.com](mailto:doe.jane@mail.com)   | 12345   | 738    |
| Sally Doe    | [doe.sally@mail.com](mailto:doe.sally@mail.com) | 12345   | 738    |
| John Doe     | [doe.john@mail.com](mailto:doe.john@mail.com)   | 98255   | 906    |
| ...          | ...                                             | ...     | ...    |

*3 customers × 3 orders = 9 rows*

---

#### 🛠️ Practical Use Cases

* **Generating all combinations** (e.g., product × size, employee × shift)
* **Testing joins** or **data completeness**
* **Building grid layouts** or datasets for **external analysis** (e.g., Excel)
* **Data dumping** for temporary exploration

---

#### ⚠️ Caution:

* **Avoid unintentional CROSS JOINs** — can explode to massive result sets.
* Be aware of performance cost:
  *10,000 rows × 40,000 rows = 400 million rows!*

```sql
-- Example for all combinations of shoe brands and sizes
SELECT Brand, Size
FROM ShoeBrands
CROSS JOIN ShoeSizes;
```

---

#### 🧩 Key Takeaway

*CROSS JOIN = ALL combinations*
Use for specific needs like testing, grid creation, or exhaustive pairings — **not** as a default join strategy.


### 🧠 Section 7: SQL `UNION` vs `JOIN`

#### ✅ UNION vs JOIN: What’s the Difference?

| Feature         | `UNION`                                | `JOIN`                                |
|----------------|-----------------------------------------|----------------------------------------|
| Output Style    | **Stacks rows vertically**              | **Combines columns horizontally**      |
| Use Case        | Merge similar data sets from two tables | Merge related data based on a key      |
| Duplicates      | Removes by default (`UNION`); keep with `UNION ALL` | Returns only matching rows (e.g., `INNER JOIN`) |
| Requirements    | Tables must have same number & type of columns | Tables must have a related column/key |

---

#### ➕ `UNION` Overview

**Combines rows from two or more `SELECT` queries.**  
Default behavior removes duplicates unless `UNION ALL` is used.

**Syntax:**

```sql
SELECT column1, column2 FROM table1
UNION
SELECT column1, column2 FROM table2;
````

---

#### 📋 `UNION` Example

**Tables:**

`undergrad_college`

| studentID | studentName     | studentEmail                                                          |
| --------- | --------------- | --------------------------------------------------------------------- |
| 1004      | Jane Eyre       | [eyre.jane@mycollege.edu](mailto:eyre.jane@mycollege.edu)             |
| 1005      | Sherlock Holmes | [holmes.sherlock@mycollege.edu](mailto:holmes.sherlock@mycollege.edu) |
| 1006      | Rey Skywalker   | [skywalker.rey@mycollege.edu](mailto:skywalker.rey@mycollege.edu)     |
| 1007      | Meat Loaf       | [meatloaf@mycollege.edu](mailto:meatloaf@mycollege.edu)               |

`business_college`

| studentID | studentName    | studentEmail                                                          |
| --------- | -------------- | --------------------------------------------------------------------- |
| 1004      | Jane Eyre      | [eyre.jane@mycollege.edu](mailto:eyre.jane@mycollege.edu)             |
| 2095      | Harriet Tubman | [harriet.tubman@buscollege.edu](mailto:harriet.tubman@buscollege.edu) |
| 2099      | Andres Segovia | [andres.segovia@buscollege.edu](mailto:andres.segovia@buscollege.edu) |
| 1007      | Meat Loaf      | [meatloaf@mycollege.edu](mailto:meatloaf@mycollege.edu)               |

**Query:**

```sql
SELECT * FROM undergrad_college
UNION
SELECT * FROM business_college
WHERE studentID NOT IN
(SELECT studentID FROM undergrad_college);
```

**Result:**

| studentID | studentName     | studentEmail                                                          |
| --------- | --------------- | --------------------------------------------------------------------- |
| 1004      | Jane Eyre       | [eyre.jane@mycollege.edu](mailto:eyre.jane@mycollege.edu)             |
| 1005      | Sherlock Holmes | [holmes.sherlock@mycollege.edu](mailto:holmes.sherlock@mycollege.edu) |
| 1006      | Rey Skywalker   | [skywalker.rey@mycollege.edu](mailto:skywalker.rey@mycollege.edu)     |
| 1007      | Meat Loaf       | [meatloaf@mycollege.edu](mailto:meatloaf@mycollege.edu)               |
| 2095      | Harriet Tubman  | [harriet.tubman@buscollege.edu](mailto:harriet.tubman@buscollege.edu) |
| 2099      | Andres Segovia  | [andres.segovia@buscollege.edu](mailto:andres.segovia@buscollege.edu) |

---

#### 🔗 `JOIN` Overview

**Combines rows from multiple tables based on related columns.**

**Syntax:**

```sql
SELECT table1.columnA, table2.columnB
FROM table1
JOIN table2
ON table1.key = table2.key;
```

---

#### 📋 `JOIN` Example

**Tables:**

`alumni`

| alum\_ID | alumni\_name |
| -------- | ------------ |
| 4005     | Bill         |
| 4010     | Alice        |
| 4015     | Jane         |
| 4020     | Paul         |
| 4025     | Jack         |

`alumni_giving`

| alum\_ID | amount |
| -------- | ------ |
| 4005     | 100    |
| 4025     | 500    |
| 4015     | 1500   |

**Query:**

```sql
SELECT alumni.alumni_name, alumni_giving.amount
FROM alumni
JOIN alumni_giving
ON alumni.alum_ID = alumni_giving.alum_ID;
```

**Result:**

| alumni\_name | amount |
| ------------ | ------ |
| Bill         | 100    |
| Jack         | 500    |
| Jane         | 1500   |

---

#### 🧠 Key Takeaways

* Use `UNION` to **combine similar rows** from different tables.
* Use `JOIN` to **merge related data** using common keys.
* Always check data types and structures for compatibility.

### 🧠 Section 8: SQL SELF-JOIN

#### ✅ What Is a SELF-JOIN?

A **SELF-JOIN** compares a table to **itself** by creating **two aliases** for the same table. It's useful for:
- Matching rows based on internal relationships
- Comparing rows within the same dataset
- Creating **running totals** or **running counts**

---

#### 🛠️ SELF-JOIN Syntax

```sql
SELECT ...
FROM table AS alias1, table AS alias2
WHERE alias1.column = alias2.column
AND alias1.column2 <> alias2.column2;
````

* Use **aliases (e.g., e1, e2)** to differentiate instances of the same table.
* Use `DISTINCT` if needed to avoid duplicate results.

---

#### 📋 Example: Employees with Same Job Code

```sql
SELECT DISTINCT e1.employeeName, e1.jobTitle, e1.jobCode
FROM Employee AS e1, Employee AS e2
WHERE e1.jobCode = e2.jobCode
AND e1.employeeName <> e2.employeeName
ORDER BY e1.jobCode, e1.employeeName;
```

\*Returns employees who **share the same job code** with others.

---

#### 🔢 Running Count with SELF-JOIN

**Query:**

```sql
SELECT COUNT(p1.itemID) AS itemNum, p1.itemName, p1.itemID
FROM Products p1
INNER JOIN Products p2
ON p1.itemID >= p2.itemID
GROUP BY p1.itemName, p1.itemID
ORDER BY 1;
```

**Result:**

| itemNum | itemName | itemID |
| ------- | -------- | ------ |
| 1       | Fedora   | FEDE   |
| 2       | Panama   | PANA   |
| 3       | Bowler   | BOWL   |
| 4       | Boater   | BOAT   |

\*Creates a **row-by-row index** based on ordering.

---

#### ➕ Running Total with SELF-JOIN

**Query:**

```sql
SELECT e1.employeeID, e1.jobCode, e1.checkDate,
SUM(e2.hoursWorked) AS RunningTOTAL
FROM Employee AS e1, Employee AS e2
WHERE e2.checkDate < e1.checkDate
GROUP BY e1.employeeID, e1.checkDate;
```

**Result:**

| employeeID | jobCode | checkDate | RunningTOTAL |
| ---------- | ------- | --------- | ------------ |
| 123085     | A2027   | (date)    | 38.75        |
| 143585     | B5057   | (date)    | 72.25        |
| 156580     | B5057   | (date)    | 90.75        |
| ...        | ...     | ...       | ...          |

\*Calculates a **cumulative total** of hours worked by check date.

---

#### 🧠 Tip:

Use `AS` to alias the table and **clarify which instance** of the table each field is coming from. This is essential for accurate comparisons.


### 🧠 Section 9: SQL Scripts

#### ✅ What Is an SQL Script?

An **SQL script** is a collection of SQL commands stored in a text file and designed to perform a specific task — often **repetitive** or **routine** in nature.

---

#### 📦 Advantages of SQL Scripts

- **Ease of Use**: Save, load, and rerun scripts as needed.
- **Consistency**: Produces the same results every time.
- **Reduced Errors**: Minimizes typos and manual mistakes.
- **Scheduled Operation**: Can be automated via schedulers or cron jobs.

---

#### 🔁 Common Use Cases

| Use Case        | Description                                                  |
|------------------|--------------------------------------------------------------|
| **Backups**       | Automate saving database states to disk for recovery         |
| **Reports**       | Generate regular summaries or KPIs for business insights     |
| **Updates**       | Perform batch updates or data insertions                     |
| **Synchronization** | Align data across multiple servers/regions                   |

---

#### 🧪 Sample Script: Data Insertion

```sql
INSERT INTO Test VALUES ('Gary', 'Newton', 33, 'Male');
INSERT INTO Test VALUES ('Debbie', 'Parker', 25, 'Female');
INSERT INTO Test VALUES ('April', 'Walker', 31, 'Female');
````

*Adds new records to the `Test` table.*

---

#### 💾 Sample Script: Database Backup (SQL Server)

```sql
BACKUP DATABASE Test
TO DISK = 'C:\Backups\Test.bak'
WITH COPY_ONLY;
```

*Saves a backup of the `Test` database to a file on disk.*

---

#### ⚙️ Scheduling SQL Scripts

* Use **SQL Server Agent**, **cron jobs**, or **task scheduler** to automate.
* Ideal for nightly backups, weekly reports, and routine syncs.


### 🧠 Section 10: SQL Stored Procedures

#### ✅ What Is a Stored Procedure?

A **Stored Procedure** is a **precompiled set of SQL statements** that:
- Accepts **parameters**
- Performs a **defined task** (e.g., querying, updating)
- Hides complex logic from end users
- Adds **security** by limiting direct table access

---

#### 🛠️ Basic Syntax (SQL Server)

```sql
CREATE PROC [Procedure_Name]
    @parameter_name datatype
AS
BEGIN
    -- SQL statements go here
END;
````

---

#### 📥 Example: Fetch Employee Details

```sql
CREATE PROCEDURE getEmployee
    @employeeID VARCHAR(50)
AS
BEGIN
    SELECT employeeID, payRate, hourlyWage, empStatus
    FROM tblEmployee
    WHERE employeeID = @employeeID;
END;
```

**Run the procedure:**

```sql
EXEC getEmployee 'AB772';
```

---

#### 📦 Variables in Procedures

Use `DECLARE` to define internal variables.

```sql
DECLARE @runDate DATETIME;
SET @runDate = GETDATE();
```

---

#### 🧪 Example: Conditional Logic with `IF EXISTS`

```sql
CREATE PROC updateEmployee
    @employeeID VARCHAR(50)
AS
BEGIN
    DECLARE @runDate DATETIME;
    SET @runDate = GETDATE();

    IF EXISTS (
        SELECT 1
        FROM tblEmployee
        WHERE employeeID = @employeeID
    )
    BEGIN
        UPDATE tblEmployee
        SET runDate = @runDate
        WHERE employeeID = @employeeID;
    END
    ELSE
    BEGIN
        INSERT INTO tempTable (employeeID)
        VALUES (@employeeID);
    END
END;
```

---

#### 🔐 Error Handling: TRY / CATCH

```sql
CREATE PROC emp_errortest
    @employeeID VARCHAR(50)
AS
BEGIN
    DECLARE @runDate DATETIME;
    SET @runDate = GETDATE();

    BEGIN TRAN
    BEGIN TRY
        UPDATE tblEmployee
        SET runDate = @runDate
        WHERE employeeID = @employeeID;
        COMMIT TRAN;
    END TRY
    BEGIN CATCH
        ROLLBACK TRAN;
        PRINT 'Big-time error, nothing done';
    END CATCH
END;
```

---

#### ⚠️ Tip:

* Parameters are passed with `@`
* Use `DECLARE` for internal variables
* Use `TRY...CATCH` for safe execution
* Add `OUT` to parameters to return values

```sql
@employeeID VARCHAR(50) OUT
```

---

#### 🧠 Key Takeaways

* Stored procedures **modularize SQL logic**
* **Secure** access to sensitive data
* Support **dynamic, parameterized execution**
* **Handle errors** gracefully with `TRY...CATCH`


### 🧠 Section 11: SQL Triggers

#### ✅ What Is a Trigger?

A **trigger** is a **stored set of SQL instructions** that **executes automatically** in response to specific **DML events** such as:

- `INSERT`
- `UPDATE`
- `DELETE`

Triggers can fire:
- `BEFORE`
- `AFTER`
- `INSTEAD OF` these DML actions.

---

#### 🔁 Use Case

Ensure **data consistency** across multiple tables. For example, inserting a new employee into `hr_table` should automatically insert related info into `benefits_table` and `payroll_table`.

---

#### 🛠️ Syntax: Basic Trigger (AFTER INSERT)

```sql
CREATE TRIGGER new_employee
AFTER INSERT ON hr_table
BEGIN
  INSERT INTO benefits_table (name, street, workid)
  VALUES ('john', '123 Any Street', '1022');
END;
````

---

#### 🧱 Compound Trigger Example

Insert into multiple tables from one trigger.

```sql
CREATE TRIGGER new_employee
AFTER INSERT ON hr_table
BEGIN ATOMIC
  INSERT INTO benefits_table (name, street, workid)
  VALUES ('john', '123 Any Street', '1022');

  INSERT INTO payroll_table (name, street, workid)
  VALUES ('john', '123 Any Street', '1022');
END;
```

---

#### 🗑️ Delete Trigger

Automatically removes related records upon deletion.

```sql
CREATE TRIGGER delete_employee
AFTER DELETE ON hr_table
BEGIN
  DELETE FROM benefits_table WHERE workid = '1022';
  DELETE FROM payroll_table WHERE workid = '1022';
END;
```

---

#### ♻️ Update Trigger

Ensures that changes in one table are mirrored in others.

```sql
CREATE TRIGGER update_employee
AFTER UPDATE ON hr_table
BEGIN
  UPDATE benefits_table
  SET name = 'newName'
  WHERE workid = '1022';

  UPDATE payroll_table
  SET name = 'newName'
  WHERE workid = '1022';
END;
```

---

#### ⚠️ Tip:

* A table can have **multiple triggers**.
* Use **`BEGIN ATOMIC ... END`** for compound operations.
* Triggers help **automate workflows** and **enforce integrity** across tables.


### 🧠 Section 12: SQL Intro to Triggers

#### ✅ What Is SQL?

**Structured Query Language (SQL)** is a standardized language for **interacting with relational databases**. It allows for:
- **Storing**, **retrieving**, and **sorting** data
- **Searching**, **updating**, and **manipulating** information

> Originally developed by **IBM (1970s)** and later commercialized by **Oracle (1979)**.

---

#### 🔔 What Is an SQL Trigger?

An **SQL Trigger** is a **stored procedure** that **automatically executes** (or "fires") in response to specific events on a table or view:
- INSERT
- UPDATE
- DELETE

A trigger waits for the specified event and performs defined actions when it occurs — **like a timer ringing when a cake finishes baking**.

---

#### 🔁 Uses of SQL Triggers

| Purpose              | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **Deriving Info**    | Auto-calculate or generate new data when other data changes                 |
| **Referential Integrity** | Ensure related records across tables are synchronized                    |
| **Event Logging**    | Record every action or event that modifies the database                     |
| **Auditing**         | Compare changes to expected behavior or patterns                            |
| **Replication**      | Copy updates or inserts to another table or database                        |
| **Security**         | Check permissions and restrict unauthorized changes                         |
| **Error Handling**   | Detect and recover from runtime issues automatically                        |

---

#### 🛠️ SQL Trigger Syntax

```sql
CREATE [OR REPLACE] TRIGGER TriggerName
{BEFORE | AFTER | INSTEAD OF}
{INSERT [OR] | UPDATE [OR] | DELETE}
[OF ColumnName]
ON TableName
[REFERENCING OLD AS Old NEW AS New]
[FOR EACH ROW]
WHEN (logical_condition)
DECLARE
    -- variable declarations
BEGIN
    -- executable statements
EXCEPTION
    -- error handling statements
END;
````

---

#### 🔍 Syntax Breakdown

* **`CREATE TRIGGER`**: Defines the trigger
* **`BEFORE | AFTER | INSTEAD OF`**: Specifies when the trigger fires
* **`INSERT | UPDATE | DELETE`**: Specifies the DML event
* **`REFERENCING OLD AS / NEW AS`**: Access old/new values for comparison
* **`WHEN`**: Conditional clause (optional)
* **`BEGIN ... END`**: Logic block for what happens when the trigger fires



### 🧠 Section 13: SQL Common Table Expressions (CTEs)

#### ✅ What Is a CTE?

A **Common Table Expression (CTE)** is a **temporary, named result set** defined within the execution scope of a single SQL statement. It simplifies complex queries, improves readability, and can be reused in the same query.

---

#### 🛠️ Basic CTE Syntax

```sql
WITH cte_name AS (
    SELECT ...
    FROM ...
    WHERE ...
)
SELECT *
FROM cte_name;
````

*Must appear **before** SELECT, INSERT, UPDATE, or DELETE statements.*

---

#### 📋 Example: Filter Product Scale from Product Line

```sql
WITH classic_cars AS (
    SELECT productLine, productScale, productDescription
    FROM products
    WHERE productLine = 'Classic Cars'
)
SELECT *
FROM classic_cars
WHERE productScale = '1:12';
```

---

#### 🔗 Multiple CTEs

Use **commas** to separate multiple CTEs:

```sql
WITH valid_orders AS (
    SELECT orderNumber, orderDate, status, customerNumber
    FROM orders
    WHERE status <> 'Cancelled'
),
order_details AS (
    SELECT o.orderNumber, d.priceEach, o.customerNumber
    FROM valid_orders o
    LEFT JOIN orderdetails d ON d.orderNumber = o.orderNumber
)
SELECT 
    orderNumber AS ORDER_NUMBER,
    SUM(priceEach) AS TOTAL,
    c.customerNumber AS CUSTOMER_NUMBER,
    c.customerName AS CUSTOMER_NAME
FROM order_details
LEFT JOIN customers c ON c.customerNumber = order_details.customerNumber
GROUP BY orderNumber;
```

---

#### 🏗️ CTE with CREATE VIEW

```sql
CREATE VIEW my_view AS
WITH vendors AS (
    SELECT * FROM products WHERE productVendor = 'Carousel DieCast Legends'
)
SELECT od.productCode, od.priceEach, v.productLine
FROM vendors v
LEFT JOIN orderdetails od ON v.productCode = od.productCode;
```

---

#### 🔁 Recursive CTE

Used for **hierarchical data** (e.g., org charts).

```sql
WITH RECURSIVE hierarchy AS (
    SELECT manager_id, staff_id, first_name
    FROM staff
    WHERE manager_id IS NULL

    UNION ALL

    SELECT s.manager_id, s.staff_id, s.first_name
    FROM staff s
    INNER JOIN hierarchy h ON h.staff_id = s.manager_id
)
SELECT *
FROM hierarchy;
```

---

#### ⚠️ Tip: Recursive Depth Limit

MySQL defaults to **1000 recursions**. You can change this with:

```sql
SET max_recursion_depth = 2000;
```

Make sure the recursion **terminates** (e.g., check `manager_id IS NULL`).

---

#### 🧠 Key Takeaways

* CTEs simplify and modularize queries.
* They are defined using `WITH`.
* You can create **multiple CTEs** and **recursive CTEs**.
* CTEs are usable in `SELECT`, `UPDATE`, `INSERT`, `DELETE`, `CREATE VIEW`, etc.

To ensure data integrity and accuracy in SQL databases, constraints are applied directly within the table schema. These constraints enforce rules on the data, such as mandating the presence of a value, ensuring uniqueness, or restricting the range of permissible values.

---

### 🧠 Section 14: SQL Constraining Data

#### ✅ What Are Constraints?

**SQL constraints** are rules applied to **columns in a table** to ensure the **accuracy and reliability** of data. They help:

* Enforce **valid input**
* Prevent **incorrect or duplicate** data
* Maintain **data integrity**

> Constraints are defined at the time of **table creation** or can be added later via `ALTER TABLE`.

---

#### 🧩 Common SQL Constraints

| Constraint      | Description                                                          |
| --------------- | -------------------------------------------------------------------- |
| **NOT NULL**    | Ensures a column **cannot contain NULL values**                      |
| **UNIQUE**      | Ensures **all values in a column are different**                     |
| **PRIMARY KEY** | A combination of **NOT NULL** and **UNIQUE**                         |
| **FOREIGN KEY** | Enforces **referential integrity** between tables                    |
| **CHECK**       | Ensures that all values in a column **satisfy a specific condition** |
| **DEFAULT**     | Sets a **default value** for a column when no value is specified     |

---

#### 🛠️ SQL Constraint Syntax Examples

**Example 1: NOT NULL + Length Limit**

```sql
name VARCHAR(15) NOT NULL,
```

> Ensures `name` cannot be NULL and must be ≤ 15 characters.

**Example 2: UNIQUE Employee ID**

```sql
id CHAR(6) UNIQUE,
```

> Ensures all `id` values are unique and fixed at 6 characters.

**Example 3: CHECK Constraint for Feedback Length**

```sql
feedback VARCHAR(2500),
CHECK (LENGTH(feedback) > 150),
```

> Enforces that feedback must be longer than 150 characters.

---

#### 📍 Where Do Constraints Go?

Constraints are written **after the data type** in the `CREATE TABLE` statement:

```sql
CREATE TABLE employees (
    id CHAR(6) UNIQUE,
    name VARCHAR(15) NOT NULL,
    feedback VARCHAR(2500),
    CHECK (LENGTH(feedback) > 150)
);
```

---

#### 🧠 Lesson Summary

SQL **constraints** help maintain **data integrity** and **enforce rules** about what data is allowed in a column. Use them to:

* Ensure required fields are not empty (`NOT NULL`)
* Prevent duplicates (`UNIQUE`)
* Enforce specific conditions (`CHECK`)
* Set defaults and define relationships (`DEFAULT`, `FOREIGN KEY`)
