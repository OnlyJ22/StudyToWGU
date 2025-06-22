Look at  204 || 303 -> Ch5.md for more content

### Section 1: Structured Query Language (SQL)

#### What Is a Query?

* A **query** is a question or request made to a database for specific data.
* Example queries:

  * “List albums with a rating above 9.”
  * “How many Rolling Stones albums were released before 1980?”

#### What Is SQL?

* **Structured Query Language (SQL)** is a standardized language used to manage and query **relational databases**.
* SQL is **universal** with slight variations across platforms (e.g., MySQL, PostgreSQL, SQL Server).

#### Tables, Fields, and Rows

* A **table** holds data in **columns (fields)** and **rows (records)**.
* Example table: `tblAlbum`

| albumID | albumTitle          | releaseYear | artistID | rating |
| ------- | ------------------- | ----------- | -------- | ------ |
| 100     | Symphony in D Minor | 1888        | 5        | 10     |
| 105     | Raised on Radio     | 1986        | 10       | 8.5    |
| 110     | Poet's Heart        | 1985        | 15       | 9      |
| 120     | The Wurst Album     | 1965        | 20       | 1      |

#### Building an SQL Query

* To select specific fields:

```sql
SELECT albumTitle
FROM tblAlbum
WHERE rating >= 9;
```

* Output:

```
albumTitle
Symphony in D Minor
Poet's Heart
```

* To select **all fields**, use `*`:

```sql
SELECT *
FROM tblAlbum
WHERE rating >= 9;
```

* Output:

```
albumID | albumTitle          | releaseYear | artistID | rating
100     | Symphony in D Minor | 1888        | 5        | 10
110     | Poet's Heart        | 1985        | 15       | 9
```

#### Multi-Table Query

* When data spans **multiple tables**, use a `WHERE` clause to **match foreign keys**.
* Example: `tblAlbum` and `tblArtist`

| artistID | artistName    |
| -------- | ------------- |
| 5        | Caesar Franck |
| 10       | Journey       |
| 15       | Kate Wolf     |
| 20       | Rotten Rolf   |

* Join these tables:

```sql
SELECT artistName, albumTitle, rating
FROM tblArtist, tblAlbum
WHERE tblArtist.artistID = tblAlbum.artistID
  AND tblAlbum.rating >= 9;
```

* Output:

```
artistName     | albumTitle          | rating
Caesar Franck  | Symphony in D Minor | 10
Kate Wolf      | Poet's Heart        | 9
```

#### SQL Essentials

| Clause   | Purpose                                   |
| -------- | ----------------------------------------- |
| `SELECT` | Identifies what fields to return          |
| `FROM`   | Specifies which table(s) to use           |
| `WHERE`  | Filters results based on given conditions |
| `*`      | Wildcard to select all fields             |

#### Summary

* SQL is used to query and manipulate relational databases.
* Use `SELECT`, `FROM`, and `WHERE` to write effective queries.
* Queries can retrieve specific fields, all fields, or join data across tables.
* Effective SQL use ensures accurate, filtered, and meaningful data retrieval.

### Section 2: SQL Overview and SQL Scripts

#### What Is SQL?

* **SQL (Structured Query Language)** is a programming language designed specifically for working with **relational databases**.
* Developed by **IBM in the 1970s**, SQL has become the standard language for **defining, managing, querying**, and **controlling access** to data.

#### Purpose of SQL

* SQL allows users to:

  * Define **database structures**
  * **Insert, update, and delete** data
  * **Query** data using specific conditions
  * **Control access** and **manage transactions**

#### SQL Command Categories

| Category                             | Description                                                                                         |
| ------------------------------------ | --------------------------------------------------------------------------------------------------- |
| **DDL** (Data Definition Language)   | Commands for **creating** and **modifying** structure (e.g., `CREATE`, `ALTER`, `DROP`)             |
| **DML** (Data Manipulation Language) | Commands for **inserting**, **updating**, or **deleting** data (e.g., `INSERT`, `UPDATE`, `DELETE`) |
| **DCL** (Data Control Language)      | Commands to **grant or revoke** user permissions (e.g., `GRANT`, `REVOKE`)                          |
| **Data Administration**              | Commands for **auditing** and **analyzing** database operations                                     |
| **Transaction Control**              | Commands for managing **transactions** (e.g., `COMMIT`, `ROLLBACK`, `SAVEPOINT`)                    |
| **Query**                            | Commands to **retrieve** data (e.g., `SELECT`)                                                      |

