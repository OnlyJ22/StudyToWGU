### Section 1: SQL Referential Constraints & Integrity

**Definition**
**Referential Constraints** are rules that limit the type of data that can be stored in a table column to maintain **validity and consistency**. **Referential Integrity** ensures the logical relationship between tables is preserved, typically via **PRIMARY** and **FOREIGN KEY** constraints.

---

**Why Use Referential Constraints & Integrity?**

* Prevents **dirty or illogical data** (e.g., negative weights, 1000-year-old alive persons)
* Enforces **data validity** and **consistency**
* Avoids **orphaned records** in child tables
* Guarantees **correctness of relationships** (e.g., valid suppliers for items)
* Enables **safe and predictable data modifications**

---

**Common SQL Constraints**

```sql
-- NOT NULL
CREATE TABLE Students (
    StudentID INT NOT NULL,
    BirthDate DATE NOT NULL
);

-- UNIQUE
CREATE TABLE Employees (
    SSN VARCHAR(11) UNIQUE
);

-- CHECK
CREATE TABLE TestScores (
    Score INT CHECK (Score BETWEEN 0 AND 100)
);

-- DEFAULT
CREATE TABLE Members (
    Gender VARCHAR(6) DEFAULT 'Male'
);

-- PRIMARY KEY
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY
);

-- Multiple constraints
CREATE TABLE PurchaseOrders (
    PONumber INT,
    POItem INT,
    QtyOrdered INT NOT NULL CHECK (QtyOrdered > 0),
    PRIMARY KEY (PONumber, POItem)
);
```

---

**Referential Integrity via Foreign Keys**

```sql
CREATE TABLE Supplier (
    SupplierID INT PRIMARY KEY,
    SupplierName VARCHAR(100)
);

CREATE TABLE ItemSupplier (
    ItemID INT,
    SupplierID INT,
    FOREIGN KEY (SupplierID) REFERENCES Supplier(SupplierID)
);
```

* Ensures every `SupplierID` in `ItemSupplier` **must already exist** in `Supplier`.

---

**Handling Deletion: ON DELETE Actions**

| Action                  | Behavior                                                  |
| ----------------------- | --------------------------------------------------------- |
| `ON DELETE RESTRICT`    | **Prevents deletion** if the key is referenced elsewhere  |
| `ON DELETE CASCADE`     | Deletes all related foreign key entries                   |
| `ON DELETE SET NULL`    | Sets foreign key fields to `NULL` if key is deleted       |
| `ON DELETE SET DEFAULT` | Sets foreign keys to a **default valid** value if defined |

```sql
CREATE TABLE ItemSupplier (
    ItemID INT,
    SupplierID INT,
    FOREIGN KEY (SupplierID) REFERENCES Supplier(SupplierID)
        ON DELETE CASCADE
);
```

---

**High-Yield Clinical Relevance**

* Buzzwords: “**Referential integrity violation**,” “**ON DELETE CASCADE**,” “**foreign key enforcement**”
* Often tested in scenarios with **parent-child table dependencies**
* Know how **deletion cascades** or **restrictions** affect relational data

---

**Key Points**

* Constraints validate data **at the field level**.
* Referential integrity maintains **relationships between tables**.
* Use `FOREIGN KEY` + `PRIMARY KEY` to enforce inter-table dependencies.
* Handle deletions explicitly with `ON DELETE` clauses.
* Combine constraints for robust, logical schema design.

---

**Lesson Summary**

SQL constraints guard individual fields against invalid data, while referential integrity ensures logical connections between records in related tables. Together, they uphold data integrity across the database. Mastering these is critical for designing reliable and efficient SQL-based systems and for understanding how to prevent data corruption in complex environments.

---

### Section 2: SQL Temporary Tables

**Definition**
**Temporary Tables** are special in-memory or on-disk structures used during a session to store intermediate or transient data. These tables are **automatically dropped** at the end of the session or can be **manually dropped** using SQL commands.

---

**Why Use Temporary Tables?**

* Improve performance when working with **large datasets**
* Create **intermediate results** for complex queries or reporting
* Simplify **multi-step operations**
* Replace inefficient **subqueries**, especially in **MySQL**
* Enable **on-the-fly data transformation** without affecting permanent data

---

**Syntax & Examples**

**Creating a Temporary Table:**

