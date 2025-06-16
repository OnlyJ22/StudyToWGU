### Section 1: The Database Table

#### Overview

* A **database table** is the fundamental structure in any database.
* It resembles a spreadsheet with **rows** (tuples) and **columns** (attributes).
* Tables are used to organize, store, and retrieve data efficiently.

#### Key Concepts

**Schema**

* The **schema** is the name of the table.
* It should clearly reflect the table's contents.
* Example: A table named `customers` stores customer-related information.

**Attribute**

* An **attribute** corresponds to a column name.
* It defines the type of data stored in each row under that column.
* Best practices: use lowercase letters and underscores (e.g., `first_name`, `phone`, `id`).

**Example Attributes**

| last\_name | first\_name | phone | id |
| ---------- | ----------- | ----- | -- |
|            |             |       |    |

**Tuple (Row)**

* A **tuple** is a single row in a table.
* It represents a complete record.
* Tuples store data values for each attribute.

**Example Tuple**

| last\_name | first\_name | phone        | id    |
| ---------- | ----------- | ------------ | ----- |
| Doe        | John        | 555-675-7700 | 40342 |

**Field**

* A **field** is the specific data at the intersection of a tuple and attribute.
* Example: `John` is a field under the `first_name` attribute in one tuple.
* Fields can be blank unless they are part of a required column like the primary key.

**Unique Identifier (Primary Key)**

* A **primary key** ensures each tuple is unique.
* Typically a single attribute like `id` (e.g., account number).
* Primary key values **must not be null or duplicated**.

**Example**

| id    | last\_name | first\_name |
| ----- | ---------- | ----------- |
| 40342 | Doe        | John        |

* `id = 40342` is a unique identifier for John Doe.

**Database Language**

* Used to enforce structure and integrity:

  * Define primary keys
  * Set which fields are required (NOT NULL)
  * Apply constraints and rules for data management
* SQL is an example of such a language.

#### Summary

* The **schema** names the table; **attributes** are columns; **tuples** are rows; **fields** are the individual values.
* A **primary key** (unique identifier) prevents duplicate rows.
* Proper design and naming conventions enhance clarity and functionality.
* **Database language** implements and enforces these structures for efficient data management.
---

### Section 2: Data Definition Language (DDL)

#### What Is DDL?

* **Data Definition Language (DDL)** is a category of SQL commands used to define and manage **database structures**.
* Common DDL commands:

  * `CREATE`: Creates tables, views, indexes, triggers
  * `ALTER`: Modifies existing database objects
  * `DROP`: Deletes database structures

#### CREATE Statement

**Syntax:**

```sql
CREATE TABLE table_name (field_name data_type);
```

**Example:**

```sql
CREATE TABLE Artists (
  artistName VARCHAR
);
```

* `VARCHAR`, `INTEGER`, `DATE` are commonly used data types.
* The semicolon `;` is necessary to terminate SQL commands.

#### ALTER Statement

* Used to **add constraints** or modify a table’s structure.

**Example: Add a primary key:**

```sql
ALTER TABLE Artists 
ADD PRIMARY KEY (artist_pk);
```

**Naming Conventions:**

* Field name: `artistID`
* Primary key constraint: `artist_pk`
* Foreign key constraint: `artist_fk`

**Example: Add a foreign key:**

```sql
ALTER TABLE Album
ADD CONSTRAINT artist_fk FOREIGN KEY (albumArtistID)
REFERENCES Artist (artistID);
```

#### DROP Statement

* Used to **delete tables or constraints**.

**Drop a table:**

```sql
DROP TABLE Artists;
```

**Drop a constraint:**

```sql
ALTER TABLE Artists
DROP CONSTRAINT ArtistID;
```

* Foreign key constraints must be dropped before dropping the associated table.

#### Other DDL Features

**Views:**

* A **view** is a virtual table used to simplify data presentation.

**Create a view:**

```sql
CREATE VIEW Artist_Country_V AS
SELECT artistName, countryCode
FROM Artist
WHERE artistID > 0;
```

