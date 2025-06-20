### Section 1: SQL Subqueries

#### What Is a Subquery?

* A **subquery** (also called a *nested query* or *INNER SELECT*) is a SQL query embedded inside another query.
* It acts as a **filter** to refine or narrow results from large datasets.
* Subqueries can appear in **SELECT**, **FROM**, **WHERE**, **UPDATE**, or **INSERT** statements.

#### Subquery in WHERE Clause

* Filters records using a subquery inside the `WHERE` condition.
* Commonly used to find records in one table that match criteria from another.

*Example: Retrieve employees enrolled in the "Health" plan.*

```sql
SELECT emp.empID, emp.empName
FROM employee emp
WHERE emp.employeeID IN
  (SELECT ben.empID
   FROM benefits ben
   WHERE ben.planCode = "Health");
```

* Uses aliases (`emp`, `ben`) for readability and clarity.

#### Subquery in FROM Clause

* The subquery is treated like a temporary table.
* Must use an alias to refer to it in the outer query.

*Example: Count number of employees per plan.*

```sql
SELECT emp.empID, emp.empName
FROM employee emp,
  (SELECT planCode, COUNT(empID) as emp_count
   FROM benefits
   GROUP BY planCode) subquery1
WHERE subquery1.empID = emp.empID;
```

* `subquery1` is the alias used to access `emp_count` and `planCode`.

#### Subquery in SELECT Clause

* Used for aggregate values per row in the outer query.
* Must return a **single value** per row (e.g., `MAX`, `MIN`, `COUNT`).

*Example: Get max order amount for each order ID.*

```sql
SELECT o1.order_id, o1.order_code,
  (SELECT MAX(order_amount)
   FROM orders o2
   WHERE o1.order_id = o2.order_id) subquery2
FROM orders o1;
```

* `subquery2` computes a scalar value (maximum order amount).

#### Subquery in UPDATE Statement (MySQL)

* Updates a table using values computed from a subquery.

*Example: Update artist votes from poll results.*

```sql
UPDATE tblArtist,
  (SELECT count(*) AS votes, user_id
   FROM tblVoteCount
   GROUP BY artist_id) AS votecount
SET tblArtist.votes = votecount.votes
WHERE tblArtist.artist_id = tblVoteCount.artist_id;
```

#### Subquery in INSERT Statement (MySQL)

* Inserts rows into a table based on results from another table.

*Example: Insert albums rated < 5 from backup.*

```sql
INSERT INTO tblAlbums (artist_id, album_title, rating)
SELECT * FROM tblBackup
WHERE rating < 5;
```

#### Summary

* Subqueries (a.k.a. nested queries or INNER SELECTs) act as **filters** embedded within a main SQL query.
* Can be used in **WHERE**, **FROM**, **SELECT**, **UPDATE**, and **INSERT** clauses.
* **Aliases** are essential when using subqueries in FROM or SELECT to enable reference from the main query.
* Must return appropriate data types/values depending on context:

  * **Single values** for SELECT clause.
  * **Result sets** for FROM and WHERE clauses.
* Syntax varies slightly between SQL systems (e.g., SQL Server vs MySQL), but core logic is consistent.

### Section 2: Sub-Queries in SQL

#### What Is a Sub-Query?

* A **sub-query** is a query defined inside another SQL statement.
* Acts as a **filter** or selection criterion to narrow down the result set.
* Can be used as a substitute for **table joins**.
* Usable within **SELECT**, **UPDATE**, **DELETE**, or **INSERT** statements.

#### Sub-Query vs. JOIN

*Example using JOIN:*

```sql
SELECT SEmployee.* 
FROM SEmployee 
INNER JOIN MProject 
ON SEmployee.EmpID = MProject.ProjectManagerID 
AND ProjectBudget > 250000.00;
```

*Equivalent using sub-query with `IN`:*

```sql
SELECT * 
FROM SEmployee 
WHERE EmpID IN 
  (SELECT ProjectManagerID 
   FROM MProject 
   WHERE ProjectBudget > 250000.00);
```

* `IN` accepts a sub-query result set like a dynamic list (e.g., `EmpID IN (1, 2, 3)`).

#### Sub-Query with UPDATE

*Example: Give a 10% salary raise to employees managing any project.*

```sql
UPDATE SEmployee 
SET Salary = Salary * 1.10 
WHERE EmpID IN 
  (SELECT ProjectManagerID 
   FROM MProject);
```

#### Nested vs Correlated Sub-Queries

* **Nested Sub-Query**: Independent of outer query; runs once.
* **Correlated Sub-Query**: Depends on outer query; runs for each row.

*Correlated Sub-Query Example:*

```sql
SELECT * 
FROM SEmployee 
WHERE EmpID IN 
  (SELECT ProjectManagerID 
   FROM MProject 
   WHERE SEmployee.Department = MProject.Department 
     AND SEmployee.EmpID = MProject.ProjectManagerID);
```

* The sub-query uses fields from the outer query (`SEmployee.Department`, `SEmployee.EmpID`).
* More resource-intensive as it runs once per row in the outer query.

