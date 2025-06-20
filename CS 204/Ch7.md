### Section 1: SQL SET Operators

**Definition**
**SET Operators** in SQL treat tables as mathematical sets and allow you to perform operations like **intersection**, **union**, and **difference** on the result sets of multiple `SELECT` queries.

---

**Why Use SET Operators?**

* Compare **similar datasets** across multiple tables
* Retrieve **common**, **distinct**, or **exclusive** records
* Cleanly perform operations **without JOINs**
* Enhance **query readability** and **efficiency** for large datasets

---

**SET Operators and Syntax**

| Operator    | Action                                     | SQL Syntax Example                           |
| ----------- | ------------------------------------------ | -------------------------------------------- |
| `INTERSECT` | Returns only **common rows**               | `SELECT * FROM A INTERSECT SELECT * FROM B;` |
| `UNION`     | Returns **distinct rows** from both        | `SELECT * FROM A UNION SELECT * FROM B;`     |
| `UNION ALL` | Returns **all rows**, including duplicates | `SELECT * FROM A UNION ALL SELECT * FROM B;` |
| `EXCEPT`    | Returns rows in A but **not** in B         | `SELECT * FROM A EXCEPT SELECT * FROM B;`    |

> Oracle uses `MINUS` instead of `EXCEPT`.

---

**Examples**

**1. INTERSECT: Common People in Hiking & Traveling**

```sql
SELECT * FROM Hiking
INTERSECT
SELECT * FROM Traveling;
```

**2. UNION: All Unique Hobbyists**

```sql
SELECT SSN, FullName FROM Hiking
UNION
SELECT SSN, FullName FROM Reading
UNION
SELECT SSN, FullName FROM Traveling
ORDER BY FullName;
```

**3. UNION ALL: All Hobbyists Including Duplicates**

```sql
SELECT SSN, FullName FROM Hiking
UNION ALL
SELECT SSN, FullName FROM Reading
UNION ALL
SELECT SSN, FullName FROM Traveling
ORDER BY FullName;
```

**4. EXCEPT: Reading Hobbyists Not Hiking**

```sql
SELECT SSN, FullName FROM Reading
EXCEPT
SELECT SSN, FullName FROM Hiking
ORDER BY FullName;
```

---

**Rules for Using SET Operators**

* All SELECT statements must return the **same number of columns**
* Corresponding columns must be of **compatible data types**
* **Field names** in final output are taken from the **first SELECT statement**
* Use `ORDER BY` **only at the end** of the full statement

---

**High-Yield Clinical Relevance**

* Buzzwords: “**SET-based operations**,” “**INTERSECT**, **UNION**, **EXCEPT**”
* Exam analogy: Like comparing **patients in different clinical groups** (e.g., overlap, unique)
* Common use: Finding **shared records** or **exclusions** between datasets

---

**Key Points**

* `INTERSECT` = **common rows** from both queries
* `UNION` = **all unique rows**
* `UNION ALL` = **all rows**, including duplicates
* `EXCEPT`/`MINUS` = rows from the first query **not in** the second
* Always match **column count and data types**

---

**Lesson Summary**

SQL SET operators empower you to apply **mathematical set theory** on relational tables. `INTERSECT`, `UNION`, `UNION ALL`, and `EXCEPT/MINUS` let you extract shared, combined, or exclusive records between datasets efficiently. Know their syntax, rules, and when to use each for maximum query clarity and control.

---
---

### Section 2: DROP VIEW in SQL

**Definition**
**DROP VIEW** is a command used to remove a **virtual table** (view) from the database schema. Unlike dropping a table, **no actual data is deleted**, since a view is just a stored SQL query, not physical storage.

---

**Why Use DROP VIEW?**

* Clean up **obsolete or incorrect views**
* Remove **temporary reporting layers**
* Avoid **errors from outdated virtual schemas**
* Prepare to **redefine or rebuild** the view

---

**Syntax & Examples**

**Basic DROP VIEW Syntax:**

```sql
DROP VIEW view_name;
```

**Example:**

```sql
DROP VIEW Employee_View;
```

**Check If View Exists (Prevents Errors):**

```sql
DROP VIEW IF EXISTS Employee_View;
```

**Create Sample View for Practice:**

```sql
CREATE VIEW Employee_View AS
SELECT empID, empFullName, empJobTitle
FROM tblEmployee
WHERE empID > 0;
```

---

**What Happens When You Drop a View?**

* View is **removed** from schema.
* Queries referencing the view will **fail** after deletion.
* **Source tables/data remain unchanged**.

---

**High-Yield Clinical Relevance**

* Analogy: Like **removing a lens/filter**—you still keep the original image (data)
* Common use: **Rebuilding reports**, **optimizing database access control**

---

**Key Points**

* `DROP VIEW` is **non-destructive** to data.
* Use `IF EXISTS` to prevent errors from missing views.
* Views are great for **access control** and **data presentation**.
* Once dropped, the view’s logic must be **recreated manually** if needed.
* No rollback for view definitions—save view logic externally.

---

**Lesson Summary**