#### What Is an SQL Script?

* An **SQL script** is a **text file** containing a sequential list of SQL commands designed to perform a specific task.
* Used for:

  * **Automating repetitive** database tasks.
  * **Batch processing** of large data sets.
* Example use case:

  * Updating work hours for hundreds of employees with one script.

#### Creating SQL Scripts

* SQL scripts are **plain text** files.
* Can be created using any **text editor** (e.g., Notepad, VS Code).
* Saved with `.sql` extension for easy recognition.

#### Running SQL Scripts

* **Executed** using database management tools (e.g., MySQL Workbench, SQL Server Management Studio).
* Common features of script tools:

  * **Loading** a script into an editor
  * **Editing** existing scripts
  * **Saving** changes to disk
  * **Executing** the script against the database

#### Summary

* **SQL** is a domain-specific language for managing relational databases.
* It includes structured categories like **DDL, DML, DCL, Data Admin, Transaction Control,** and **Queries**.
* **SQL scripts** automate and streamline repetitive database tasks, increasing accuracy and efficiency.
* Scripts are written as text files and executed using database management utilities.

### Section 3: SQL Command Categories and Queries

#### What Is SQL?

* **SQL (Structured Query Language)** is a programming language developed by **IBM in the early 1970s**.
* Designed to **query and manipulate** data in a **relational database** — a structured grouping of related data.

#### SQL Command Categories

| Category                             | Description                                                                                       |
| ------------------------------------ | ------------------------------------------------------------------------------------------------- |
| **DDL (Data Definition Language)**   | Defines and modifies **database structure**. Examples: `CREATE`, `ALTER`, `DROP`.                 |
| **DML (Data Manipulation Language)** | Changes **data** in the database. Examples: `INSERT`, `UPDATE`, `DELETE`.                         |
| **DCL (Data Control Language)**      | Controls **user access**. Examples: `GRANT`, `REVOKE`, `ALTER PASSWORD`.                          |
| **Data Administration**              | Used for **auditing and analyzing** database operations. Examples: `START AUDIT`, `STOP AUDIT`.   |
| **Transaction Control**              | Manages **transactions** and ensures data integrity. Examples: `COMMIT`, `ROLLBACK`, `SAVEPOINT`. |
| **DQL (Data Query Language)**        | Retrieves data from the database. Only command: `SELECT`.                                         |

#### What Is a SQL Query?

* A **query** is a **DQL command**, most commonly used in SQL to retrieve data.
* The `SELECT` command can be expanded with various **clauses**:

| Clause     | Function                                                        |
| ---------- | --------------------------------------------------------------- |
| `FROM`     | Specifies which **table(s)** to query                           |
| `WHERE`    | Filters results based on a **condition**                        |
| `DISTINCT` | Returns only **unique** values, eliminating duplicates          |
| `ORDER BY` | Sorts results by one or more fields (**ASC** or **DESC** order) |

* Even with multiple clauses, a SQL query with `SELECT` is still a **single statement**.

#### What Is a SQL Script?

* A **SQL Script** is a **set of multiple SQL statements** grouped for a specific task.
* Useful for:

  * **Batch operations** (e.g., inserting multiple rows).
  * **Automating** repetitive database tasks.
* Example: Inserting 20 records followed by a verification query:

```sql
INSERT INTO Customers VALUES (...);
-- (Repeat for each record)
SELECT * FROM Customers;
```

#### Summary

* **SQL** is a powerful language used to define, manipulate, control, and query relational databases.
* **Command categories** include DDL, DML, DCL, Data Admin, Transaction Control, and DQL.
* The `SELECT` statement in **DQL** is the most used command and can include multiple **clauses** for flexible querying.
* **SQL scripts** combine multiple statements for complex or repetitive tasks.
