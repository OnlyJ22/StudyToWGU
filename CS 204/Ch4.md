### Section 1: What is Data Manipulation Language?

**Definition**
Data Manipulation Language (DML) refers to a subset of SQL commands used for managing data stored within relational databases. DML allows users to perform operations such as inserting, updating, deleting, and retrieving data without altering the structure of database tables.

**Key Characteristics**

* Not a compiled programming language; rather, it is a declarative set of commands.
* Works like advanced spreadsheet formulas to interact with large datasets.
* Enables integration with other applications for dynamic data access and manipulation.
* Operates on data only — not on the schema (tables, columns, indexes, etc.).

**Primary DML Commands in SQL**

* `SELECT`: Retrieves data from one or more tables.

  * Example: `SELECT * FROM students;`
* `INSERT`: Adds new data into a table.

  * Example: `INSERT INTO students (name, age) VALUES ('John', 20);`
* `UPDATE`: Modifies existing data in a table.

  * Example: `UPDATE students SET age = 21 WHERE name = 'John';`
* `DELETE`: Removes existing data from a table.

  * Example: `DELETE FROM students WHERE name = 'John';`

**DML vs. Other SQL Subsets**

* **DML**: Manipulates data (`SELECT`, `INSERT`, `UPDATE`, `DELETE`)
* **DDL (Data Definition Language)**: Defines and alters table structure (`CREATE`, `ALTER`, `DROP`)
* **DCL (Data Control Language)**: Manages access and permissions (`GRANT`, `REVOKE`)
* **TCL (Transaction Control Language)**: Controls transaction processing (`COMMIT`, `ROLLBACK`, `SAVEPOINT`)

**Important Considerations**

* DML commands do not affect the table structures.
* Transaction control is crucial when using DML commands, especially `UPDATE` and `DELETE`, to prevent accidental data loss.
* Typically used within applications and scripts to manage live data interaction.

**Lesson Summary**
DML is essential for data-centric operations in relational databases. It forms the core of day-to-day interactions with stored information — retrieving it for analysis (`SELECT`), adding new entries (`INSERT`), modifying existing records (`UPDATE`), or removing data (`DELETE`). However, DML does not handle schema changes — that’s the domain of DDL.

### Section 2: Data Manipulation Language (DML)

**Definition**
Data Manipulation Language (DML) is a subset of SQL commands focused on modifying the **data within database tables** — not the structure. It enables users to **query, insert, update, and delete** data.

---

**Key DML Commands**

* **SELECT**
  Retrieves data from one or more tables. Commonly used with a `WHERE` clause to narrow down results.

  ```sql
  SELECT artistName, genre, country
  FROM tblArtist
  WHERE country = 'Canada';
  ```

* **INSERT**
  Adds new rows into a table. The column names and values must match in number and type.

  ```sql
  INSERT INTO tblArtist (artistName, genre, country)
  VALUES ('Boston', 'Rock', 'US');
  ```

* **UPDATE**
  Modifies existing data in a table. Always include a `WHERE` clause unless updating all rows.

  ```sql
  UPDATE tblArtist
  SET country = 'Canada'
  WHERE artistName = 'Rush';
  ```

* **DELETE**
  Removes data from a table. Also use a `WHERE` clause to avoid deleting all records.

  ```sql
  DELETE FROM tblArtist
  WHERE genre = 'Heavy Metal Disco';
  ```

---

**Important Notes**

* **DML commands only manipulate data**, not the database schema (unlike DDL).
* **Semicolons** (`;`) are used to indicate the end of a SQL statement.
* Always **use `WHERE` with UPDATE or DELETE** to prevent accidental bulk modifications.

---

**Lesson Summary**
DML refers to the commands used to **manipulate data in relational databases**, namely `SELECT`, `INSERT`, `UPDATE`, and `DELETE`. These commands allow you to work with the records in a table without altering the table's structure.

### Section 3: SQL `UPDATE` Statement

**Definition**
The `UPDATE` statement in SQL is used to modify **existing data in a table**. It can update one or multiple columns and can use conditions to control which rows are changed.

---

**Syntax**

```sql
-- Basic form
UPDATE table_name
SET column1 = value1,
    column2 = value2
WHERE condition;

-- With subquery
UPDATE table1
SET column1 = (SELECT expression
               FROM table2
               WHERE condition);
```

---

**Example 1: Basic Update**
Update the departure time for flight number 699:

```sql
UPDATE Flights
SET Depart_Time = '10:00'
WHERE Flight_Number = 699;
```

**Result:**