**Drop a view:**

```sql
DROP VIEW Artist_Country_V;
```

**Indexes:**

* Used to improve query speed and sort order.

```sql
CREATE INDEX countryCode ON Artist;
```

**Triggers:**

* Executes automatically when specific database events occur.

**Example (MS-SQL):**

```sql
CREATE TRIGGER noMods
ON DATABASE
FOR DROP_TABLE
AS
PRINT 'You are not allowed to do that!'
ROLLBACK;
```

#### Summary

* **DDL** commands are used to define and manage database structure.
* `CREATE`, `ALTER`, and `DROP` are essential for building and modifying tables, constraints, views, indexes, and triggers.
* **Best practice:** Use consistent naming conventions for keys and constraints to ease maintenance.
* **Views**, **indexes**, and **triggers** are powerful DDL tools for optimizing and controlling database behavior.
---

### Section 3: Tweaking the Structure – Advanced DDL Commands

#### What Is Data Definition Language (DDL)?

* **DDL (Data Definition Language)** is a subset of SQL commands used to define and modify the **structure** of database objects.
* Major DDL commands:

  * `CREATE`: Build a new table
  * `DROP`: Remove a table
  * `ALTER`: Modify structure of an existing table

#### CREATE Command

**Syntax:**

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

* Defines the structure: data types, primary keys, `NOT NULL` constraints.

#### DROP Command

**Syntax:**

```sql
DROP TABLE Table_Name;
```

**Example:**

```sql
DROP TABLE Artist;
```

* **Deletes the table and all data** within it.
* Use cautiously, especially in production databases.

#### ALTER Command

* Allows **modification of existing table structures**:

  * Add columns
  * Modify columns
  * Remove columns
  * Rename columns or tables

---

**Add Columns:**

```sql
ALTER TABLE Artist
ADD (
  subGenre VARCHAR(50),
  stateProvince VARCHAR(50)
);
```

**Modify Columns:**

```sql
ALTER TABLE Artist
MODIFY artistName VARCHAR(100) NOT NULL;
ALTER TABLE Artist
MODIFY genre VARCHAR(15) NOT NULL;
```

**Remove a Column:**

```sql
ALTER TABLE Artist
DROP COLUMN subGenre;
```

**Rename a Column:**

```sql
ALTER TABLE Artist
RENAME COLUMN countryCode TO ISOCountryCode;
```

**Rename a Table:**

```sql
ALTER TABLE Artist
RENAME TO coolArtists;
```

* Be cautious with renaming; it may **break existing queries or reports**.

#### Summary

* **CREATE**: Defines new table structure.
* **DROP**: Completely removes tables.
* **ALTER**: Tweaks table structures by adding, modifying, removing, or renaming components.
* DDL operates on **structure**, not **data**.
* These commands are foundational in designing, adjusting, and maintaining clean and scalable databases.
---

### Section 4: Using SQL's Primary Keys

#### What Is a Primary Key?

* A **Primary Key** is a column (or a set of columns) in a table that **uniquely identifies each row**.
* It must follow two rules:

  * **Uniqueness**: No duplicate values.
  * **Not Null**: Every row must have a value in this column.

**Example Use Case**:

* Driver’s license number in a DMV database.
* Social Security Number for identity management.

#### Syntax for Defining a Primary Key

**When creating a table:**

```sql
CREATE TABLE Artist (
  id INT PRIMARY KEY,
  artistName VARCHAR(100) NOT NULL,
  genre VARCHAR(50)
);
```

* The `id` field serves as the primary key.
* Ensures that each artist has a unique identifier.

#### Why Primary Keys Matter

* **Avoids duplicate records**.
* **Keeps data integrity** even when values in other fields are the same (e.g., multiple “John Smiths”).
* **Used in queries** to retrieve, update, or delete specific rows.

**Example Query**:

```sql
DELETE FROM drivers
WHERE id = 12345;
```

* This command deletes the exact row with primary key `id = 12345`.

