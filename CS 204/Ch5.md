### Section 1: SQL Complex Queries

**Definition**
SQL complex queries retrieve data from multiple tables using advanced clauses and logic. These include **joins**, **unions**, and **stored procedures**, crucial for managing large relational databases.

---

**INNER JOIN**

* Returns **only matching records** from both tables.

```sql
SELECT *
FROM tblAlbum
INNER JOIN tblArtist ON tblAlbum.artistID = tblArtist.artistID;
```

**Result:** Only rows where `artistID` matches in both tables.

---

**LEFT OUTER JOIN**

* Returns **all rows from the left table** plus matching rows from the right.

```sql
SELECT *
FROM tblArtist
LEFT OUTER JOIN tblAlbum ON tblArtist.artistID = tblAlbum.artistID;
```

**Result:** Includes all artists, even those with no albums.

---

**RIGHT OUTER JOIN**

* Returns **all rows from the right table** plus matching rows from the left.

```sql
SELECT *
FROM tblArtist
RIGHT OUTER JOIN tblAlbum ON tblArtist.artistID = tblAlbum.artistID;
```

**Result:** Includes all albums, even those without a known artist.

---

**FULL OUTER JOIN (UNMATCHED ROWS)**

* Returns **all rows from both tables**.

```sql
SELECT *
FROM tblArtist
FULL OUTER JOIN tblAlbum ON tblArtist.artistID = tblAlbum.artistID
WHERE tblArtist.artistID IS NULL OR tblAlbum.artistID IS NULL;
```

**Result:** Unmatched records from either table.

---

**UNION**

* Combines **results from multiple SELECT statements** into new rows.

```sql
SELECT artistName FROM tblArtist
UNION
SELECT albumTitle FROM tblAlbum;
```

**Result:** All distinct records combined vertically.

---

**STORED PROCEDURES**

* Reusable SQL blocks for **controlled, parameterized access**.

```sql
CREATE PROCEDURE uspGetArtist
  @artistTable VARCHAR(100),
  @artistID INT
AS
BEGIN
  DECLARE @SQL VARCHAR(1000)
  SET @SQL = 'SELECT artistID, artistName FROM ' + @artistTable +
             ' WHERE artistID = ' + CAST(@artistID AS VARCHAR)
  EXEC(@SQL)
END
```

**Execute:**

```sql
EXEC uspGetArtist @artistTable='tblArtist', @artistID=155;
```

---

**Lesson Summary**

* **INNER JOIN**: Only matching records.
* **LEFT OUTER JOIN**: All left table rows + matched right.
* **RIGHT OUTER JOIN**: All right table rows + matched left.
* **FULL OUTER JOIN**: All rows from both; useful for unmatched detection.
* **UNION**: Combines records into new rows.
* **Stored Procedures**: Controlled, parameter-driven queries for reusability and security.

### Section 2: SQL INNER JOIN

**Definition**
The **INNER JOIN** (also known as a *simple join*) retrieves only those records where there is a match between columns in both tables based on a specified condition.

---

**Syntax**

```sql
SELECT table1.columnA, table2.columnB
FROM table1
INNER JOIN table2
ON table1.commonField = table2.commonField;
```

---

**Example**

**Tables:**

`tblAlbum`

| albumID | artistID | albumTitle             | releaseDate | genreID |
| ------- | -------- | ---------------------- | ----------- | ------- |
| 15      | 30       | Rattle and Hum         | 1988        | 27      |
| 25      | 90       | Folk Favorites         | 1993        | 36      |
| 30      | 95       | Mozart's Greatest Hits | 2005        | 12      |

`tblGenre`

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

**Output:**

| albumTitle             | genre     |
| ---------------------- | --------- |
| Rattle and Hum         | Rock      |
| Folk Favorites         | Folk      |
| Mozart's Greatest Hits | Classical |

---

**Key Concepts:**

* Only rows **with matching genreID** values in both `tblAlbum` and `tblGenre` are returned.
* Field names should be **prefixed** with table names to avoid ambiguity (e.g., `tblAlbum.genreID`).
* INNER JOIN is used for **data analysis**, **reporting**, and **relational linking** between datasets.

---

**Lesson Summary**

* **INNER JOIN** pulls data from multiple tables **only when records match** a specified condition.
* It’s used to merge rows based on a **shared key**, like `genreID` in this example.
* INNER JOIN returns **intersection** data, making it essential for analyzing **related** database entries.

### Section 3: SQL LEFT JOIN & RIGHT JOIN

**Definition**
SQL JOINs combine data from two or more tables using a common field. **LEFT JOIN** returns all records from the left table and matched records from the right. **RIGHT JOIN** returns all records from the right table and matched records from the left.

---

**LEFT JOIN Syntax**

```sql
SELECT table1.columnA, table2.columnB
FROM table1
LEFT JOIN table2
ON table1.sharedField = table2.sharedField;
```

**RIGHT JOIN Syntax**

```sql
SELECT table1.columnA, table2.columnB
FROM table1
RIGHT JOIN table2
ON table1.sharedField = table2.sharedField;
```

---

**Example Tables**

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

---

**LEFT JOIN Example**

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