```
Flight_Number  |  Depart_Time
-------------- | -------------
699            | 10:00
```

---

**Example 2: Update Using a Subquery**
Update the `Arriving_Airport` name from its abbreviation:

```sql
UPDATE Flights
SET Arriving_Airport = (
    SELECT name
    FROM Airport_Names
    WHERE Abbreviation = 'ATL'
)
WHERE Flight_Number = 725;
```

**Result:**

```
Flight_Number | Arriving_Airport
------------- | ----------------
725           | Atlanta
```

---

**Important Notes**

* The `SET` clause defines the new values.
* The `WHERE` clause specifies which rows to update. **Omitting it updates all rows**.
* `UPDATE` statements can reference other tables using **subqueries**.

---

**Lesson Summary**
The SQL `UPDATE` statement modifies records within a table. It's essential to use the `WHERE` clause carefully to avoid unintended bulk updates. It supports complex logic with subqueries for dynamic value setting.

### Section 4: SQL `DELETE` Statement

**Definition**
The `DELETE` statement in SQL is used to **permanently remove records** from a table in a relational database. It does not remove the table itself—only the data inside it. **There is no undo**, so it must be used cautiously.

---

**Syntax**

```sql
-- Basic deletion
DELETE FROM table_name
WHERE condition;

-- Delete using subquery
DELETE FROM table_name
WHERE column IN (
    SELECT column FROM other_table WHERE condition
);
```

---

**Example 1: Simple Delete**
Remove flight number 145:

```sql
DELETE FROM Flights
WHERE Flight_Number = 145;
```

**Result:**

```
Flight_Number | Departing_Airport | Arriving_Airport
------------- | ----------------- | -----------------
699           | OHR               | LAX
725           | LAX               | ATL
```

---

**Example 2: Delete with Subquery**
Remove all flights arriving in Atlanta:

```sql
DELETE FROM Flights
WHERE Arriving_Airport IN (
    SELECT Abbreviation
    FROM Airport_Names
    WHERE Name = 'Atlanta'
);
```

**Result:**

```
Flight_Number | Departing_Airport | Arriving_Airport
------------- | ----------------- | -----------------
145           | OHR               | LAX
699           | OHR               | LAX
```

---

**Important Notes**

* `DELETE` removes **rows**, not tables.
* Use the `WHERE` clause to **target specific rows**. Omitting it will remove **all records**.
* The use of **subqueries** makes `DELETE` extremely powerful—and risky—when working with relational data.

---

**Lesson Summary**
SQL's `DELETE` statement is a critical DML tool for removing data. When paired with `WHERE` clauses and subqueries, it enables precise deletions—but a single mistake can result in loss of critical data. Always validate the condition before executing a `DELETE`.

### Section 5: SQL Transaction Control Language (TCL)

**Definition**
**TCL (Transaction Control Language)** manages changes made by DML (`INSERT`, `UPDATE`, `DELETE`) statements. It controls transaction processing and ensures data integrity through atomic operations.

---

**Key TCL Commands**

| Command     | Description                                                        |
| ----------- | ------------------------------------------------------------------ |
| `COMMIT`    | Permanently saves all changes since the last `COMMIT`              |
| `SAVEPOINT` | Sets a point in the transaction to which you can later roll back   |
| `ROLLBACK`  | Undoes changes to the last `COMMIT`, or to a specified `SAVEPOINT` |

---

**Example 1: COMMIT**

```sql
INSERT INTO Lessons VALUES ('LS004', 'Service Engineering');
COMMIT;
```

* **Effect**: Row `'LS004', 'Service Engineering'` is permanently added.

---

**Example 2: SAVEPOINT**

```sql
INSERT INTO Lessons VALUES('LS005', 'Reliability Engineering');
SAVEPOINT A;

INSERT INTO Lessons VALUES ('LS006', 'System of Systems');
SAVEPOINT B;
```

* **Effect**: Two rows inserted; two savepoints created.

---

**Example 3: ROLLBACK**

```sql
ROLLBACK TO A;
```

* **Effect**: Undoes the insert of `'LS006', 'System of Systems'`; keeps `'LS005', 'Reliability Engineering'`.

---

**Important Notes**

* `COMMIT` **clears** all `SAVEPOINT`s.
* `ROLLBACK` without `TO` will undo all uncommitted changes.
* TCL works only with **DML** (not DDL like `CREATE`, `DROP`).

---

**Lesson Summary**
TCL ensures transactional integrity in databases.

