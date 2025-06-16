### Section 1: Relational Databases

#### What Is a Relational Database?

* A relational database organizes associated data points (e.g., names, addresses) into structured tables.
* Tables are connected through defined relationships, enabling efficient data retrieval and analysis.
* Each table corresponds to a real-world entity, and relationships allow for meaningful linkage between data sets.

#### Database Relationships

* Each table represents a specific entity, such as Customers, Products, or Orders.
* Example:

  * Customers table: includes CustomerID, Name, Address.
  * Products table: includes ProductID, Name, Price.
  * Orders table: includes OrderID, CustomerID.
  * OrderItems table: includes OrderItemID, OrderID, ProductID — serves as a junction table.
* The OrderItems table resolves the many-to-many relationship between Orders and Products.
* Relationships allow tracking of which customer placed which order and what products were included.

#### Rules for Relational Databases

* Each table must have:

  * A unique table name.
  * Multiple rows (records).
  * Unique rows.
  * A primary key to uniquely identify each record.
  * Unique attribute names for each column.
* These design rules ensure consistency, accuracy, and data integrity.

#### Primary and Foreign Keys

* Primary Key:

  * A field or combination of fields that uniquely identifies each record.
  * Example: CustomerID in Customers, OrderID in Orders.
  * Can be a composite key (e.g., combining multiple fields).
* Foreign Key:

  * A field in one table that refers to the primary key in another table.
  * Creates relational links between tables.
  * Example: CustomerID in Orders is a foreign key referring to the Customers table.

#### Cardinality of Relationships

* One-to-One (1:1): One record in Table A relates to one in Table B.

  * Example: One Voter has one Ballot.
* One-to-Many (1\:m): One record in Table A relates to many in Table B.

  * Example: One Customer can have many Orders.
* Many-to-One (m:1): Many records in Table A relate to one in Table B.

  * Example: Many Voters can vote for one Party.
* Many-to-Many (m\:m): Many records in Table A relate to many in Table B.

  * Example: Many Products appear in many Orders — resolved using a junction table like OrderItems.

#### Summary

* Relational databases use structured tables linked by defined relationships.
* Relationships are formed using primary and foreign keys.
* Cardinality defines how records in one table relate to those in another: 1:1, 1\:m, m:1, or m\:m.
* Proper design ensures accurate, efficient, and flexible data handling.

---

### Section 2: Database Applications

#### What Is a Database Application?

* A **database application** is software that enables users to access, manage, and interact with data stored in a database.
* It filters out irrelevant data and presents only the necessary records to each user.
* Key benefit: **multi-user access** with built-in **data safety and control mechanisms**.
* Historically rooted—data tracking has existed since ancient times (e.g., Sumerian clay receipts).

#### How Databases Work

* A database is composed of **tables** that store data in **rows** (records) and **columns** (fields).
* Each column is assigned a specific **data type** (e.g., text, date, number).
* Rows represent individual entries—e.g., each employee in a personnel database.
* Users **query** the database to retrieve only the data they need, allowing databases to efficiently handle **very large datasets**.

#### Advantages Over Spreadsheets

* **Spreadsheets**:

  * Good for small datasets and graphical analysis (e.g., charts).
  * Not optimized for concurrent multi-user access.
  * Becomes unwieldy with large or complex datasets.
* **Databases**:

  * Designed for large-scale data storage and retrieval.
  * Support **simultaneous access** by multiple users without performance issues.
  * Users retrieve only specific records through queries—improving speed and focus.
  * More robust in terms of **data integrity** and **security controls**.

#### Summary

* Database applications are essential tools for managing and interacting with structured data.
* They support large volumes of data and multiple users while maintaining performance and security.
* Compared to spreadsheets, databases offer better scalability, precision, and multi-user capabilities.

---

### Section 3: Database Programs

#### What Is a Database Program?

* A **database program** is a tool that helps organize, search, and retrieve data efficiently.
* It functions like a system for managing large and growing collections—just as you'd organize and label a growing book collection.
* As data increases, a more complex **database management system** becomes necessary to maintain access speed and usability.

#### Types of Database Programs

* Two main types:

  * **Flat file (single file) database programs**
  * **Relational Database Management Systems (RDBMS)**

#### Single File / Flat File Database Programs

* Suitable for **small datasets** with **single-user access**.
* Data is stored in a **plain text** or tabular format, such as a spreadsheet.
* Example: **Microsoft Excel**

  * Can store thousands to over a million records depending on version.
  * Allows limited sharing (e.g., on a single computer).
  * Cannot store complex data types (e.g., video, audio).
* Analogy: A handwritten list in a notepad—simple, limited, and personal.