**Interpretation:**
All students are listed. Johnson isn’t enrolled in a course, so his `course_name` is NULL.

---

**RIGHT JOIN Example**

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

**Interpretation:**
Only courses at the *Main* campus are shown, with their enrolled students.

---

**Lesson Summary**

* **LEFT JOIN**: returns all rows from the left table and matched rows from the right. Non-matches return NULLs.
* **RIGHT JOIN**: returns all rows from the right table and matched rows from the left.
* Useful for querying data with partial matches or ensuring all entities from one side (e.g., all students or all courses) appear in reports.

### Section 4: SQL FULL OUTER JOIN

**Definition**
A **FULL OUTER JOIN** returns **all records** when there is a match in **either** left or right table. Unmatched records from each side will have `NULL` values for the other side’s columns.

---

**FULL OUTER JOIN Syntax**

```sql
SELECT table1.columnA, table2.columnB
FROM table1
FULL OUTER JOIN table2
ON table1.commonField = table2.commonField;
```

---

**Example Tables**

**Student**

| last\_name | first\_name | id  | major   |
| ---------- | ----------- | --- | ------- |
| Doe        | John        | 012 | Biology |
| Smith      | Joe         | 015 | English |
| Brown      | Jane        | 018 | Biology |
| Johnson    | Jim         | 210 | English |
| James      | Peter       | 202 | Biology |
| Jones      | Paul        | 203 | English |

**Registration**

| instructor | course\_name | course\_location | id  |
| ---------- | ------------ | ---------------- | --- |
| Jones      | Biology101   | Main             | 012 |
| Jones      | Biology101   | Main             | 202 |
| Jones      | Chemistry101 | Online           | 018 |
| Miller     | English101   | Main             | 015 |
| Miller     | Writing101   | Online           | 210 |

---

**FULL OUTER JOIN Example**

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

**Interpretation:**
Paul Jones (id: 203) hasn’t registered for a course. His unmatched row is still returned due to FULL OUTER JOIN.

---

**FULL OUTER JOIN with WHERE Clause**

```sql
SELECT student.id, student.major, registration.course_name
FROM student
FULL OUTER JOIN registration
ON student.id = registration.id
WHERE student.major = 'Biology';
```

**Filtered Result:**

| id  | major   | course\_name |
| --- | ------- | ------------ |
| 012 | Biology | Biology101   |
| 018 | Biology | Chemistry101 |
| 202 | Biology | Biology101   |

---

**Lesson Summary**

* **FULL OUTER JOIN** returns **all rows from both tables**.
* Unmatched rows from either side result in `NULL` values.
* Helpful for finding **incomplete data links**, such as unregistered students.
* Use **WHERE** and **ORDER BY** to refine large results and make queries more targeted.

### Section 5: SQL CROSS JOIN

**Definition**
A **CROSS JOIN** returns **every possible combination** of rows from two tables. If Table A has *m* rows and Table B has *n* rows, the result will be *m × n* rows.

---

**CROSS JOIN Syntax**

```sql
SELECT *
FROM TableA
CROSS JOIN TableB;
```

*Or implicitly (not recommended for clarity):*

```sql
SELECT *
FROM TableA, TableB;
```

---

**Example Tables**

**Customer**

| CustomerName | CustomerEmail                                   |
| ------------ | ----------------------------------------------- |
| John Doe     | [doe.john@mail.com](mailto:doe.john@mail.com)   |
| Jane Doe     | [doe.jane@mail.com](mailto:doe.jane@mail.com)   |
| Sally Doe    | [doe.sally@mail.com](mailto:doe.sally@mail.com) |

**Orders**

| OrderId | ItemId |
| ------- | ------ |
| 12345   | 738    |
| 98255   | 906    |
| 55556   | 329    |

---

**Result of `CROSS JOIN`**

```sql
SELECT *
FROM Customer
CROSS JOIN Orders;
```

**Output:**

| CustomerName | CustomerEmail                                   | OrderId | ItemId |
| ------------ | ----------------------------------------------- | ------- | ------ |
| John Doe     | [doe.john@mail.com](mailto:doe.john@mail.com)   | 12345   | 738    |
| Jane Doe     | [doe.jane@mail.com](mailto:doe.jane@mail.com)   | 12345   | 738    |
| Sally Doe    | [doe.sally@mail.com](mailto:doe.sally@mail.com) | 12345   | 738    |
| John Doe     | [doe.john@mail.com](mailto:doe.john@mail.com)   | 98255   | 906    |
| Jane Doe     | [doe.jane@mail.com](mailto:doe.jane@mail.com)   | 98255   | 906    |
| Sally Doe    | [doe.sally@mail.com](mailto:doe.sally@mail.com) | 98255   | 906    |
| John Doe     | [doe.john@mail.com](mailto:doe.john@mail.com)   | 55556   | 329    |
| Jane Doe     | [doe.jane@mail.com](mailto:doe.jane@mail.com)   | 55556   | 329    |
| Sally Doe    | [doe.sally@mail.com](mailto:doe.sally@mail.com) | 55556   | 329    |

---

**Use Cases**