#### Summary

* A **primary key** ensures that every row in a table is uniquely identifiable.
* Must be **unique** and **non-null**.
* Commonly used in large databases to perform efficient, targeted operations on individual records.
* Primary keys provide the backbone for **data integrity and relational referencing**.
---

### Section 5: Using SQL's Foreign Keys

#### What Is a Foreign Key?

* A **foreign key** is a field (or group of fields) in a table that **references the primary key** in another table.
* It is used to **establish a link** between the data in two tables.
* Supports **relational integrity** by ensuring that the value in the foreign key column exists in the referenced table.

#### Primary Key vs Foreign Key

| Aspect      | Primary Key                  | Foreign Key                            |
| ----------- | ---------------------------- | -------------------------------------- |
| Purpose     | Uniquely identifies each row | Links one table to another             |
| Uniqueness  | Must be unique               | Can contain duplicates                 |
| Null values | Cannot be null               | Can be null (if optional relationship) |
| Location    | In the parent (main) table   | In the child (referencing) table       |

#### Example Scenario

**Parent Table: `Artist`**

```sql
CREATE TABLE Artist (
  artistID INT PRIMARY KEY,
  artistName VARCHAR(100)
);
```

**Child Table: `Album`**

```sql
CREATE TABLE Album (
  albumID INT PRIMARY KEY,
  albumTitle VARCHAR(100),
  artistID INT,
  FOREIGN KEY (artistID) REFERENCES Artist(artistID)
);
```

* `artistID` in `Album` is the **foreign key**.
* It **links back** to `artistID` in `Artist`, ensuring each album entry refers to a valid artist.

#### Real-World Use Case

Imagine a database for tracking birthday gifts and thank-you notes:

* **Parent Table**: `Gifts` (contains unique gift IDs and details).
* **Child Tables**: `ThankYou_Email`, `ThankYou_Mail`, `ThankYou_Delivery`.
* Each child table stores the method of sending a thank-you but links to `Gifts` via a **foreign key** on `giftID`.

This allows:

* Organized breakdown of data.
* Efficient and scalable database queries.
* One source of truth for shared information (like sender details).

#### Summary

* A **foreign key** links a child table to a parent table using a reference to the parent’s primary key.
* They **don’t have to be unique** and can be reused across rows.
* Critical for breaking down large, complex datasets into manageable, interlinked tables.
* Maintains **referential integrity**, ensuring consistency across the database.
---

### Section 6: The Need for Order Schema

#### What Is SQL?

* **SQL (Structured Query Language)** is designed to **access and manipulate** information in a database.
* Key commands include:

  * `SELECT` – retrieve data
  * `INSERT` – add new data
  * `UPDATE` – modify existing data
  * `DELETE` – remove data
  * `CREATE` – generate new database objects
* SQL provides a structured environment to manage and maintain data.

#### What Is a Schema in SQL?

* A **schema** is a blueprint that **describes the structure** of data stored in a database.
* It defines:

  * **Type** – e.g., `INTEGER`, `VARCHAR`, `DATE`
  * **Size** – amount of storage allocated
  * **Organization** – how data is grouped and arranged

#### Why Schemas Matter

* They enforce **structure and consistency**, enabling:

  * Efficient data storage
  * Fast retrieval
  * Error prevention during database operations
* Analogous to a library’s organization and cataloging system.

#### Schema Design in Relational Databases

* Schemas define **multiple tables**, relationships, and constraints.
* Example structure for a **contact/address** database:

| Table   | Field     | Type    | Size | Primary Key? | Nullable? |
| ------- | --------- | ------- | ---- | ------------ | --------- |
| Contact | Name      | Text    | 50   | Yes          | No        |
| Contact | Telephone | Numeric | 12   | No           | Yes       |
| Contact | Email     | Text    | 50   | No           | Yes       |
| Address | Name      | Text    | 50   | Yes          | No        |
| Address | Street    | Text    | 100  | No           | Yes       |
| Address | City      | Text    | 100  | No           | Yes       |
| Address | State     | Text    | 50   | No           | Yes       |
| Address | Zip       | Numeric | 100  | No           | Yes       |