#### Relational Database Management System (RDBMS)

* Designed for **large datasets** with **multiple concurrent users**.
* Supports **interrelationships** between entries, reducing redundancy and improving search efficiency.
* Can handle **complex data types** and ensure **data security**.
* Examples:

  * **Microsoft Access** – Ideal for small to medium businesses; supports up to \~20 users effectively.
  * **MySQL** – Free, widely used; good for individual developers and learners.
  * **Microsoft SQL Server / Oracle Database** – Enterprise-grade, suitable for complex and large-scale data systems.
* Analogy: An indexed, categorized library system with shared access across a network.

#### Summary

* Flat file database programs (e.g., Excel) are suitable for small, single-user scenarios.
* RDBMS solutions (e.g., Access, MySQL, SQL Server, Oracle) are built for larger, multi-user environments.
* As data complexity and access needs increase, RDBMS offers better performance, security, and scalability.

---

### Section 4: Database Schemas

#### What Is a Database Schema?

* A **database schema** is the blueprint of a relational database.
* Two main types:

  * **Physical schema** – defines the hardware, servers, and connections for database installation.
  * **Logical schema** – outlines the structure of tables, fields, and relationships (used by developers, admins, and users).
* Just like building a house requires a blueprint, building a database requires a schema to avoid inefficiencies or future redesign.

#### Designing a Schema

* Tables must be planned in advance, even before any data is entered.
* Example: A music database might include the following tables:

| Table Name | Primary Key | Other Fields                               |
| ---------- | ----------- | ------------------------------------------ |
| tblArtist  | artistID    | artistName, artistCountry                  |
| tblAlbum   | albumID     | artistID, albumTitle, releaseDate, genreID |
| tblReviews | reviewID    | albumID, reviewText                        |
| tblGenres  | genreID     | genre                                      |

* Primary keys are chosen first; fields are then grouped accordingly.
* **Normalization**: The process of minimizing data redundancy across tables.

#### Map It Out

* Use diagramming tools (e.g., Microsoft Access, Visio) to visually design table structures and their relationships.
* Relationships are shown by connecting **primary keys** (bolded fields) to **foreign keys** in related tables.
* Examples of relationships:

  * One artist → many albums (`artistID` in `tblAlbum`)
  * One album → many reviews (`albumID` in `tblReviews`)
  * One genre → many albums (`genreID` in `tblAlbum`)
* Seeing the schema visually may reveal the need for more flexibility (e.g., allowing albums to belong to multiple genres).

#### Summary

* A **schema** defines the logical and physical structure of a database.
* Designing the schema **before data entry** ensures scalability, efficiency, and proper normalization.
* Logical schemas define tables, fields, and relationships; physical schemas define infrastructure.
* Good schema design reduces redundancy and supports effective database functionality.
---

### Section 5: Structured Query Language (SQL)

#### What Is SQL?

* **SQL (Structured Query Language)** is a specialized programming language used to manage and manipulate relational databases.
* It allows users to:

  * **Insert**, **update**, and **delete** records
  * **Retrieve specific data** through queries
  * Perform **arithmetic**, **logical**, and **relational** operations on data
* SQL is a standardized language, meaning knowledge of SQL applies across different database systems (e.g., MySQL, PostgreSQL, SQL Server, Oracle).

#### Manipulating a Database

* **Data manipulation** includes:

  * Adding new data
  * Modifying existing data
  * Deleting data
  * Querying (retrieving) specific data
* A **query** is essentially a question posed to the database.

#### SQL Statements

* SQL uses **statements** to perform actions.
* Common SQL statements include:

  * `CREATE` – to create a new table or database
  * `SELECT` – to retrieve data
  * `INSERT` – to add new records
  * `UPDATE` – to modify records
  * `DELETE` – to remove records

#### SQL Syntax

* The basic syntax for querying data:

```
SELECT field(s)
FROM table(s)
WHERE condition;
```

* Example: Retrieve names of employees earning more than \$65,000

```
SELECT Name
FROM Employees
WHERE Salary > 65000;
```

* Add sorting using `ORDER BY`:

```
SELECT Name
FROM Employees
WHERE Salary > 65000
ORDER BY Name;
```

* Use `*` to select all fields:

```
SELECT *
FROM Employees
WHERE Salary > 65000;
```

#### SQL Operators

* **Arithmetic Operators**:

  * `+` (add), `-` (subtract), `*` (multiply), `/` (divide)

* **Comparison Operators**:

  * `=` (equal), `<>` (not equal), `>` (greater than), `<` (less than), `>=`, `<=`