```sql
CREATE TEMPORARY TABLE tokens (
    customerID INT PRIMARY KEY,
    tokenCount INT
);
```

**Inserting Data:**

```sql
INSERT INTO tokens (customerID, tokenCount)
SELECT customerID, tokenCount
FROM customer
WHERE customerID = 942;
```

**Temporary Table from Query (e.g., Top Scores):**

```sql
CREATE TEMPORARY TABLE gamer_top_scores
SELECT gs.gamerID,
       g.gamerName,
       MAX(gs.score) AS topScore
FROM game_scores gs
JOIN gamer g ON g.gamerID = gs.gamerID
GROUP BY g.gamerID
ORDER BY topScore DESC
LIMIT 10;
```

**Dropping Temporary Table:**

```sql
DROP TEMPORARY TABLE gamer_top_scores;
```

---

**High-Yield Clinical Relevance**

* Analogy: **Temporary tables** in SQL = **temporary variables** or **cache** in program execution
* Buzzwords: “**CREATE TEMPORARY TABLE**,” “**session-level table**,” “**dropped on disconnect**”
* Exam context: **Session-based operations**, **performance optimization**, **dynamic report generation**

---

**Key Points**

* Temporary tables **exist only during the session** that created them.
* **Good practice**: explicitly drop temporary tables after use.
* Cannot interfere with **permanent tables** when using `TEMPORARY`.
* Useful in replacing **nested subqueries** and managing **complex intermediate data**.

---

**Lesson Summary**

Temporary tables offer a powerful way to manage transient data for intermediate processing, complex queries, or quick performance gains. Use `CREATE TEMPORARY TABLE` to define, work with them during your session, and clean up using `DROP TEMPORARY TABLE`. These tables are session-specific, safe from collisions with permanent schema, and essential in data-heavy or report-driven applications.

---
---

### Section 3: Modifying SQL Table Structures

**Definition**
Modifying SQL table structures involves changing the schema of existing tables—such as adding/removing columns, altering data types, or modifying constraints—to meet **evolving data requirements** while maintaining **data integrity**.

---

**Why Modify Table Structures?**

* Add **new attributes** (e.g., email, phone) as requirements evolve
* Increase **field capacity** due to business growth
* Enforce or relax **data validation constraints**
* Remove obsolete fields
* Handle **schema migrations** in live systems

---

**Syntax & Examples**

**Adding a New Column:**

```sql
ALTER TABLE supplier ADD ContactEmail nchar(50);
```

**Add Column With NOT NULL and Default:**

```sql
ALTER TABLE supplier ADD ContactEmail nchar(50) NOT NULL DEFAULT 'user@study.com';
```

**Changing Column Size:**

```sql
ALTER TABLE supplier MODIFY COLUMN ContactEmail nchar(60);
```

**Pre-check Before Making Column NOT NULL:**

```sql
SELECT * FROM supplier WHERE ContactEmail IS NULL;
-- If empty, then:
ALTER TABLE supplier MODIFY COLUMN ContactEmail nchar(50) NOT NULL;
```

---

**Dropping Fields and Constraints**

**Drop Primary Key Constraint First:**

```sql
ALTER TABLE supplier DROP PRIMARY KEY;
```

**Then Drop the Column:**

```sql
ALTER TABLE supplier DROP COLUMN supplierID;
```

**Drop Foreign Key Constraint:**

```sql
-- MySQL
ALTER TABLE itemSupplier DROP FOREIGN KEY fk_supplierID;

-- MS SQL Server
ALTER TABLE itemSupplier DROP CONSTRAINT fk_supplierID;
```

---

**Modifying Constraints**

**Add UNIQUE Constraint:**

```sql
ALTER TABLE Employees ADD CONSTRAINT uc_ssn UNIQUE (SSN);
```

**Add CHECK Constraint:**

```sql
ALTER TABLE TestScores ADD CONSTRAINT chk_score_range CHECK (Score BETWEEN 0 AND 100);
```

> ⚠️ *Adding constraints may fail if existing data violates the rule.* Always validate data first.

---

**High-Yield Clinical Relevance**

* Analogous to **changing structure of an evolving medical database**
* Expect questions involving **order of operations** (e.g., dropping FK → PK → column)

---

**Key Points**