* Each table has a **primary key** to uniquely identify records.
* Keys also **link related tables**, enabling relational queries.

#### Summary

* SQL is essential for efficient data management.
* Schemas define how data is stored, ensuring **consistency, performance, and clarity**.
* Proper schema design is crucial for maintaining organized, reliable databases.
---

### Section 7: CHAR vs. VARCHAR Data Types in SQL

#### CHAR vs. VARCHAR

| Data Type    | Description                    | Example                                                         | Ideal Use Case                                |
| ------------ | ------------------------------ | --------------------------------------------------------------- | --------------------------------------------- |
| `CHAR(n)`    | Fixed-length character data    | `CHAR(6)` = exactly 6 characters, padded with spaces if shorter | PINs, state codes, standardized abbreviations |
| `VARCHAR(n)` | Variable-length character data | `VARCHAR(30)` = up to 30 characters, no padding                 | Names, titles, descriptions                   |

#### CHAR – Fixed-Length Data

* Allocates **exactly** `n` characters of storage.
* Shorter strings are **padded with spaces**.
* Example:

```sql
college_code CHAR(6);
```

* `'NY'` becomes `'NY    '` (4 blank spaces).
* Efficient for data of **uniform size** (e.g., ZIP codes, country codes).

#### VARCHAR – Variable-Length Data

* Allocates **up to** `n` characters.
* Only uses as much space as needed—no padding.
* Example:

```sql
college_name VARCHAR(30);
```

* `'UCLA'` stored as `'UCLA'`, not padded.
* Flexible for **irregular-length** data like names, emails, or comments.

#### Summary

* Use `CHAR` for fixed-length identifiers and codes.
* Use `VARCHAR` when the data length is variable and space matters.
* Choosing the right data type affects **storage efficiency and validation**.
---

### Section 8: SQL Number Data Types

#### Overview of Numeric Data Types

SQL offers several numeric data types that vary by storage size and range, allowing database designers to **optimize space** and **control data limits**.

| Data Type   | Bytes | Range (Unsigned)                | Use Case                     |
| ----------- | ----- | ------------------------------- | ---------------------------- |
| `TINYINT`   | 1     | 0 to 255                        | Status flags, small counters |
| `SMALLINT`  | 2     | 0 to 65,535                     | Moderate counters, IDs       |
| `MEDIUMINT` | 3     | 0 to 16,777,215                 | IDs for medium datasets      |
| `INT`       | 4     | 0 to 4,294,967,295              | Default for most integers    |
| `BIGINT`    | 8     | 0 to 18,446,744,073,709,551,615 | High-volume data systems     |

#### INT – Standard Integer

* **Bytes used:** 4 (32 bits)
* **Total values:** 2³² (unsigned)
* **Typical use:** General-purpose numeric storage

```sql
age INT;
```

* Can store numbers like `42`, `2024`, etc.
* Default integer type for most numeric data unless otherwise optimized.

#### SMALLINT – Space Saver

* **Bytes used:** 2 (16 bits)
* **Total values:** 2¹⁶ = 65,536 (unsigned)
* Best for smaller numerical ranges (e.g., year, count of items)

```sql
stock_quantity SMALLINT;
```

* Uses half the storage space of `INT`.

#### TINYINT, MEDIUMINT, BIGINT

| Type        | Use Case                                          |
| ----------- | ------------------------------------------------- |
| `TINYINT`   | Binary choices, ratings (0–255)                   |
| `MEDIUMINT` | Large catalog IDs, mid-sized datasets             |
| `BIGINT`    | Financial systems, time tracking, scientific data |

#### Summary

* Choosing the right numeric data type improves **performance** and **storage efficiency**.
* Use `SMALLINT` or `TINYINT` where ranges are predictable and small.
* Reserve `BIGINT` for large-scale applications.
* Always align data type choice with **expected range** and **storage constraints**.
---

