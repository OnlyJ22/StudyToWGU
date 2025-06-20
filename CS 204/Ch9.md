### Section 1: SQL SET Operators

#### What Is a SET Operator?

* In SQL, **SET operators** allow you to treat **table records as mathematical sets**.
* Enables combining or comparing data from **two or more tables** using set theory.
* **Supported Operators**:

  * **INTERSECT**: Common rows between tables.
  * **UNION / UNION ALL**: All rows from both tables (with or without duplicates).
  * **EXCEPT**: Rows in one table but not the other.
  * **MINUS** (Oracle equivalent of EXCEPT).

#### INTERSECT Operator

* Returns only the **common records** from two SELECT queries.
* All columns and data types must **match in number and type**.

*Example: People who enjoy both Hiking and Traveling:*

```sql
SELECT * FROM Hiking 
INTERSECT 
SELECT * FROM Traveling;
```

* Use `ORDER BY` at the end to sort results:

```sql
... INTERSECT ... 
ORDER BY FullName;
```

* **Implicit comparison**: Matches entire row values.

#### UNION and UNION ALL

* Combines records from two or more SELECT statements.

| Operator  | Description                         |
| --------- | ----------------------------------- |
| UNION     | Combines and **removes duplicates** |
| UNION ALL | Combines and **retains duplicates** |

*Example: Combine people from all three tables:*

```sql
SELECT SSN, FullName FROM Hiking
UNION
SELECT SSN, FullName FROM Reading
UNION
SELECT SSN, FullName FROM Traveling
ORDER BY FullName;
```

* To keep duplicates:

```sql
... UNION ALL ...
```

*All SELECT queries must return the same number and type of columns.*

#### EXCEPT Operator

* Returns rows in the **first SELECT** that are **not in the second**.
* Known as **MINUS** in Oracle.

*Example: People who enjoy Reading but not Hiking:*

```sql
SELECT FullName, SSN FROM Reading
EXCEPT
SELECT FullName, SSN FROM Hiking
ORDER BY FullName;
```

#### Rules and Caveats

| Rule                           | Description                                               |
| ------------------------------ | --------------------------------------------------------- |
| Same number of fields          | Each SELECT must return the **same number of columns**    |
| Compatible data types          | Corresponding fields must be of **compatible data types** |
| Use `ORDER BY` only once       | Placed at the **end of the final SELECT** query           |
| Columns need not match exactly | Names can differ; only **positions and types** matter     |
| Partial field usage is valid   | You can SELECT only specific columns for set operations   |

#### Summary

* **SQL SET operators** allow table data to be combined or compared like **mathematical sets**.
* **INTERSECT** finds common records, **UNION/UNION ALL** merge datasets, and **EXCEPT** filters unique rows.
* Useful for **multi-table queries** and replacing complex JOIN logic with **simpler set comparisons**.
* Follow syntax rules regarding **field counts**, **data types**, and **ordering** to avoid errors.

### Section 2: UNION vs. JOIN in SQL

#### What Is a UNION?

* Combines the **rows** of two or more result sets into a **single result set**.
* Useful when **merging similar data** from **different sources**.
* Removes **duplicate rows** by default (use `UNION ALL` to retain duplicates).
* Columns in both SELECT statements must:

  * Have the **same number** of columns.
  * Be of **compatible data types**.

*Example: Combine donor data from multiple university departments.*

```sql
SELECT * FROM undergrad_college
UNION
SELECT * FROM business_college
WHERE studentID NOT IN (
  SELECT studentID FROM undergrad_college);
```

*Result:*

| studentID | studentName     | studentEmail                                                          |
| --------- | --------------- | --------------------------------------------------------------------- |
| 1004      | Jane Eyre       | [eyre.jane@mycollege.edu](mailto:eyre.jane@mycollege.edu)             |
| 1005      | Sherlock Holmes | [holmes.sherlock@mycollege.edu](mailto:holmes.sherlock@mycollege.edu) |
| 1006      | Rey Skywalker   | [skywalker.rey@mycollege.edu](mailto:skywalker.rey@mycollege.edu)     |
| 1007      | Meat Loaf       | [meatloaf@mycollege.edu](mailto:meatloaf@mycollege.edu)               |
| 2095      | Harriet Tubman  | [harriet.tubman@buscollege.edu](mailto:harriet.tubman@buscollege.edu) |
| 2099      | Andres Segovia  | [andres.segovia@buscollege.edu](mailto:andres.segovia@buscollege.edu) |

#### What Is a JOIN?

* Merges **columns** from two or more tables based on a **related column** (usually a key).
* Ideal for **enriching data** from one table using **related info** from another.
* Default JOIN is an **INNER JOIN**, returning only **matching records**.

*Example: Combine alumni names with donation amounts.*