#### Single-Row vs Multi-Row Sub-Queries

* **Single-Row Output**: Use operators like `=`, `<`, `>`.
  *Example:*

  ```sql
  SELECT * 
  FROM SEmployee 
  WHERE Salary > 
    (SELECT AVG(Salary) 
     FROM SEmployee);
  ```

* **Multi-Row Output**: Use `IN`, `EXISTS`, etc.
  *Example:*

  ```sql
  SELECT * 
  FROM SEmployee 
  WHERE EmpID IN 
    (SELECT ProjectManagerID 
     FROM MProject 
     WHERE Department = 'IT');
  ```

* Avoid using `=` with multi-row sub-query outputs — causes errors.

*Corrected version for MAX:*

```sql
SELECT * 
FROM SEmployee 
WHERE EmpID IN 
  (SELECT ProjectManagerID 
   FROM MProject 
   WHERE ProjectBudget = 
     (SELECT MAX(ProjectBudget) 
      FROM MProject));
```

#### Multi-Column Sub-Queries

* Used when one field (like city name) may appear in multiple countries or contexts.

*Example: Identify capital cities with mild winters (more accurate query):*

```sql
SELECT Country.Country, Country.Capital 
FROM Country 
WHERE EXISTS 
  (SELECT Country, Location 
   FROM CountryClimate 
   WHERE Season = 'Winter' 
     AND Temperature = 'Mild' 
     AND Country.Country = CountryClimate.Country 
     AND Country.Capital = CountryClimate.Location);
```

* Matches both **country** and **capital** for accurate filtering.

*Oracle-style multi-column syntax:*

```sql
SELECT * 
FROM Country 
WHERE (Country, Capital) IN 
  (SELECT Country, Location 
   FROM CountryClimate 
   WHERE Season = 'Winter' 
     AND Temperature = 'Mild');
```

#### Summary

* A **sub-query** is a query inside another SQL statement, useful for filtering and conditionally selecting data.
* Two types:

  * **Nested**: runs once independently.
  * **Correlated**: runs repeatedly with outer query context.
* Sub-queries can return:

  * **Single values** (e.g., average, max) for comparison with `=`, `>`, `<`.
  * **Multiple rows/columns** for use with `IN`, `EXISTS`.
* **Performance Tip**: Correlated sub-queries can be expensive; always evaluate if a **JOIN** offers better efficiency.
 
### Section 3: Sub-Queries – Advanced Usage and Application

#### What Is a Sub-Query?

* A **sub-query** is an SQL query embedded within another query.
* Two types:

  * **Nested Sub-Query**: Independent of the outer query; runs once.
  * **Correlated Sub-Query**: Dependent on values from the outer query; runs per outer row.

*Example – Nested:*

```sql
SELECT Employee.* 
FROM Employee 
WHERE Employee.Salary < 
  (SELECT AVG(Salary) FROM Employee);
```

*Example – Correlated:*

```sql
SELECT Employee.* 
FROM Employee 
WHERE Employee.EmpID IN 
  (SELECT Manager.EmpID 
   FROM Manager 
   WHERE Manager.EmpID = Employee.EmpID);
```

#### Sub-Query in SELECT Statement

*Example: Students scoring >40 in BIO01:*

```sql
SELECT SStudent.* 
FROM SStudent 
WHERE SStudent.studentID IN 
  (SELECT SMark.studentID 
   FROM SMark 
   WHERE SMark.SubjectID = 'BIO01' 
     AND SMark.Marks > 40 
     AND SMark.studentID = SStudent.studentID);
```

* **Correlated sub-query** scans the `SMark` table 10 times (once per `SStudent` row).
* Joins can be more efficient for such logic:

```sql
SELECT SStudent.studentID 
FROM SStudent 
JOIN SMark 
ON SStudent.studentID = SMark.studentID 
WHERE SMark.SubjectID = 'BIO01' 
  AND SMark.Marks > 40;
```

*Example – Multiple Sub-Queries in One Statement:*

```sql
SELECT SStudent.* 
FROM SStudent 
WHERE studentID IN 
  (SELECT studentID 
   FROM SMark 
   WHERE SubjectID = 'BIO01' 
     AND Marks > 60) 
AND studentID IN 
  (SELECT studentID 
   FROM SHostel);
```

#### Sub-Query in UPDATE Statement

*Example: Reduce hostel fees by 10% for BIO01 high scorers:*

```sql
UPDATE SHostel 
SET hostelFees = hostelFees * 0.9 
WHERE studentID = 
  (SELECT studentID 
   FROM SMark 
   WHERE studentID = SHostel.studentID 
     AND Marks > 60 
     AND SubjectID = 'BIO01');
```

* Note: `=` requires the sub-query to return only **one** value.
* This works because the `(studentID, SubjectID)` pair is a **primary key** in `SMark`.

#### Sub-Query in DELETE Statement

*Example: Remove hostel entries for students no longer in the system:*