### Section 9: SQL Decimal Data Types – NUMERIC vs. DECIMAL

#### Purpose

Use `NUMERIC` or `DECIMAL` when working with **fixed-precision decimal values**, such as prices, ratios, measurements, and financial data.

#### Syntax

```sql
DECIMAL(p, s)
NUMERIC(p, s)
```

* **p (precision):** Total number of digits allowed.
* **s (scale):** Number of digits after the decimal point.

**Example:**

```sql
DECIMAL(6, 2)  → 9999.99 (4 digits before, 2 after)
NUMERIC(10, 5) → 99999.99999
```

#### Key Differences

| Feature           | DECIMAL                                           | NUMERIC                             |
| ----------------- | ------------------------------------------------- | ----------------------------------- |
| Standard behavior | May store more digits in some SQL implementations | Enforces exact precision strictly   |
| SQL equivalence   | Not treated as equivalent by all systems          | Same limitations apply              |
| Best practice     | Pick one and stay consistent                      | Avoid cross-usage with foreign keys |

#### Example

```sql
CREATE TABLE products (
  productPrice DECIMAL(6, 2),
  productRatio NUMERIC(10, 5)
);

INSERT INTO products VALUES (1043.33, 58468.14500);
```

| productPrice | productRatio |
| ------------ | ------------ |
| 1043.33      | 58468.14500  |

#### Comparison with INTEGER Types

| Data Type | Allows Decimals | Common Usage                 |
| --------- | --------------- | ---------------------------- |
| `INT`     | ❌               | Counts, IDs                  |
| `DECIMAL` | ✅               | Currency, financial records  |
| `NUMERIC` | ✅               | Ratios, scientific precision |

#### Summary

* Use `NUMERIC(p, s)` or `DECIMAL(p, s)` for values needing precise decimal storage.
* Choose one consistently across your schema to avoid compatibility issues.
* Always specify precision and scale to enforce format and avoid unexpected behavior.


---

### Section 10: SQL Approximate Numeric Data Types – REAL, FLOAT, DOUBLE

#### Overview

SQL provides **approximate numeric data types** for representing floating-point numbers with varying degrees of **precision**. These types are ideal when some **loss of accuracy** is acceptable, typically in scientific calculations or where exact precision isn’t critical.

---

#### REAL

* **Storage:** 4 bytes
* **Precision:** \~7 digits
* **Use Case:** Moderate-precision floating-point numbers
* **Equivalent:** `FLOAT(24)` in MySQL

```sql
price REAL
```

---

#### FLOAT

* **Storage:** 4 or 8 bytes depending on precision
* **Precision (MySQL/SQL Server):**

  * `FLOAT(n)` where:

    * `n = 0–24` → 4 bytes (single precision)
    * `n = 25–53` → 8 bytes (double precision)
* **Max Precision:** \~15 digits
* **Syntax (SQL Server/MySQL 8+):**

```sql
rate FLOAT(53)
```

---

#### DOUBLE (DOUBLE PRECISION)

* **Storage:** 8 bytes
* **Precision:** Greater than FLOAT
* **Syntax (MySQL):** `DOUBLE(size, d)`

  * `size` = total digits
  * `d` = digits after decimal

```sql
SELECT CAST(Pay_Rate AS DOUBLE(6, 2));
```

* **Use Case:** High-precision numbers like hourly pay with overtime adjustments

---

#### Comparison Table

| Type   | Storage   | Approx. Precision | Syntax            | Use Case                       |
| ------ | --------- | ----------------- | ----------------- | ------------------------------ |
| REAL   | 4 bytes   | \~7 digits        | `REAL`            | Moderate precision             |
| FLOAT  | 4–8 bytes | \~15 digits       | `FLOAT(n)`        | Adjustable precision           |
| DOUBLE | 8 bytes   | Greater precision | `DOUBLE(size, d)` | High-precision (e.g., finance) |

---

#### Summary

