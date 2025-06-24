### Section 1: SQL vs. T-SQL

#### What Is SQL?

* **SQL (Structured Query Language)**: A language developed by **IBM in the 1970s** and released commercially by **Oracle in 1979**.
* Designed to **access, manipulate, and manage** relational databases.
* Core SQL commands include:

| Command  | Description                                 |
| -------- | ------------------------------------------- |
| `SELECT` | Retrieves data from a database              |
| `INSERT` | Adds new records                            |
| `UPDATE` | Modifies existing records                   |
| `DELETE` | Removes records                             |
| `CREATE` | Defines new database objects (e.g., tables) |

* SQL forms the **standard framework** for interacting with relational databases.

#### What Is T-SQL?

* **T-SQL (Transact-SQL)**: A **proprietary extension** of SQL developed by **Microsoft and Sybase**.
* Designed to work exclusively with **relational databases** (i.e., table-based data storage).
* Adds **procedural programming capabilities** and **data processing enhancements** to SQL.

#### Key Differences Between SQL and T-SQL

| Feature                 | SQL                             | T-SQL (Transact-SQL)                                         |
| ----------------------- | ------------------------------- | ------------------------------------------------------------ |
| **Standardization**     | ANSI-standard                   | Microsoft-specific extension                                 |
| **Database Support**    | Works with multiple RDBMSs      | Designed for **Microsoft SQL Server**                        |
| **Procedural Features** | Lacks built-in procedural logic | Supports **IF, WHILE, BEGIN...END, TRY...CATCH**, etc.       |
| **Local Variables**     | Not standard                    | Supports `DECLARE`, `SET`, and variable scoping              |
| **String Processing**   | Basic                           | Advanced string functions like `LEN`, `CHARINDEX`, `REPLACE` |
| **Date Processing**     | Basic date handling             | Rich set of date functions: `DATEDIFF`, `GETDATE()`, etc.    |
| **Math Functions**      | Limited                         | Supports advanced math with `ROUND`, `POWER`, `ABS`, etc.    |
| **`DELETE` / `UPDATE`** | Basic command set               | Extended with `FROM` clause for more flexibility             |

#### Summary

* **SQL** is the **standard database language** for querying and modifying relational databases.
* **T-SQL** is a **Microsoft-specific extension** of SQL with additional **procedural and functional enhancements**.
* T-SQL improves flexibility and power for **SQL Server environments**, especially for scripting and automating complex database tasks.

### Section 2: PL/SQL — Oracle’s Procedural Language Extension

#### What Is PL/SQL?

* **PL/SQL (Procedural Language/SQL)** is Oracle's proprietary extension of **SQL**.
* Developed specifically to **communicate with Oracle databases**, combining SQL’s data manipulation power with procedural logic (like conditionals and loops).
* Queries are executed using tools like **SQL\*Plus**, which serves as the interface between user commands and the Oracle database server.

#### PL/SQL Block Structure

PL/SQL programs are structured into **blocks**, each consisting of:

| Section     | Description                                            | Optional? |
| ----------- | ------------------------------------------------------ | --------- |
| `DECLARE`   | Declare and initialize variables or constants.         | Yes       |
| `BEGIN`     | Contains all executable SQL statements.                | No        |
| `EXCEPTION` | Handles errors that occur in the `BEGIN` block.        | Yes       |
| `END;`      | Marks the end of the block. Must end with a semicolon. | No        |

#### Example PL/SQL Block

```sql
DECLARE
  numItems INTEGER := 10;
BEGIN
  SELECT itemName
  INTO :item_name
  FROM itemsTable
  WHERE itemNum = numItems;
EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No matching item!');
END;
```

#### Syntax and Features

| Feature                  | Example                              | Notes                                         |
| ------------------------ | ------------------------------------ | --------------------------------------------- |
| **Variable Declaration** | `numItems INTEGER := 10;`            | In `DECLARE` section                          |
| **Executable Block**     | Between `BEGIN` and `END;`           | Must contain at least one statement           |
| **Null Statement**       | `NULL;`                              | Used when no operation is intended            |
| **Exception Handling**   | `WHEN NO_DATA_FOUND THEN ...`        | Optional but adds robustness                  |
| **Delimiters**           | `;`, `--`, `,`                       | Semicolon ends a statement, `--` for comments |
| **Comments**             | `-- single-line`, `/* multi-line */` | Not executed, useful for documentation        |

#### SQL\*Plus

* **SQL\*Plus** is Oracle’s **command-line interface** for executing PL/SQL scripts and queries.
* It displays query results and supports loading, editing, saving, and running scripts.

#### Summary

* **PL/SQL** is Oracle’s procedural language built on top of SQL, used to run logic and database commands in structured blocks.
* A PL/SQL block typically includes optional **declaration**, required **execution**, and optional **exception handling** sections.
* Executed in tools like **SQL\*Plus**, PL/SQL enhances the capability of SQL by introducing logic, control structures, and robust error handling.

### Section 3: Dynamic SQL and Its Risks

#### What Is Dynamic SQL?

* **Dynamic SQL** refers to **SQL statements that are generated and executed at runtime**.
* Used when the **exact query details** (e.g., table name, filter values) are **not known until execution**.
* Example use case: **Search functionality** where users input parameters dynamically (e.g., Amazon search).

#### Static vs. Dynamic SQL

| Type        | Description                         | Known at Compile Time? |
| ----------- | ----------------------------------- | ---------------------- |
| Static SQL  | Predefined SQL with fixed structure | Yes                    |
| Dynamic SQL | Built and executed at runtime       | No                     |

#### Example of Dynamic SQL in SQL Server

```sql
DECLARE @tableName VARCHAR(100)
DECLARE @artistID INT
DECLARE @cmd VARCHAR(4000)

SET @tableName = 'tblArtist'
SET @artistID = 15

SET @cmd = 'SELECT artistID, artistName FROM ' + @tableName + ' WHERE artistID = ' + CAST(@artistID AS VARCHAR)
EXEC(@cmd)
```

* `@cmd` stores the **constructed query string**.
* `EXEC(@cmd)` executes the dynamic SQL.

#### Benefits of Dynamic SQL

* **Flexibility**: Works well when query structure depends on runtime inputs.
* **User-defined operations**: Enables dynamic filters, search features, custom reports.
* **Supports automation**: For tasks like dynamically accessing archived vs. live tables.

#### Downsides of Dynamic SQL

* **Performance Overhead**: The database engine must compile each new dynamic query.
* **Complexity**: Harder to debug and maintain due to variable substitution.
* **User Burden**: Too many parameters may overwhelm the user.

#### SQL Injection Risk

* **SQL Injection** is a major **security vulnerability** where attackers insert malicious SQL code.
* Happens when **user input is not sanitized** before being used in dynamic SQL.
* Example of an injection:

  ```sql
  ' OR 1=1; DROP TABLE Students; --
  ```
* **Mitigation** strategies:

  * Use **parameterized queries**.
  * Validate and sanitize **user inputs**.
  * Limit **user permissions**.
  * Regularly **update and patch** the system.

#### Summary

* **Dynamic SQL** enables building SQL queries on the fly, making database operations more responsive and flexible.
* It is especially useful when the query structure is unknown until user input is received.
* However, it comes with **performance** and **security concerns**, especially the risk of **SQL Injection**.
* Always implement **best practices** to ensure dynamic SQL is used safely and efficiently.