```sql
DELETE FROM SHostel 
WHERE studentID NOT IN 
  (SELECT studentID 
   FROM SStudent 
   WHERE SStudent.studentID = SHostel.studentID);
```

* Prevents orphaned rows in the `SHostel` table.

#### Sub-Query in INSERT Statement

*Example: Add all non-boarder students to the hostel:*

```sql
INSERT INTO SHostel (studentID, Hostel, HostelFees)
SELECT studentID, 'North Wing Hostel', '8000.00' 
FROM SStudent 
WHERE studentID NOT IN 
  (SELECT studentID 
   FROM SHostel 
   WHERE SHostel.studentID = SStudent.studentID);
```

* Ensures new hostel entries are only created for students not already present.

#### Summary

* Sub-queries are powerful tools in SQL that can be embedded in **SELECT**, **UPDATE**, **DELETE**, and **INSERT**.
* Use **nested sub-queries** for one-time logic and **correlated sub-queries** for row-specific conditions.
* Correlated sub-queries are performance-intensive due to repeated executions; prefer **JOINs** where possible.
* Always consider the **expected output type** (single vs multiple rows) and **operator** used (`=`, `IN`, `NOT IN`, `EXISTS`).
* Design queries to ensure the **sub-query does not return multiple values** when only one is expected by the comparison.

### Section 4: EXISTS, NOT EXISTS, and WITH Operators in SQL

#### EXISTS and NOT EXISTS Operators

* Used in **sub-queries** to test for the **existence** or **non-existence** of records.
* Must be used with another SQL command (SELECT, UPDATE, DELETE).
* More efficient than `IN` for large sub-query result sets.

*Example – EXISTS: List items with suppliers.*

```sql
SELECT item.itemID 
FROM item 
WHERE EXISTS (
  SELECT itemID 
  FROM itemSupplier 
  WHERE itemSupplier.itemID = item.itemID);
```

*Example – NOT EXISTS: List items without suppliers.*

```sql
SELECT itemID 
FROM item 
WHERE NOT EXISTS (
  SELECT itemID 
  FROM itemSupplier 
  WHERE itemSupplier.itemID = item.itemID);
```

#### EXISTS in UPDATE and DELETE

*Example – UPDATE UOM for items with suppliers:*

```sql
UPDATE item 
SET uom = CONCAT(TRIM(uom), 's') 
WHERE EXISTS (
  SELECT DISTINCT itemID 
  FROM itemSupplier 
  WHERE itemSupplier.itemID = item.itemID);
```

*Example – DELETE items with suppliers:*

```sql
DELETE FROM item 
WHERE EXISTS (
  SELECT DISTINCT itemID 
  FROM itemSupplier 
  WHERE itemSupplier.itemID = item.itemID);
```

#### EXISTS vs IN Comparison

| Feature           | EXISTS                           | IN                                 |
| ----------------- | -------------------------------- | ---------------------------------- |
| Use Case          | Checks for existence             | Checks if value is in a list       |
| Column Comparison | Can compare multiple columns     | Only supports single-column checks |
| NULL Handling     | Handles NULLs correctly          | Fails with NULLs                   |
| Performance       | Faster with large sub-query sets | Better for small sub-query sets    |

*Example – IN operator alternative:*

```sql
SELECT itemID 
FROM item 
WHERE itemID IN (
  SELECT DISTINCT itemID 
  FROM itemSupplier);
```

#### WITH Clause (Common Table Expressions - CTE)

* Creates a **temporary table/view** for the duration of the query.
* Improves **readability**, **modularity**, and **reusability** of complex SQL.

*Example – Define and use a CTE for total sales:*

```sql
WITH PODetail_CTE (PONumber, Supplier, TotalSales) AS (
  SELECT podetail.ponumber, poheader.supplierID, 
         SUM(podetail.qtyordered * itemsupplier.price) AS totalSales
  FROM poheader, podetail, itemsupplier
  WHERE poheader.ponumber = podetail.ponumber 
    AND poheader.supplierID = itemsupplier.supplierID 
    AND podetail.itemID = itemsupplier.itemID
  GROUP BY podetail.ponumber, poheader.supplierID
)
SELECT SUM(TotalSales) 
FROM PODetail_CTE;
```

#### WITH Clause in UPDATE

*Example – Update UOM using CTE:*

```sql
WITH item_CTE (itemID, UOM) AS (
  SELECT itemID, UOM 
  FROM item 
  WHERE itemID = 'I000000005'
)
UPDATE item 
SET UOM = 'PCs' 
WHERE itemID IN (SELECT itemID FROM item_CTE);
```

* CTE `item_CTE` acts as a filtered view of `item`.
* Changes apply to **base table**, not the CTE itself.

#### Summary

* **EXISTS / NOT EXISTS**: Used to filter based on presence or absence of data in sub-queries. Better for large result sets and multi-column comparisons.
* **IN / ANY**: Simpler for small, single-column data checks; struggles with NULLs.
* **WITH clause**: Defines **CTEs** — temporary tables that simplify query logic. Useful in complex `SELECT`, `UPDATE`, and `DELETE` statements.