* Use **REAL** for moderate-precision numbers where 4 bytes suffice.
* Use **FLOAT** when you want adjustable precision (up to 8 bytes).
* Use **DOUBLE** for high-precision requirements.
* These types **round values** and are considered **approximate** – not suitable for exact calculations like currency. Use `DECIMAL`/`NUMERIC` for those instead.
---

### Section 11: SQL BOOLEAN Data Type

#### What Is BOOLEAN?

* **BOOLEAN** is a **logical data type** that stores **TRUE** or **FALSE** values.
* Based on **Boolean logic**, it allows simple **binary decisions**—ideal for flags, statuses, and binary questions (yes/no, active/inactive, etc.).

---

#### Storage & Representation

* **TRUE** = 1
* **FALSE** = 0
* Some systems also support **NULL** for unknown or unassigned values.
* Internally, BOOLEAN may be stored as a **bit**, **tinyint**, or another small integer depending on the SQL dialect.

---

#### Syntax Example

```sql
CREATE TABLE donors (
  donor_id INT PRIMARY KEY,
  name VARCHAR(100),
  alumni_status BOOLEAN
);
```

* Inserting values:

```sql
INSERT INTO donors (donor_id, name, alumni_status)
VALUES (1, 'John Doe', TRUE);
```

* Querying alumni donors:

```sql
SELECT name FROM donors
WHERE alumni_status = TRUE;
```

---

#### Use Cases

| Scenario                   | Column Name   | Type    |
| -------------------------- | ------------- | ------- |
| Is a customer active?      | `is_active`   | BOOLEAN |
| Has payment been received? | `paid_status` | BOOLEAN |
| Is the user an admin?      | `is_admin`    | BOOLEAN |

---

#### Summary

* **BOOLEAN** is used for binary conditions in SQL (TRUE/FALSE).
* Ideal for yes/no flags, statuses, and logic-based filtering.
* Helps maintain **data integrity** by enforcing valid values in binary decision fields.
---

### Section 12: SQL DATE, TIME, and TIMESTAMP Data Types

#### Why Use Specific Date/Time Types?

* Enforcing **accurate formatting** (e.g., `YYYY-MM-DD`, `HH:MM:SS`)
* Enables **date-based filtering, sorting, and interval calculations**
* Reduces the likelihood of **entry and parsing errors**

---

#### DATE Data Type

* Stores **calendar dates** in the format `YYYY-MM-DD`
* Example declaration:

```sql
contract_date DATE;
```

* Example insert:

```sql
INSERT INTO contracts (contract_date)
VALUES ('2025-06-15');
```

---

#### TIME Data Type

* Stores **time of day** in the format `HH:MM:SS[.nnnnnnn]`
* Useful for scheduling, tracking time-based events

```sql
worker_time TIME;
```

* Example insert:

```sql
INSERT INTO schedule (worker_time)
VALUES ('14:30:00');
```

---

#### TIMESTAMP Data Type

* Records **both date and time**: `YYYY-MM-DD HH:MM:SS`
* Often used to track **when rows are created or updated**
* Example declaration:

```sql
entry_created TIMESTAMP DEFAULT CURRENT_TIMESTAMP;
```

* Automatically captures the **exact moment** a row is inserted

---

#### Comparison Table

| Data Type   | Format                | Use Case                      |
| ----------- | --------------------- | ----------------------------- |
| `DATE`      | `YYYY-MM-DD`          | Store only dates              |
| `TIME`      | `HH:MM:SS[.nnnnnnn]`  | Track time without date       |
| `TIMESTAMP` | `YYYY-MM-DD HH:MM:SS` | Log events with date and time |

---

#### Summary

* Use `DATE` for events, appointments, or logs needing only day-level tracking.
* Use `TIME` when hour-specific tracking matters (e.g., shifts, alarms).
* Use `TIMESTAMP` to record exact **date and time** changes—especially useful in **auditing and logging** scenarios.
---

### Section 13: BLOB – Binary Large Object

#### What Is a BLOB?