* **Logical (Boolean) Operators**:

  * `AND` – both conditions must be true
  * `OR` – at least one condition must be true
  * `NOT` – condition must be false

* Example queries using logical operators:

```
WHERE Salary > 65000 AND Position = "Accountant";
```

```
WHERE Position = "Accountant" OR Position = "Financial Analyst";
```

```
WHERE NOT (Position = "Accountant");
```

#### Summary

* SQL is the language used to interact with relational databases.
* The `SELECT` statement is the most common way to query and retrieve data.
* SQL supports arithmetic, comparison, and Boolean logic to filter and refine results.
* Mastering basic SQL queries is essential for managing and analyzing relational data.

---

### Section 6: The Prevalence of Databases and Normalization

#### Databases in Everyday Life

* **Databases are everywhere**—used by businesses (e.g., Walmart, Amazon) and individuals (e.g., email, contacts).
* Even the **file system** on your personal computer is a basic form of a database.
* Because of their widespread use and massive data volumes, optimizing databases for **efficiency** and **minimal duplication** is essential.

#### What Is SQL?

* **SQL (Structured Query Language)** is a language developed by IBM in the 1970s for managing relational databases.
* Became commercially available via Oracle in 1979.
* Common SQL commands include:

  * `SELECT` – retrieve data
  * `INSERT` – add data
  * `UPDATE` – modify data
  * `DELETE` – remove data
  * `CREATE` – define new objects (e.g., tables)
* SQL is robust and standardized, making it usable across database systems.

#### What Is Normalization?

* **Normalization** is the process of organizing data to eliminate **redundancy** and ensure **data integrity**.
* In a **relational database**, data is stored in **tables** (rows = records, columns = fields).
* Normalization is **not automatic**—it must be incorporated during the database design phase.

#### Normalization Example

* Initial table with redundant data (e.g., multiple rows for the same person).
* Apply **1NF (First Normal Form)**:

  * Identify duplicated columns.
  * Determine a **unique key** (e.g., Name).
  * Split data into logical groupings (e.g., one table for personal attributes, another for food preferences).
* This minimizes duplication and simplifies data management.

#### Rules for First Normal Form (1NF)

1. **Identify duplicated columns** in the original table.
2. **Identify a unique key** (field or combination of fields) for each record.
3. **Break data** into separate tables based on logical groupings and link them with the key.

#### Higher Normal Forms (Overview)

* **2NF (Second Normal Form)**:

  * Build on 1NF by removing **partial dependencies** (e.g., split off unrelated columns that only depend on part of a composite key).
* **3NF (Third Normal Form)**:

  * Build on 2NF by removing **transitive dependencies** (e.g., zip codes dependent on states should be in a separate table).

#### Summary

* SQL is the standard language for database manipulation and maintenance.
* Normalization improves data structure by reducing redundancy.
* **1NF** requires uniqueness and removes repeated data by separating it into logical groupings.
* Further normalization (2NF, 3NF) continues to remove dependencies for a more efficient, scalable database design.
---

### Section 7: DBMS Table Design and Normal Forms

#### Database Management System (DBMS) Design

* A **DBMS** stores and organizes data in **tables** composed of **rows** and **columns**.
* Proper design ensures:

  * Accurate data entry and retrieval
  * Prevention of errors and anomalies
  * Clean relationships between tables
* Errors in table design lead to inconsistencies—like assigning the same room to two guests with similar names.

#### Why Normalize?

* **Normalization** removes anomalies, redundancy, and inconsistencies.
* Ensures each table serves a single, specific **entity or purpose**.
* Example: A hotel room should only belong to one guest—not serve multiple, conflicting roles.

#### The Normal Forms

* **Normal forms** are progressive design stages used to optimize tables and reduce errors.
* The main stages: **1NF**, **2NF**, and **3NF**.

---

#### First Normal Form (1NF)

* Requirements:

  * Each column must have **atomic (single) values**
  * Columns must have **unique names**
  * All values in a column must be of the **same data type**
  * No two rows should be identical

* Example Violation:

  * A single cell contains multiple phone numbers or inconsistent formats (e.g., "451-copy").

* Corrected Table:

  * Each phone number appears in a separate row.
  * All values follow a consistent numeric format.

---

#### Second Normal Form (2NF)

* Requirements:

  * Table is already in **1NF**
  * **No partial dependencies** on a composite primary key

* Example Violation:

  * A table where `CustName` depends on `CustomerID`, but not on the full composite key (e.g., `CustomerID + CustodyClass`)

* Solution:

  * Separate into:

    * **Customer Table** (CustomerID, CustName)
    * **Custody Table** (CustodyClassID, CustodyClass)
    * A linking table with foreign keys

---