```sql
SELECT alumni_name, amount
FROM alumni 
JOIN alumni_giving
ON alumni.alum_ID = alumni_giving.alum_ID;
```

*Result:*

| alumni\_name | amount |
| ------------ | ------ |
| Bill         | 100    |
| Jane         | 1500   |
| Jack         | 500    |

#### Key Differences Between UNION and JOIN

| Feature         | UNION                                        | JOIN                                     |
| --------------- | -------------------------------------------- | ---------------------------------------- |
| Operation Type  | Combines rows (vertical merge)               | Combines columns (horizontal merge)      |
| Matching Fields | Columns must align in number/type            | Uses a key column to relate tables       |
| Duplication     | Removes duplicates (default)                 | Includes only matching rows (INNER JOIN) |
| Use Case        | Merge similar records from different sources | Enrich rows with additional info         |

#### Summary

* **UNION** merges rows across similar tables for a **broad view**.
* **JOIN** merges columns across related tables for a **detailed view**.
* Use **UNION** when stacking data vertically; use **JOIN** when aligning data horizontally.
* Always ensure **column compatibility** with UNION and **foreign key relations** with JOIN.

### Section 3: Grouping and Aggregation Using `GROUP BY`, `ROLLUP`, `CUBE`, and `GROUPING SETS`

#### Basic `GROUP BY` Clause

* The `GROUP BY` clause is used for **aggregating data** based on one or more **dimensions** (columns).
* Often paired with aggregate functions like `SUM()`, `COUNT()`, `AVG()`, etc.

*Example – Total Sales by SalesPerson:*

```sql
SELECT SalesPersonID, SUM(SalesVolume) AS 'Total Sales'
FROM Sales
WHERE Region IN ('East', 'West')
GROUP BY SalesPersonID
ORDER BY SalesPersonID;
```

* Returns one row per `SalesPersonID`.

*Example – Total Sales by SalesPerson and Region:*

```sql
SELECT SalesPersonID, SalesRegion, SUM(SalesVolume) AS 'Total Sales'
FROM Sales
WHERE SalesRegion IN ('East', 'West')
GROUP BY SalesPersonID, SalesRegion
ORDER BY SalesPersonID, SalesRegion;
```

* Returns one row per `SalesPersonID` and `SalesRegion` pair.

#### Using `ROLLUP`

* Adds **subtotal rows** based on hierarchical grouping.
* Omits subtotal for the **last column** in the `ROLLUP()` list.

*Example – Subtotals by SalesPerson:*

```sql
SELECT SalesPersonID, SalesRegion, SUM(SalesVolume) AS 'Total Sales'
FROM Sales
WHERE SalesRegion IN ('East', 'West')
GROUP BY ROLLUP(SalesPersonID, SalesRegion)
ORDER BY SalesPersonID ASC, SalesRegion DESC;
```

* Adds:

  * Subtotals per `SalesPersonID` (with `NULL` in `SalesRegion`)
  * Grand total (with `NULL` in both columns)

#### Using `CUBE`

* Similar to `ROLLUP`, but includes **all combinations** of grouped dimensions.
* Provides **cross-tab style aggregation**.

*Example – Totals by SalesPerson, Region, and all combinations:*

```sql
SELECT SalesPersonID, SalesRegion, SUM(SalesVolume) AS 'Total Sales'
FROM Sales
WHERE SalesRegion IN ('East', 'West')
GROUP BY CUBE(SalesPersonID, SalesRegion)
ORDER BY SalesPersonID ASC, SalesRegion DESC;
```

* Adds:

  * Subtotals per `SalesPersonID` (NULL `SalesRegion`)
  * Subtotals per `SalesRegion` (NULL `SalesPersonID`)
  * Grand total

#### Using `GROUPING SETS`

* Provides **full control** over how rows are grouped.
* Supports **non-hierarchical** aggregation.

*Example – Group by different combinations:*

```sql
SELECT SalesPersonID, SalesRegion, State, SUM(SalesVolume) AS 'Total Sales'
FROM Sales
WHERE SalesRegion IN ('East', 'West') 
  AND SalesPersonID IN ('S0001', 'S0002', 'S0003')
GROUP BY GROUPING SETS (
  (SalesPersonID),
  (SalesPersonID, SalesRegion),
  (State)
);
```

* Output:

  * Group by `SalesPersonID` only (NULL `SalesRegion` and `State`)
  * Group by `SalesPersonID` and `SalesRegion` (NULL `State`)
  * Group by `State` only (NULL `SalesPersonID` and `SalesRegion`)

#### Summary

| Feature          | Description                                                 |
| ---------------- | ----------------------------------------------------------- |
| `GROUP BY`       | Basic aggregation by one or more fields                     |
| `ROLLUP`         | Adds subtotals in a **hierarchical** fashion                |
| `CUBE`           | Adds subtotals for **all combinations** of grouping columns |
| `GROUPING SETS`  | Flexible definition of specific grouping combinations       |
| `NULL` in Output | Represents **aggregated total** at that grouping level      |