* `ALTER TABLE` allows changes like **adding**, **modifying**, or **removing** columns/constraints.
* Use `DROP CONSTRAINT` before removing keys used in relationships.
* Always **validate existing data** before enforcing stricter constraints.
* Use **default values** to handle new NOT NULL fields in populated tables.
* Modifications may **cascade across related tables**—handle dependencies carefully.

---

**Lesson Summary**

Table modifications are a necessary part of managing dynamic, real-world databases. They range from simple column additions to complex schema adjustments involving foreign keys and constraints. Proper planning and sequencing of commands—especially around key relationships and existing data—are essential to avoid compromising database integrity.

---
---

### Section 4: DROP Columns & DELETE Rows in SQL

**Definition**
**DROP** is a destructive command that removes **columns**, **tables**, or **entire schemas**, permanently erasing data and structure. **DELETE** is used to remove **rows** (data records) while preserving the table structure.

---

**Why Use DROP or DELETE?**

* **DROP COLUMN**: Remove obsolete or sensitive fields (e.g., SSN)
* **DELETE ROW**: Remove outdated, incorrect, or unwanted records
* Enforce **data privacy** and **schema optimization**
* Clean up **test or temporary data**

---

**Syntax & Examples**

**Drop a Column:**

* **SQL Server / Oracle:**

```sql
ALTER TABLE customer_data DROP COLUMN SSN;
```

* **MySQL:**

```sql
ALTER TABLE customer_data DROP SSN;
```

> ⚠️ This **cannot be undone.** All data in the column will be permanently lost.

**Drop a Column With Dependencies:**

* First drop related **constraints** (e.g., primary/foreign keys).

```sql
ALTER TABLE customer_data DROP CONSTRAINT fk_ssn;
ALTER TABLE customer_data DROP COLUMN SSN;
```

---

**Delete a Row:**

```sql
DELETE FROM Customer_Table_2
WHERE firstName = 'John' AND lastName = 'Doe';
```

> ⚠️ Omitting `WHERE` clause deletes **all rows**:

```sql
DELETE FROM Customer_Table_2;  -- Deletes every row!
```

**Rollback Support:**

* In systems with **transactions**, use:

```sql
BEGIN TRANSACTION;
DELETE FROM Customer_Table_2 WHERE firstName = 'John';
ROLLBACK;  -- Reverts deletion
```

---

**High-Yield Clinical Relevance**

* Buzzwords: “**DROP COLUMN**,” “**DELETE FROM WHERE**,” “**irreversible column deletion**”
* Step 1 scenarios may relate to **data integrity violations** due to improper deletions

---

**Key Points**

* `ALTER TABLE ... DROP COLUMN` → permanently removes column and data
* `DELETE FROM ... WHERE` → removes specific rows
* Always **check for constraints or foreign keys** before DROP
* `ROLLBACK` can reverse DELETE (not DROP)
* Be precise with `WHERE` clause to prevent mass deletion

---

**Lesson Summary**

In SQL, **DROP** is used to irreversibly remove columns and structures, while **DELETE** targets specific rows of data. These operations are essential for maintaining up-to-date, secure, and clean databases, but require caution to avoid unintended data loss or integrity issues.

---
---

### Section 5: DROP CONSTRAINT in SQL

**Definition**
**DROP CONSTRAINT** is an SQL command used to **remove existing rules**—such as `NOT NULL`, `DEFAULT`, `PRIMARY KEY`, or `FOREIGN KEY`—that restrict the type or format of data in a table. Removing constraints makes the table more flexible but may reduce data integrity.

---

**Why Use DROP CONSTRAINT?**

* Adjust business rules (e.g., relax overly strict password requirements)
* Allow entry of **duplicate or NULL values** where previously restricted
* Fix errors caused by outdated **data formatting rules**
* Prepare schema for new or modified constraints

---

**Syntax & Examples**

**1. Drop `NOT NULL` Constraint (SQL Server):**

```sql
ALTER TABLE Customer_Table
ALTER COLUMN CustomerID INT NULL;
```

> ⚠️ `NOT NULL` is **part of column definition**, not named separately.

---

**2. Drop `DEFAULT` Constraint (Named):**

```sql
ALTER TABLE Customer_Table
DROP CONSTRAINT DF_OrderDate;
```

> You must know the **constraint name** (e.g., `DF_OrderDate`). Use system queries to find it if unknown.

---

**3. Drop `PRIMARY KEY`:**