* **Generating full combinations** (e.g., `Brands × Sizes`, `Dates × Resources`)
* **Data completeness checks**
* **Filling matrix/grid templates**
* **Dumping raw data for external analysis**

---

**Warning**

* **Avoid on large tables** unless necessary. A 10k × 40k join = **400 million rows**.
* **Always use CROSS JOIN explicitly** to clarify intent.

---

**Lesson Summary**

* A **CROSS JOIN** = **Cartesian product**: every row from one table with every row from the other.
* SQL syntax uses either `CROSS JOIN` or comma-separated tables.
* Ideal for **exhaustive combinations**, grid population, and diagnostic exports.
* Be cautious with size and performance!

### Section 6: SQL SELF-JOIN

**Buzzwords:** *Self-Join*, *Alias*, *Running Totals*, *Running Counts*

---

**Definition**
A **SELF-JOIN** is a regular join where a table is joined **with itself** using **aliases**. This is used to compare rows within the same table.

---

**Syntax Example: Employees with Same Job Code**

```sql
SELECT DISTINCT e1.employeeName, e1.jobTitle, e1.jobCode
FROM Employee AS e1, Employee AS e2
WHERE e1.jobCode = e2.jobCode
  AND e1.employeeName <> e2.employeeName
ORDER BY e1.jobCode, e1.employeeName;
```

**Explanation:**

* `e1`, `e2`: aliases for the same table
* `DISTINCT`: avoids duplicate row pairs
* `<>`: excludes comparing a row to itself

---

**Application: Running Count**

```sql
SELECT COUNT(p1.itemID) AS itemNum, p1.itemName, p1.itemID
FROM Products p1
INNER JOIN Products p2 ON p1.itemID >= p2.itemID
GROUP BY p1.itemName, p1.itemID
ORDER BY 1;
```

**Use:** Ranks items based on itemID.

---

**Application: Running Total**

```sql
SELECT e1.employeeID, e1.jobCode, e1.checkDate,
       SUM(e2.hoursWorked) AS RunningTOTAL
FROM Employee AS e1, Employee AS e2
WHERE e2.checkDate < e1.checkDate
GROUP BY e1.employeeID, e1.jobCode, e1.checkDate;
```

**Use:** Calculates cumulative hours worked by employee up to a given date.

---

**Key Tips**

* **Aliases (`AS e1`, `AS e2`)**: Required to distinguish table instances.
* **Use `DISTINCT`**: Prevents duplicate result rows.
* **Helpful for**:

  * Identifying matching rows (e.g., employees with same roles)
  * Computing *running aggregates* (totals, ranks)
  * Deriving patterns within a single dataset

**Lesson Summary**
A **SELF-JOIN** allows comparison within a table by referencing it multiple times using **aliases**. It’s essential for identifying intra-table relationships, performing **running totals/counts**, and restructuring large tables into more manageable subsets.

### Section 7: SQL ALIASING

**Definition**
**Aliasing** in SQL assigns an alternative name to database objects such as **tables**, **columns**, **computed fields**, or **fully qualified object paths** for **clarity**, **readability**, or **security**.

---

**Why Use Aliasing?**

* Make **non-English** object names readable
* **Hide** sensitive internal names (e.g., schema.server.dbo.table)
* Label **computed columns** (e.g., SUM, AVG)
* Simplify **complex joins**
* Enable **reusable views** for consistent naming
* Enhance **code readability**

---

**Syntax**

**Columns:**

```sql
SELECT Prénom AS 'First Name', Nom_de_famille AS 'Last Name'
FROM Employés AS Employees;
```

**Tables:**

```sql
SELECT A.* 
FROM BankCustomer A, BankAccount B, AccountCode C 
WHERE A.CustomerID = B.CustomerID 
  AND B.AccountType = C.AccountType 
  AND B.CurrentBalance > 100.00;
```

**Computed Columns:**

```sql
SELECT Department, 
       SUM(Salary) AS 'Total Salary', 
       AVG(Salary) AS 'Average Salary' 
FROM SEmployee 
GROUP BY Department;
```

---

**Permanent Aliases**

**1. Synonyms (SQL Server, Oracle):**

```sql
CREATE SYNONYM Employees FOR Employés;
-- Now you can use:
SELECT * FROM Employees;
```

**2. Views:**

```sql
CREATE VIEW vEmployee AS
SELECT Employee,
       Prénom AS FirstName,
       Nom_de_famille AS LastName
FROM Employés;

-- Use:
SELECT * FROM vEmployee;
```

---

**Security Use-Case**
Hide internal structure in public queries:

```sql
CREATE SYNONYM myTable FOR SecurityServer.TopSecretDatabase.dbo.employee;
SELECT * FROM myTable;
```

---

**Key Points**

* Use `AS` for clarity, though it’s optional.
* Views = reusable aliasing of field names.
* Synonyms = permanent table-level aliases.
* Simplifies multi-table joins and improves maintainability.

---

**Lesson Summary**
SQL aliasing enhances **clarity**, **security**, and **efficiency**. Use aliases to translate non-standard names, clean up complex queries, or secure schema structures. Employ **synonyms** for permanent object name replacement and **views** to alias field names consistently across your application.