*Advanced grouping tools like `ROLLUP`, `CUBE`, and `GROUPING SETS` are essential for **reporting**, **dashboards**, and **data analytics**.*

### Section 4: Subqueries for Data Manipulation

#### What Is a Subquery?

* A **subquery** is a query **nested inside another SQL statement**.
* **Outer query**: the main (or parent) query.
* **Inner query**: the subquery (executed first).
* Common uses: **SELECT**, **INSERT**, **UPDATE**, **DELETE**, **CREATE TABLE**.

#### Subquery to CREATE a Table

* Creates a **new table** using the **result of a SELECT subquery**.

*Example – Create a table for female U16 players:*

```sql
CREATE TABLE FEMALE_PLAYER_U16 AS
SELECT * FROM PLAYER
WHERE PlayerGender = 'f' AND PlayerDivision = 'U16';
```

* The resulting table includes only female players in the U16 division.

#### Subquery to INSERT Records

* Inserts **selected records** from another table into the current one.

*Example – Add female U14 players into the U16 table:*

```sql
INSERT INTO FEMALE_PLAYER_U16
SELECT * FROM PLAYER
WHERE PlayerGender = 'f' AND PlayerDivision = 'U14';
```

* This moves qualifying U14 female players into the U16 table.

#### Subquery to UPDATE Records

* Used to update values in one table using **data from another table**.

*Example – Update Emily Johns’ phone number to match David Brown’s:*

```sql
UPDATE FEMALE_PLAYER_U16
SET PlayerPhoneNumber = (
  SELECT PlayerPhoneNumber 
  FROM PLAYER
  WHERE PlayerFirstName = 'David' AND PlayerLastName = 'Brown'
)
WHERE PlayerFirstName = 'Emily' AND PlayerLastName = 'Johns';
```

* The inner query fetches David Brown’s number.
* The outer query updates Emily Johns’ record with that value.

#### Summary

| Use Case         | SQL Statement Type        | Purpose                                       |
| ---------------- | ------------------------- | --------------------------------------------- |
| Data extraction  | `SELECT` within `SELECT`  | Filter/query based on another result set      |
| Table creation   | `CREATE TABLE ... AS`     | Generate a new table from a subquery          |
| Record insertion | `INSERT INTO ... SELECT`  | Insert rows selected by subquery              |
| Record update    | `UPDATE ... SET = SELECT` | Use subquery result to update specific values |

*Subqueries are powerful tools for **querying and manipulating** data efficiently, avoiding manual duplication or restructuring of data.*

### Section 5: Multi-Table Inserts in SQL

#### What Are Multi-Table Inserts?

* A **multi-table insert** allows inserting data into **multiple tables** from a **single SQL command**.
* Useful for reducing **redundant data entry**, ensuring **data consistency**, and improving **efficiency** across departments or systems.

#### Use Case Example

* A college admission application updates:

  * `Student` table (base data),
  * `MAcademic` table (academic info),
  * `MHostel` table (accommodation info).

*Goal:* Insert related records into `MAcademic` and `MHostel` once a `Student` record is created.

#### Multi-Table Inserts in Different SQL Implementations

#### **Oracle SQL: `INSERT ALL`**

*Inserts into multiple tables from one source query.*

```sql
INSERT ALL
  INTO MAcademic (StudentID, FirstName, LastName, ContactNo, DateOfBirth)
  VALUES (StudentID, FirstName, LastName, ContactNo, DateOfBirth)
  INTO MHostel (StudentID, FirstName, LastName, ContactNo)
  VALUES (StudentID, FirstName, LastName, ContactNo)
SELECT StudentID, FirstName, LastName, ContactNo, DateOfBirth
FROM Student
WHERE StudentID = 'newID';
```

*Requirements:*

* All target columns must either be supplied or accept `NULL` values.
* The source table (`Student`) must contain the required data.

*Conditional Multi-Inserts (e.g., grading categories):*

```sql
INSERT ALL
  WHEN Marks < 50 THEN INTO Fail
  WHEN Marks >= 50 AND Marks < 75 THEN INTO Credit
  WHEN Marks >= 75 THEN INTO Distinction
SELECT StudentID, SubjectID, Marks FROM Mark;
```

---

#### **MS SQL Server: `INSERT INTO ... OUTPUT INSERTED`**

*Supports multi-table insert using OUTPUT to redirect inserted data.*

```sql
INSERT INTO MAcademic (StudentID, FirstName, LastName, DateOfBirth, ContactNo)
OUTPUT INSERTED.StudentID, INSERTED.FirstName, INSERTED.LastName, INSERTED.ContactNo 
INTO MHostel
SELECT StudentID, FirstName, LastName, DateOfBirth, ContactNo FROM Student;
```