```sql
ALTER TABLE Customer_Table
DROP PRIMARY KEY;
```

> If `CustomerID` is used as a foreign key in other tables, remove those dependencies first.

---

**4. Drop `FOREIGN KEY`:**

```sql
ALTER TABLE Orders
DROP FOREIGN KEY fk_customerID;  -- MySQL

-- OR for MS SQL Server:
ALTER TABLE Orders
DROP CONSTRAINT fk_customerID;
```

---

**High-Yield Clinical Relevance**

* Buzzwords: “**DROP CONSTRAINT**,” “**ALTER TABLE DROP PRIMARY KEY**,” “**relax data validation rules**”
* Likely test scenario: **Switching business rules** or **updating legacy schema**
* Understand the **impact on data integrity** when removing constraints

---

**Key Points**

* `ALTER TABLE` + `DROP CONSTRAINT` or `ALTER COLUMN` removes limits on data entry
* `NOT NULL` is dropped by **altering column nullability**
* Named constraints (e.g., `DEFAULT`, `CHECK`) require **constraint name**
* Primary/foreign keys should be dropped **in dependency order**
* Always assess how dropping constraints will affect **data validity**

---

**Lesson Summary**

Constraints act like **rules** guarding the integrity of data in a table. Sometimes, those rules must be lifted to adapt to new requirements. The `DROP CONSTRAINT` command allows this—but with care. Whether you're removing a `NOT NULL`, `DEFAULT`, or key constraint, understand the **implications for data consistency** and ensure the changes align with new business logic.

---
---

### Section 6: SQL DROP TABLE

**Definition**
**DROP TABLE** is a destructive SQL command that **removes an entire table**, along with **all its data and structure**, from the database. This action is **permanent and irreversible**, making it critical for **freeing up space**, **simplifying schemas**, or **cleaning up temporary tables**.

---

**Why Use DROP TABLE?**

* Free up **storage space** by removing unused tables
* Eliminate **temporary or redundant structures**
* Clean up after **session-specific operations** (e.g., temp shopping carts)
* Simplify or restructure **database schema**

---

**Syntax & Examples**

**Basic Syntax (All Databases):**

```sql
DROP TABLE table_name;
```

**Example:**

```sql
DROP TABLE Sales;
```

**Oracle Specific – Secure Wipe:**

```sql
DROP TABLE Temporary_Data PURGE;
```

> `PURGE` bypasses the recycle bin for secure deletion.

**SQL Server with Safety Check:**

```sql
DROP TABLE IF EXISTS browser_history;
```

---

**Real-World Application**

```sql
DROP TABLE Customer_123_Saved_Cart;
```

> Used for deleting **temporary carts** in e-commerce systems to manage session-specific data.

---

**High-Yield Clinical Relevance**

* Buzzwords: “**DROP TABLE PURGE**,” “**irreversible**,” “**schema cleanup**”
* Common use case in exam: **Resetting test environments**, or **session-based cleanup**
* Likely distractor: Confusing **DELETE (row-level)** vs. **DROP (structure-level)**

---

**Key Points**

* `DROP TABLE` permanently removes both **data and structure**.
* Use `IF EXISTS` (SQL Server) to avoid errors if the table doesn't exist.
* **Cannot drop** a table that’s **referenced by a foreign key**—remove dependencies first.
* `PURGE` in Oracle ensures **no recovery** is possible.
* No rollback—**handle with extreme caution**.

---

**Lesson Summary**

`DROP TABLE` is a powerful command for clearing out unnecessary database objects, especially temporary or session-related tables. However, because it **permanently removes all records and structure**, it must be used with **precision and forethought**. Use `PURGE` for secure deletion in Oracle, and `IF EXISTS` for safe execution in SQL Server.

---

### Section 7: Dropping Temporary Tables in SQL

**Definition**
Temporary (or **temp**) tables are short-lived tables used for **intermediate processing**, **calculations**, or **session-specific storage**. When their use is complete, they should be removed using the `DROP TABLE` command to conserve **database space** and **maintain integrity**.

---

**Why Drop Temporary Tables?**

* Prevent **resource bloat** by cleaning up after temporary usage
* Avoid **naming conflicts** in future sessions
* Prevent **query failures** from referencing non-existent tables
* Ensure **efficient use of memory and disk space**

---

**Syntax & Examples**

**Creating a Local Temp Table (SQL Server):**