* Use `COMMIT` to finalize changes.
* Use `SAVEPOINT` for partial rollback control.
* Use `ROLLBACK` to undo unwanted or erroneous changes.

### Section 6: SQL String Functions: LEFT, RIGHT, SUBSTR

**Definition**
SQL provides **string manipulation functions**—`LEFT`, `RIGHT`, and `SUBSTR`—to extract or truncate parts of strings from fields. These are useful for formatting or cleaning up data stored in tables.

---

**LEFT Function**
**Syntax:**

```sql
LEFT(string, length)
```

* Extracts `length` characters starting from the **left** of the string.

**Example:** Limit artist name to 255 characters during insertion

```sql
INSERT INTO tblArtist (artistName)
VALUES (LEFT(Form.artist_name, 255));
```

**Example:** Display first 50 characters of a long field

```sql
SELECT LEFT(albumNotes, 50) FROM tblAlbum;
```

---

**RIGHT Function**
**Syntax:**

```sql
RIGHT(string, length)
```

* Extracts `length` characters from the **right** end of the string.

**Example:** Get 2-character country code from `countryName`

```sql
SELECT RIGHT(countryName, 2)
FROM tblArtist
WHERE countryName = 'ALBANIA-AL';
```

---

**SUBSTR Function**
**Syntax:**

```sql
SUBSTR(string, position, length)
```

* Extracts a substring from any starting `position` and optional `length`.

**Example:** Get substring starting at position 3 for 5 characters

```sql
SELECT SUBSTR(countryName, 3, 5);
-- Output: DENMA
```

**Example:** Get entire string from position 3 onward

```sql
SELECT SUBSTR(countryName, 3, LEN(countryName));
-- Output: DENMARK-DK
```

**Combined Use Case: Strip prefix and suffix from formatted string**

```sql
SELECT SUBSTR(countryName, 3, LEN(countryName) - 5);
-- Output: DENMARK
```

(*Assumes prefix is 2 characters, suffix is 3 characters, plus separator*)

---

**Lesson Summary**

* `LEFT()` – Extracts characters from the beginning of a string.
* `RIGHT()` – Extracts characters from the end.
* `SUBSTR()` – Extracts from a custom position.
* Use `LEN()` to handle strings of unknown or variable length.
  These functions are crucial for **string normalization, formatting**, and **data cleaning** in SQL.

### Section 7: SQL TRUNCATE Statement

**Definition**
The `TRUNCATE` statement in SQL is used to **delete all rows from a table**, functioning like a faster version of `DELETE` without a `WHERE` clause. It **resets auto-increment values** and **frees storage space**, unlike `DELETE`, which may retain allocated space.

---

**Key Features**

* **Removes all rows** from a table.
* **Resets auto-increment fields** (e.g., ID counters).
* **Cannot be rolled back** (no undo).
* **Retains table structure** (unlike `DROP`).
* **Preserves** indexes, constraints, and privileges.
* **Frees storage space** (in most DBMS).

---

**Comparison Table**

| Feature                 | DELETE                  | TRUNCATE  | DROP               |
| ----------------------- | ----------------------- | --------- | ------------------ |
| Removes rows            | Yes (with WHERE)        | Yes (all) | Yes (entire table) |
| Removes table structure | No                      | No        | Yes                |
| Resets auto-increment   | No                      | Yes       | Yes                |
| Can be rolled back      | Yes (if in transaction) | No        | No                 |
| Space reclaimed         | No                      | Yes       | Yes                |

---

**Syntax by DBMS**

**Oracle**

```sql
TRUNCATE TABLE expired_credentials;
-- Optional:
TRUNCATE TABLE expired_credentials REUSE STORAGE;
```

**SQL Server**

```sql
TRUNCATE TABLE Employees.Expired_Credentials;
```

**MySQL**

```sql
TRUNCATE TABLE expired_credentials;
```

---

**Example Before & After**

**Before TRUNCATE:**

| ID | Credential     |
| -- | -------------- |
| 1  | Expired Token  |
| 2  | Old Key        |
| 3  | Revoked Access |
| 4  | Terminated ID  |

**After TRUNCATE:**

| ID                                                            | Credential |
| ------------------------------------------------------------- | ---------- |
|                                                               |            |
| (*Table is empty; auto-increment resets to 1 on next insert*) |            |

---

**Lesson Summary**
The SQL `TRUNCATE` statement provides a **quick and efficient** way to delete all rows from a table while retaining the structure, constraints, and permissions. It is **more efficient** than `DELETE`, **non-reversible**, and **resets identity fields**, making it ideal for complete table cleanups during maintenance or testing.