#### Third Normal Form (3NF)

* Requirements:

  * Table is already in **2NF**
  * **No transitive dependencies** (non-key fields shouldn't depend on other non-key fields)

* Example Violation:

  * `Street` and `City` depend on `ZipCode`, not directly on the primary key

* Solution:

  * Split into:

    * **Address Table** (AddressID, Street, City, ZipCode)
    * **Customer Table** includes AddressID
    * **Items Table** links CustomerID with stored items
    * **Custody Class Table** holds item categories

---

#### Summary

* Poor DBMS design leads to **data anomalies and redundancy**.
* **Normalization** ensures better data organization:

  * **1NF** removes multivalued and inconsistent fields
  * **2NF** eliminates partial dependencies
  * **3NF** removes transitive dependencies
* Each stage creates clearer table relationships and ensures accurate, efficient data storage and retrieval.
---

### Section 8: First Normal Form (1NF)

#### What Is First Normal Form?

* **First Normal Form (1NF)** is the initial step in database normalization.
* The goal is to reduce **redundancy** and ensure each table contains **atomic** (granular) data.
* It sets the foundation for creating organized, scalable relational databases.

#### General Rules of 1NF

* **Each table must have a primary key** – a unique identifier for each row.
* **Each column must have a unique name** – no duplicates or ambiguous labels.
* **No repeating groups or redundant data** – fields shouldn't store multiple values or the same kind of data in multiple columns.
* **All values must be atomic** – data should be indivisible (e.g., separate first and last names).

#### Violations and Corrections

*Example 1: Missing Primary Key and Redundant Data*

| Emp\_First | Emp\_Last | Emp\_Full\_Name | Job\_Title | Department     |
| ---------- | --------- | --------------- | ---------- | -------------- |
| Jane       | Austen    | Jane Austen     | CFO        | Administration |

*Issues*:

* No primary key.
* Redundant `Emp_Full_Name` (can be derived from first and last names).

*Corrected Table (1NF)*:

| Emp\_ID | Emp\_First | Emp\_Last | Job\_Title | Department     |
| ------- | ---------- | --------- | ---------- | -------------- |
| 124002  | Jane       | Austen    | CFO        | Administration |

*Example 2: Repeated Fields*

| Emp\_ID | Emp\_First | Emp\_Last | Benefit | Benefit | Job\_Title |
| ------- | ---------- | --------- | ------- | ------- | ---------- |
| 19994   | Poe        | Edgar     | Health  | Dental  | Author     |

*Issues*:

* Duplicate column name `Benefit`.
* Repeating values in a single row.

*Corrected Table (1NF)* – separate into benefits table:

**Employee Table**

| Emp\_ID | Emp\_First | Emp\_Last | Job\_Title |
| ------- | ---------- | --------- | ---------- |
| 19994   | Poe        | Edgar     | Author     |

**Employee\_Benefits Table**

| Emp\_ID | Benefit\_Type |
| ------- | ------------- |
| 19994   | Health        |
| 19994   | Dental        |

Or using benefit plan IDs:

**Employee Table**

| Emp\_ID | Emp\_First | Emp\_Last | Health\_Plan | Dental\_Plan |
| ------- | ---------- | --------- | ------------ | ------------ |
| 19994   | Poe        | Edgar     | 1024         | 2048         |

#### Summary

* 1NF focuses on eliminating **redundant columns** and **non-atomic fields**.
* A table in 1NF:

  * Has a **primary key**
  * Uses **unique column names**
  * Stores **atomic data**
  * Avoids **repetition** and **composite fields**
* 1NF simplifies queries and supports the transition to higher normal forms (2NF, 3NF).
---

### Section 9: Second Normal Form (2NF)

#### What Is Second Normal Form?

* **Second Normal Form (2NF)** is the second level of database normalization.
* Its goal is to eliminate **partial dependencies**, further reducing redundancy and improving data integrity.
* A table must already be in **First Normal Form (1NF)** before applying 2NF.

#### General Rules of 2NF

* The table is already in **1NF**.
* **Partial dependencies are removed**—no non-key attribute should depend on part of a **composite primary key**.
* Every **non-primary field** must be fully functionally dependent on the **entire primary key**.

#### Understanding Partial Dependencies

* A **partial dependency** occurs when a non-key field is dependent on only part of a composite key.
* Example Scenario:

  * Table has: `StudentID`, `StudentName`, `ProfessorID`, `ProfessorName`, `CourseGrade`
  * `StudentName` depends only on `StudentID`
  * `ProfessorName` depends only on `ProfessorID`
  * `CourseGrade` depends on the combination of both (`StudentID`, `ProfessorID`)

*Problem*:

* If a student transfers, we risk losing associated professor data—this leads to **data anomalies**.

---

#### Step-by-Step Conversion to 2NF

**Original Table (1NF)**:

| StudentID | StudentName     | ProfessorID | ProfessorName | CourseGrade |
| --------- | --------------- | ----------- | ------------- | ----------- |
| 9090      | Jane Eyre       | 10445       | Bronte        | A           |
| 9540      | Sherlock Holmes | 13543       | Doyle         | B           |
| 9021      | Raven           | 12450       | Poe           | A           |
| 9632      | Annabel Lee     | 12450       | Poe           | B           |
| 9255      | Van Helsing     | 13085       | Stoker        | C           |

**Split into Separate Tables**:

**Student Table**:

| StudentID | StudentName     |
| --------- | --------------- |
| 9090      | Jane Eyre       |
| 9540      | Sherlock Holmes |
| 9021      | Raven           |
| 9632      | Annabel Lee     |
| 9255      | Van Helsing     |

**Professor Table**:

| ProfessorID | ProfessorName |
| ----------- | ------------- |
| 10445       | Bronte        |
| 13543       | Doyle         |
| 12450       | Poe           |
| 13085       | Stoker        |

**Grades Table**:

| StudentID | ProfessorID | Grade |
| --------- | ----------- | ----- |
| 9090      | 10445       | A     |
| 9540      | 13543       | B     |
| 9021      | 12450       | A     |
| 9632      | 12450       | B     |
| 9255      | 13085       | C     |

*Result*:

* All partial dependencies are removed.
* Each non-primary attribute depends only on the **entire primary key** or its own surrogate key.
* Database is now in **Second Normal Form (2NF)**.

---

#### Summary

* A table is in 2NF when it:

  * Is already in **1NF**
  * Has **no partial dependencies**
* Achieved by splitting up the data into logically related tables.
* **Benefits**:

  * Cleaner relationships
  * Eliminates redundancy
  * Preserves data integrity—changes in one table don’t affect unrelated records.
---

### Section 10: Third Normal Form (3NF)

#### What Is Third Normal Form?

* **Third Normal Form (3NF)** is the third level of database normalization.
* Its primary goal is to eliminate **transitive dependencies**—where one non-key column depends on another non-key column rather than the **primary key**.
* This further simplifies the structure, reducing anomalies and improving data consistency.

#### Requirements for 3NF

* The table must be in **Second Normal Form (2NF)**.
* All **non-primary fields** must be directly dependent **only on the primary key**.
* **No transitive dependencies**—fields shouldn't depend on other non-key fields.

#### Understanding Transitive Dependence

* A **transitive dependency** occurs when:

  * Column A depends on Column B
  * Column B depends on the primary key
  * Therefore, Column A indirectly depends on the primary key through Column B
* Example:

  * `albumID` → `rating` → `ratingNotes`
  * `ratingNotes` depends on `rating`, not directly on `albumID`

---

#### 3NF Example 1: Artist Table

**Before Normalization**:

| artistID | countryCode | countryName    |
| -------- | ----------- | -------------- |
| 1        | US          | United States  |
| 2        | UK          | United Kingdom |

*Problem*:

* `countryName` depends on `countryCode`, which depends on `artistID` → **transitive dependency**

**After Normalization**:

**Artist Table**:

| artistID | countryCode |
| -------- | ----------- |
| 1        | US          |
| 2        | UK          |

**Country Table**:

| countryCode | countryName    |
| ----------- | -------------- |
| US          | United States  |
| UK          | United Kingdom |

---

#### 3NF Example 2: Album Table

**Before Normalization**:

| albumID | albumTitle | artistID | rating | ratingNotes        |
| ------- | ---------- | -------- | ------ | ------------------ |
| 101     | Stormlight | 1        | 5      | Exceptional lyrics |

*Problem*:

* `ratingNotes` depends on `rating`, not directly on `albumID` → **transitive dependency**

**After Normalization**:

**Album Table**:

| albumID | albumTitle | artistID |
| ------- | ---------- | -------- |
| 101     | Stormlight | 1        |

**Ratings Table**:

| albumID | rating | ratingNotes        |
| ------- | ------ | ------------------ |
| 101     | 5      | Exceptional lyrics |

---

#### Example 3: Entity Relationship Diagram (ERD)

* An ERD shows normalized tables and their relationships:

  * Primary keys
  * Foreign key links
  * 1:1 and 1\:m relationships
* Used for visualizing the structure of 3NF databases

---

#### Practical Considerations

* While **3NF reduces redundancy**, it can introduce **complexity and overhead**:

  * More tables = more joins and queries
  * Can affect performance and usability
* **3NF is a goal**, but sometimes **2NF** offers a more balanced, practical approach—especially in smaller or less complex systems.

---

#### Summary

* **3NF removes transitive dependencies**, ensuring every column depends only on the **primary key**.
* Benefits:

  * Cleaner structure
  * Greater data integrity
* Trade-offs:

  * Increased complexity and maintenance
  * May not always be necessary depending on system scale and needs
* **Use 3NF where it adds value**, but prioritize **practical design** and **performance**.
---

### Section 11: Denormalization

#### What Is Denormalization?

* **Denormalization** is the process of restructuring a database to improve **read performance** by **reducing the number of joins** required in queries.
* Contrasts with **normalization**, which emphasizes structure, minimal redundancy, and data integrity.
* Used mainly in **data-heavy, read-intensive systems** such as **data warehouses**, **dashboards**, and **reporting tools**.

---

#### Strategies for Denormalization

* **Collapsing Tables**: Combine frequently joined tables into one.
* **Splitting Tables**: Break one large table into smaller, access-optimized subsets.
* **Adding Redundant Columns**: Duplicate frequently queried values across tables to eliminate the need for joins.
* **Adding Derived Columns**: Store pre-calculated results (e.g., totals, labels) to avoid real-time computation.

These strategies prioritize **speed and accessibility** over strict adherence to data normalization rules.

---

#### Benefits of Denormalization

* **Improved Query Performance**: Fewer joins mean faster data retrieval.
* **Faster Reports and Dashboards**: Ideal for real-time and high-volume environments.
* **Simplified Structures**: Flatter, denormalized tables are easier for non-technical users to work with.
* **Effective in Read-Heavy Systems**: Best used where data is accessed frequently but updated less often.

---

#### Use Cases of Denormalization

* **Data Warehouses and Reporting Systems**: Enables quick access to massive datasets for analytics.
* **Data Mining and Machine Learning**: Streamlines data preparation for models.
* **Read-Heavy Applications**: Reduces query complexity in lookup-heavy systems.
* **Business Dashboards**: Ensures real-time metrics and KPIs load with minimal delay.

---

#### Trade-offs of Denormalization

* **Data Duplication**: Same information may exist in multiple places.
* **Higher Risk of Inconsistencies**: More fields to update when data changes.
* **Complex Maintenance**: Harder to enforce rules and trace issues.
* **Reduced Flexibility**: Changes to data usage patterns may require major rework.

---

#### Summary

* Denormalization focuses on **speed and efficiency** rather than perfect structure.
* Useful in scenarios where **fast data retrieval** is more important than **strict data integrity**.
* Common in **business intelligence**, **analytics**, and **machine learning pipelines**.
* Must be carefully managed to balance **performance gains** against **maintenance complexity**.
Understood — always include a clear **title** in future responses. Here's the refined version of your lesson summary with the appropriate title at the top:

---

### Section 12: Introduction to Database Queries and SQL

## Database Query Overview

A **query** is a request for information from a database. Queries can retrieve, insert, update, or delete data. While advanced queries may involve multiple tables and conditions, the foundational structure is straightforward and consistent.

---

## SQL (Structured Query Language)

SQL is the industry-standard language used to interact with relational databases such as MySQL, PostgreSQL, Oracle, and SQL Server.

### SELECT – Retrieve Data

```sql
SELECT * FROM tblJokes;
```

Returns all records from the `tblJokes` table.

### WHERE – Filter Results

```sql
SELECT * FROM tblJokes WHERE clean_joke = 1;
```

Filters records to show only those marked as clean.

### ORDER BY – Sort Results

```sql
SELECT * FROM tblJokes WHERE clean_joke = 1 ORDER BY author ASC;
```

Returns clean jokes sorted by the `author` field in ascending order.

### GROUP BY – Aggregate Data

Groups rows based on a column's value, often used with aggregate functions.

Example:

```sql
SELECT author, COUNT(*) FROM tblJokes GROUP BY author;
```

---

## Modifying Data with SQL

### INSERT – Add New Data

```sql
INSERT INTO tblArtist (artistName, genre, countryCode, notes)
VALUES ('Journey', 'Rock', 'US', 'missing Raised on Radio');
```

### UPDATE – Modify Existing Data

```sql
UPDATE tblArtist SET artistName = 'Anthem [UK]'
WHERE artistID = 1;
```

### DELETE – Remove Data

```sql
DELETE FROM tblArtist
WHERE notes = 'delete me';
```

Use carefully — this removes records permanently.

---

## Table Creation (MySQL Example)

### Create `tblArtist`

```sql
CREATE TABLE tblArtist (
  artistID INT NOT NULL AUTO_INCREMENT,
  artistName VARCHAR(100),
  genre VARCHAR(100),
  countryCode VARCHAR(100),
  notes VARCHAR(100),
  PRIMARY KEY (artistID)
);
```

### Create `tblAlbum`

```sql
CREATE TABLE tblAlbum (
  albumID INT NOT NULL AUTO_INCREMENT,
  albumTitle VARCHAR(100),
  notes VARCHAR(100),
  artistID INT NOT NULL,
  PRIMARY KEY (albumID),
  FOREIGN KEY (artistID) REFERENCES tblArtist(artistID)
);
```

---

## Microsoft Access Note

* Microsoft Access provides a visual query builder but still supports raw SQL.
* Other systems (MySQL, Oracle, PostgreSQL) focus more on direct SQL.
* Prefixing objects (e.g., `tblJokes`, `rptJokes`) helps identify their purpose.

---

## Lesson Summary

* Queries are essential for working with data in a database.
* SQL is used to retrieve and manipulate data using consistent syntax.
* Key SQL operations include `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.
* Tools like Access offer visual interfaces, but SQL is universally supported across major systems.

Let me know if you'd like this turned into flashcards, a PDF, or practice exercises.

### Section 13: Denormalization

#### What Is Denormalization?

* Denormalization is the process of restructuring a database to prioritize query speed and ease of access.
* It combines data into fewer, larger tables to reduce the number of joins required in queries.
* Especially useful in read-heavy systems like data warehouses and reporting platforms where performance is more critical than strict organization.

#### Strategies for Denormalization

* Collapsing tables: Combine frequently joined tables into a single table to eliminate the need for joins.
* Splitting a table: Divide a large table into smaller, more manageable pieces based on access patterns.
* Adding redundant columns: Copy key values into multiple tables to reduce dependency on joins.
* Adding derived columns: Pre-calculate and store values (e.g., totals or status labels) to avoid real-time calculations.

#### Benefits of Denormalization

* Better performance: Fewer joins result in faster queries.
* Faster reports and dashboards: Ideal for data visualization and business intelligence.
* Easier for users: Flat, wide tables are simpler to navigate for non-technical users.
* Well-suited for read-heavy environments: Optimized for systems that require fast access to large amounts of data.
* Aligns with real-world use: While less structured, denormalized data often better serves end-user needs.

#### Use Cases of Denormalization

* Data warehouses and reporting systems: Enables fast querying and efficient report generation.
* Data mining and machine learning: Simplifies data access and reduces processing time.
* Read-heavy applications: Improves responsiveness by minimizing the complexity of data retrieval.
* Business dashboards: Enhances performance for real-time metrics and operational views.

#### Trade-offs of Denormalization

* Data duplication: Increases storage and potential for inconsistencies.
* More opportunities for error: Updating data in multiple places raises the risk of mismatches.
* Harder to maintain: Schema changes and updates require greater oversight.
* Reduced flexibility: Optimized for specific queries; changes in access needs may require schema redesign.

#### Summary

* Denormalization improves performance by restructuring data for faster access and fewer joins.
* Best used in read-heavy environments where speed is more important than perfect normalization.
* Techniques include collapsing tables, splitting tables, adding redundant or derived columns.
* Comes with trade-offs like increased complexity, maintenance effort, and risk of inconsistency.
---

### Section 14: What Is MySQL?

#### What Is MySQL?

* **MySQL** is a **relational database management system (RDBMS)** that stores data in **tables**—each table represents a collection of related data.
* Each **row** in a table is a unique record, identified by a **primary key**.
* Example: An employee table would have rows for each employee, with columns for name, title, and department.

| Employee # | Employee Name | Title       | Department    |
| ---------- | ------------- | ----------- | ------------- |
| 12345      | Mark          | Support Rep | Support       |
| 54321      | Susan         | Manager     | Accounting    |
| 13245      | Gary          | Programmer  | Development   |
| 42315      | Karen         | Sales Rep   | Outside Sales |

* **Open source**: Freely available with access to source code.
* **Widely used**: One of the most popular open source databases globally.

#### What Is SQL in MySQL?

* **SQL** stands for **Structured Query Language**—used to interact with MySQL databases.
* SQL operations are divided into three main categories:

  * **DDL (Data Definition Language)**
  * **DML (Data Manipulation Language)**
  * **DCL (Data Control Language)**

#### What Is DDL in MySQL?

* **Data Definition Language (DDL)** modifies the structure of databases and tables.
* Common DDL commands:

  * `CREATE`: Create a new database or table.
  * `ALTER`: Modify an existing table.
  * `DROP`: Delete a table.

```sql
CREATE DATABASE db_name;
ALTER TABLE table_name ADD column_name data_type;
DROP TABLE table_name;
```

#### What Is DML in MySQL?

* **Data Manipulation Language (DML)** works on the data inside the tables.
* Common DML commands:

  * `SELECT`: Retrieve data.
  * `INSERT`: Add new records.
  * `UPDATE`: Modify existing records.
  * `DELETE`: Remove records.

```sql
SELECT * FROM table_name;
INSERT INTO table_name(col1, col2, ...) VALUES (val1, val2, ...);
UPDATE table_name SET col1 = val1 WHERE some_column = some_value;
DELETE FROM table_name WHERE some_column = some_value;
```

#### What Is DCL in MySQL?

* **Data Control Language (DCL)** manages **permissions and access control**.
* Common DCL commands:

  * `GRANT`: Give user access or privileges.
  * `REVOKE`: Remove user access or privileges.

```sql
GRANT SELECT, INSERT ON database_name TO 'user'@'host';
REVOKE SELECT, INSERT ON database_name FROM 'user'@'host';
```

#### Summary

* **MySQL** organizes data into tables and uses **SQL** to manage and interact with that data.
* SQL is divided into:

  * **DDL** – structure management
  * **DML** – data management
  * **DCL** – security and permissions
* MySQL is both powerful and flexible, making it a widely used tool for relational database management.
---

### Section 15: DBMS & SQL

#### What Is a DBMS and SQL?

* A **Database Management System (DBMS)** is software that allows users to access and manipulate data within a database.
* **SQL (Structured Query Language)** is used to perform queries—requests for specific information from the database.
* The process of using SQL with a DBMS involves:

  1. Gaining access to the DBMS.
  2. Requesting specific data.
  3. Receiving the requested data.

#### Basic SQL Commands

SQL commands interact with structured data in tables. This section builds on two example tables:

**Employee Table**

| last\_name | first\_name | hire\_date | department\_number | ID  |
| ---------- | ----------- | ---------- | ------------------ | --- |
| Jones      | Michael     | 1/5/2000   | 10                 | 213 |
| Williams   | Michelle    | 11/27/2001 | 09                 | 208 |
| Smith      | David       | 9/15/2002  | 10                 | 205 |
| Miller     | Cary        | 5/29/2001  | 09                 | 209 |
| Davis      | Anne        | 3/11/2002  | 09                 | 204 |
| Wilson     | Cooper      | 9/17/2000  | 11                 | 201 |

**Department Table**

| department\_name | department\_number |
| ---------------- | ------------------ |
| Accounting       | 11                 |
| Shipping         | 10                 |
| Receiving        | 09                 |

#### SELECT Statement

* Retrieves data from a database.
* `SELECT *` returns all data from a table:

```sql
SELECT * FROM employee;
```

* Retrieve specific columns with conditions:

```sql
SELECT last_name, hire_date
FROM employee
WHERE hire_date <= '12/1/2001'
AND department_number = 09
ORDER BY hire_date;
```

**Result:**

| last\_name | hire\_date |
| ---------- | ---------- |
| Miller     | 05/29/2001 |
| Williams   | 11/27/2001 |

* Use `LIKE` to filter text patterns:

```sql
WHERE first_name LIKE 'M%';
```

Returns employees with first names starting with 'M'.

#### JOIN Statement

* Combines rows from multiple tables using related columns:

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

**Join Types:**

* `INNER JOIN`: matched rows from both tables
* `LEFT JOIN`: all rows from left table + matched rows from right
* `RIGHT JOIN`: all rows from right table + matched rows from left

#### Data Modification Commands

**CREATE** – defines a new table:

```sql
CREATE TABLE location (
  location_name varchar,
  location_id number,
  department_number number
);
```

**INSERT** – adds a new row:

```sql
INSERT INTO employee (last_name, first_name, hire_date, department_number, id)
VALUES ('Johnson', 'Kim', '1/1/2002', 11, 200);
```

**DELETE** – removes rows that meet a condition:

```sql
DELETE FROM department
WHERE department_number = 11;
```

**TRUNCATE** – deletes all rows in a table:

```sql
TRUNCATE TABLE employee;
```

**DROP** – removes the entire table:

```sql
DROP TABLE employee;
```

#### Summary

* SQL is essential for managing and retrieving data in a DBMS.
* `SELECT` retrieves data, and `JOIN` merges related data from tables.
* `CREATE`, `INSERT`, `DELETE`, `TRUNCATE`, and `DROP` modify the data and schema.
* Even basic SQL commands provide powerful control over a database.