* **BLOB (Binary Large Object)** is a **SQL object data type** used to store **large binary files**: images, videos, PDFs, or executables.
* Stores **raw binary data**—not human-readable text.
* Used for storing data that doesn't fit traditional types like `VARCHAR`, `INT`, etc.

---

#### Key Characteristics

* BLOBs are **not interpreted** by the database—only stored and retrieved.
* Stored **outside main table space** to conserve memory.
* **Pointer/reference model**: the database holds a reference to the BLOB data.

---

#### BLOB in MySQL

| Type         | Max Size  |
| ------------ | --------- |
| `TINYBLOB`   | 256 bytes |
| `BLOB`       | 65 KB     |
| `MEDIUMBLOB` | 16 MB     |
| `LONGBLOB`   | 4 GB      |

```sql
CREATE TABLE media (
  media_id INT,
  media_data LONGBLOB
);
```

---

#### BLOB in Oracle

* Max Size: **4 GB**
* Example:

```sql
CREATE TABLE badge_photo (
  PhotoID INT,
  badge BLOB
);

INSERT INTO badge_photo VALUES (1, EMPTY_BLOB());
```

---

#### BLOB in SQL Server

* Equivalent: `VARBINARY(MAX)`
* Max Size: **2 GB**

```sql
CREATE TABLE Employee (
  EmployeeID INT PRIMARY KEY,
  EmpName VARCHAR(255),
  BadgePhotoHiRes VARBINARY(MAX)
);
```

---

#### Summary

| DBMS       | Type/Keyword     | Max Size |
| ---------- | ---------------- | -------- |
| MySQL      | `LONGBLOB`       | 4 GB     |
| Oracle     | `BLOB`           | 4 GB     |
| SQL Server | `VARBINARY(MAX)` | 2 GB     |

* Use BLOBs for efficient handling of **non-textual, large binary data**.
* Each DBMS has **different size limits** and syntax for implementing BLOBs.

### Section 14: Constraining Data in SQL

**High-Yield Concept:** Constraints in SQL enforce rules at the column level to ensure data integrity and accuracy. Common constraints include `NOT NULL`, `UNIQUE`, `CHECK`, `DEFAULT`, and `PRIMARY KEY`.

---

#### Definition

A **constraint** limits the type of data that can be inserted into a column. This ensures consistent and valid data entry across the database.

---

#### Placement of Constraints

Constraints are written **immediately after the data type** in a column definition within the `CREATE TABLE` statement.

**Example:**

```sql
name VARCHAR(15) NOT NULL,
```

---

#### Common Constraint Types

* **NOT NULL**
  Ensures that a column cannot have a NULL value.

  ```sql
  name VARCHAR(15) NOT NULL,
  ```

* **UNIQUE**
  Ensures all values in a column are different.

  ```sql
  id CHAR(6) UNIQUE,
  ```

* **CHECK**
  Ensures that values in a column satisfy a specific condition.
  Example enforcing feedback length:

  ```sql
  feedback VARCHAR(2500),
  CHECK (LENGTH(feedback) > 150),
  ```

* **DEFAULT**
  Sets a default value for a column when no value is specified.

  ```sql
  status VARCHAR(10) DEFAULT 'active',
  ```

* **PRIMARY KEY**
  A combination of `NOT NULL` and `UNIQUE`. Uniquely identifies each row.

  ```sql
  id CHAR(6) PRIMARY KEY,
  ```

---

#### Important Notes

* Always use a **comma** to separate column definitions unless it’s the last item (which ends with a semicolon).
* Brackets (e.g., `[NOT NULL]`) are sometimes used for readability but are not required or standard in SQL syntax.

---

#### Lesson Summary

* SQL **constraints** enforce rules to ensure valid data entry.
* Common types: `NOT NULL`, `UNIQUE`, `CHECK`, `DEFAULT`, `PRIMARY KEY`.
* Proper use of constraints ensures high data integrity and reduces bugs or inconsistencies.

Let me know if you want this adapted into a quick reference or table format.