`DROP VIEW` lets you remove a virtual structure without touching the underlying data. It’s a safe, effective way to manage database views, especially during iterative design or when old views become obsolete. Use `IF EXISTS` for robustness, and remember—dropping a view never drops the real data it references.

### Section 3: What Is a Database Index?

#### Definition and Purpose

* A **database index** is a data structure that enhances the **speed and efficiency** of data retrieval from a database.
* Comparable to an index in a cookbook or a library catalog—helps locate information quickly without scanning every row in a table.
* Searches only **specific fields**, reducing the size of the result set compared to full-text searches.

#### Spreadsheet vs. Database Index

| Feature      | Spreadsheet             | Database Index                       |
| ------------ | ----------------------- | ------------------------------------ |
| Purpose      | Tabulate numerical data | Retrieve and organize large datasets |
| Tool Example | Microsoft Excel         | Microsoft Access, ERIC, Ancestry     |
| Scale        | Small data sets         | Large-scale, complex data            |

#### Database Index vs. Full-Text Search Engine

| Feature            | Database Index          | Full-Text Search Engine  |
| ------------------ | ----------------------- | ------------------------ |
| Indexed Content    | Specific fields         | Every word               |
| Result Set Size    | Smaller, focused        | Larger, more general     |
| Metadata Access    | Direct to data          | Metadata only            |
| Data Manipulation  | Import/export supported | Typically not supported  |
| Vocabulary Control | Controlled (e.g., ERIC) | Not typically controlled |
| Example            | Ancestry, ERIC          | Google                   |

#### Types of Database Indexes

1. **B+ Tree**

   * Balanced tree with multiple branches.
   * Scans entire index for queries.
   * Best for complex searches.

2. **B- Tree**

   * Self-balancing tree with fewer branches.
   * Easy to update (insert/delete).
   * Best for simple, fast queries.

3. **R- Tree**

   * Designed for **spatial/location** data.
   * Used in mobile apps for geographic searches (e.g., nearby coffee shops).

4. **Hash Table**

   * Uses key-value pairs.
   * Very fast, unordered access.
   * Best for simple lookups.

#### Categories of Database Indexes

| Category         | Clustered Index                            | Non-Clustered Index                         |
| ---------------- | ------------------------------------------ | ------------------------------------------- |
| Row Order        | Matches index order                        | Independent of index order                  |
| Physical Storage | Data rows are stored in index order        | Index stored separately                     |
| Count per Table  | Only one allowed                           | Multiple per table allowed                  |
| Example          | Back-of-the-book index (physically sorted) | Index cards pointing to data (logical link) |

#### Summary

* A **database index** boosts query speed and performance by creating structured references to data.
* Types include **B+ tree**, **B- tree**, **R-tree**, and **hash table**—each optimized for different types of data and queries.
* Indexes are categorized as **clustered** (physical order) or **non-clustered** (logical pointer).
* Indexes differ from full-text engines and spreadsheets in **functionality**, **scale**, and **specialization**.

### Section 4: What Is an SQL Index?

#### Definition and Purpose

* An **SQL index** is an **object in the database schema** that creates a **pointer** to data within a table.
* Speeds up **data retrieval** in queries, but can **slow down INSERT and UPDATE** operations.
* Can be created or dropped **without affecting the underlying data**.

*Example: Indexing `bandName` column in a music database allows faster search by band name.*

#### Creating an Index

*General Syntax:*

```sql
CREATE INDEX index_name 
ON table_name (column1, column2, ...);
```

* To **index an entire table**, just omit the column list.
* To index specific columns, list them inside parentheses.

*Example – Index on `albumTitle` and `genre`:*

```sql
CREATE INDEX albumGenre 
ON tblAlbum (albumTitle, genre);
```

#### Unique Index

* Prevents duplicate entries across specified columns.
* Uses the **UNIQUE** keyword.

*Example:*

```sql
CREATE UNIQUE INDEX genreUnique 
ON tblGenre (genre);
```

*Note: Be cautious when applying UNIQUE on columns like `artistName` or `albumTitle` due to potential duplication. To resolve this, use composite keys like `artistName + country`.*

#### Considerations When Indexing

| Factor                       | Recommendation                             |
| ---------------------------- | ------------------------------------------ |
| Table size                   | Avoid indexing small tables                |
| Column NULL values           | Avoid indexing columns with many NULLs     |
| Frequency of updates/inserts | Indexing slows down write-heavy operations |
| Column uniqueness            | Use UNIQUE only when truly appropriate     |

#### Querying with an Index

* Modern SQL engines **automatically use indexes** for query optimization.
* MySQL **no longer supports** the `WITH(INDEX(...))` hint.

*Example SELECT using indexed columns:*

```sql
SELECT * 
FROM tblAlbum 
WHERE albumTitle = 'Revolver' AND genre = 'Rock';
```

* The optimizer will use the `albumGenre` index if beneficial.

#### Summary

* SQL indexes are performance tools that provide **faster access** to data by **referencing specific columns**.
* You can index one or multiple columns and enforce **uniqueness** where needed.
* Use indexes **strategically**—especially for large tables or frequently queried fields.
* Avoid indexing **write-heavy** columns or those with **many NULLs**.