```sql
CREATE TABLE #employee_temp (
    employeeID INT NOT NULL,
    empName CHAR(50) NOT NULL,
    hourWorked FLOAT NOT NULL
);
```

**Drop a Local Temporary Table:**

```sql
DROP TABLE #employee_temp;
```

**Drop a Global Temporary Table:**

```sql
DROP TABLE ##employee_temp;
```

**In MySQL:**

```sql
CREATE TEMPORARY TABLE employee_temp (...);
DROP TEMPORARY TABLE employee_temp;
```

> Note: **MySQL** does not use the `#` prefix; the `TEMPORARY` keyword in the `CREATE` statement handles scope.

---

**Best Practice: Check if Table Exists**

```sql
-- SQL Server
IF OBJECT_ID('tempdb..#employee_temp') IS NOT NULL
    DROP TABLE #employee_temp;
```

---

**High-Yield Clinical Relevance**

* Buzzwords: “**DROP TEMPORARY TABLE**,” “**session-scoped temp table**,” “**tempdb cleanup**”
* Common analogy: Like **temporary surgical instruments**—use them and dispose to avoid infection/data bloat
* USMLE-style scenario: **Session-based transaction rollback** or **dynamic data caching**

---

**Key Points**

* Temporary tables should be **dropped explicitly** even though many are auto-deleted on session end.
* `DROP TABLE` fully deletes the **table and all its data**.
* Prefix `#` = local temp table (SQL Server), `##` = global temp table.
* Use condition checks (`IF EXISTS`) before dropping to prevent runtime errors.
* Cannot reference dropped temp tables—will result in execution errors.

---

**Lesson Summary**

Temporary tables are invaluable for short-term operations, but must be dropped to keep the database clean and efficient. Use `DROP TABLE` to remove these structures once they're no longer needed. Always check their existence before deletion to prevent unnecessary errors and ensure robust SQL procedures.

---

---

### Section 8: DROP INDEX & DROP DATABASE in SQL

**Definition**
The **DROP INDEX** and **DROP DATABASE** SQL commands are used to **permanently remove database structures**. `DROP INDEX` deletes an index used for sorting or fast searching; `DROP DATABASE` deletes the **entire database** including all tables, views, and stored data.

---

**Why Use DROP INDEX or DROP DATABASE?**

* Reclaim **storage space**
* Remove **obsolete or unused structures**
* Clean up **development** or **backup environments**
* Eliminate **redundant or incorrect indexes**
* Reset corrupted or unnecessary **entire databases**

---

**Syntax & Examples**

**1. DROP INDEX (SQL Server syntax):**

```sql
DROP INDEX tblAlbum.dateModified;
```

> Removes the `dateModified` index from the `tblAlbum` table—**data remains intact.**

**MySQL Example:**

```sql
ALTER TABLE tblAlbum DROP INDEX dateModified;
```

---

**2. DROP DATABASE:**

```sql
DROP DATABASE albumsBackup;
```

> Entire database is removed—**all tables, indexes, views, and data** are deleted.

---

**Cautions**

* Both commands are **destructive** and **irreversible**.
* Use **extreme caution**—especially in production environments.
* `DROP DATABASE` cannot be rolled back and **completely removes the schema**.
* `DROP INDEX` can **degrade performance** of queries if removed inappropriately.

---

**High-Yield Clinical Relevance**

* Buzzwords: “**DROP INDEX**,” “**DROP DATABASE**,” “**storage cleanup**”
* Step 1 analogy: Like removing **obsolete clinical guidelines or protocols**
* May appear in scenarios related to **backup rotation**, **index tuning**, or **database version resets**

---

**Key Points**

* `DROP INDEX` removes the **index structure**, not the actual table data.
* `DROP DATABASE` deletes the entire **database schema**.
* Syntax varies slightly between **SQL Server**, **MySQL**, and **Oracle**.
* Always **backup** before using destructive commands.
* Can be part of **maintenance**, **optimization**, or **schema restructuring**.

---

**Lesson Summary**

SQL provides powerful commands like `DROP INDEX` and `DROP DATABASE` for deep cleanup and optimization. While `DROP INDEX` improves storage and reduces index clutter, `DROP DATABASE` erases all data and structure. These commands are best used carefully and intentionally, ideally in **maintenance scripts or controlled environments**.

---