*Key Concepts:*

* `OUTPUT INSERTED` captures values from the first insert.
* Second insert (`MHostel`) uses these values.
* Effective for **two-table inserts**.

---

#### **Triggers as a Cross-Platform Alternative**

*Trigger inserts related records automatically after the base insert.*

```sql
CREATE TRIGGER triggerStudent
ON Student
AFTER INSERT
AS
BEGIN
  INSERT INTO MHostel (StudentID, FirstName, LastName, ContactNo)
  SELECT StudentID, FirstName, LastName, ContactNo FROM INSERTED;

  INSERT INTO MAcademic (StudentID, FirstName, LastName, ContactNo, DateOfBirth)
  SELECT StudentID, FirstName, LastName, ContactNo, DateOfBirth FROM INSERTED;
END;
```

*Trigger fires after insertion into `Student`, replicates data into other tables.*

---

#### Summary

| Method                 | Platform      | Supports Multiple Tables | Flexibility                   |
| ---------------------- | ------------- | ------------------------ | ----------------------------- |
| `INSERT ALL`           | Oracle        | ✅                        | Conditional insert logic      |
| `OUTPUT INSERTED`      | MS SQL Server | Limited (max 2)          | Synchronous insert redirect   |
| `AFTER INSERT Trigger` | All platforms | ✅                        | Auto-inserts upon base insert |

*Multi-table inserts ensure **efficiency**, **data consistency**, and **less manual entry**, especially across interrelated tables.*

### Section 6: PIVOT and UNPIVOT in SQL

#### What Are PIVOT and UNPIVOT?

| Command     | Purpose                             |
| ----------- | ----------------------------------- |
| **PIVOT**   | Converts **rows into columns**      |
| **UNPIVOT** | Converts **columns back into rows** |

* These commands **restructure** data presentation without changing the underlying data.
* Often used for **reporting** and **data summarization**.

---

#### PIVOT Syntax

```sql
SELECT [Column Names]
FROM [Table Name]
PIVOT (
  [Aggregate Function] FOR [Pivot Column] IN ([New Column Names])
) AS [Alias];
```

*Example: Convert `productLine` values to columns:*

```sql
SELECT productName, Planes, Cars
FROM products
PIVOT (
  SUM(buyPrice) FOR productLine IN (Planes, Cars)
) AS PivotTable;
```

*Result:*

| productName      | Planes | Cars  |
| ---------------- | ------ | ----- |
| P-51D Mustang    | 49.00  | NULL  |
| Vintage Bi-Plane | 87.63  | NULL  |
| Corsair F4U      | 23.59  | NULL  |
| Chevy Camaro Z28 | NULL   | 50.51 |

---

#### UNPIVOT Syntax

```sql
SELECT [Column Names]
FROM [Table Name]
UNPIVOT (
  [Target Column] FOR [Former Column Names] IN ([Old Column Names])
) AS [Alias];
```

*Example: Convert columns back to rows:*

```sql
SELECT productName, productLine, buyPrice
FROM (
  SELECT productName, Planes, Cars FROM products
) p
UNPIVOT (
  buyPrice FOR productLine IN (Planes, Cars)
) AS UnpivotTable;
```

*Result:*

| productName      | productLine | buyPrice |
| ---------------- | ----------- | -------- |
| P-51D Mustang    | Planes      | 49.00    |
| Vintage Bi-Plane | Planes      | 87.63    |
| Corsair F4U      | Planes      | 23.59    |
| Chevy Camaro Z28 | Cars        | 50.51    |

---

#### MySQL Workaround for PIVOT

*MySQL lacks built-in `PIVOT`/`UNPIVOT`—use `CASE` and `UNION ALL`:*

*Pivot using `CASE`:*

```sql
SELECT
  productName,
  SUM(CASE WHEN productLine = 'Planes' THEN buyPrice ELSE 0 END) AS Planes,
  SUM(CASE WHEN productLine = 'Cars' THEN buyPrice ELSE 0 END) AS Cars
FROM products
GROUP BY productName;
```

*Unpivot using `UNION ALL`:*

```sql
SELECT productName, 'Planes' AS productLine, Planes AS buyPrice FROM products
UNION ALL
SELECT productName, 'Cars' AS productLine, Cars AS buyPrice FROM products;
```

---

#### Summary

* **PIVOT** reshapes row data into columns—ideal for summarization.
* **UNPIVOT** reverts columns back into rows—used for normalization.
* MySQL lacks direct support but **workarounds** with `CASE` and `UNION ALL` exist.
* Commonly used in **reporting tools**, **dashboards**, and **data transformation workflows**.
