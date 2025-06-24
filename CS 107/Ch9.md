### Section 1: Database Concurrency, Locking, and Transactions

#### What Is Concurrency?

* **Database Concurrency** is the ability of a database to allow **multiple users or processes** to access and modify data **simultaneously**.
* Example: Thousands of users booking airline tickets at the same time.

#### Transactions

* A **transaction** is an **indivisible unit of work** in a database.
* All operations in a transaction must either:

  * **COMMIT** (all changes saved)
  * **ROLLBACK** (revert all changes if an error occurs)
* Ensures **data consistency** across operations.

#### Locking Mechanisms

| Lock Type                  | Description                                                                     |
| -------------------------- | ------------------------------------------------------------------------------- |
| **Shared (Read) Lock**     | Allows **multiple users** to read the same data. Prevents updates during read.  |
| **Exclusive (Write) Lock** | Allows **only one user** to update data. Blocks all reads/writes during update. |
| **Implicit Lock**          | Automatically handled by the **database engine**.                               |
| **Explicit Lock**          | Programmatically placed by **developers**.                                      |

#### Example: Shopping Cart Scenario

1. **Add to Cart** → Shared lock on item (others can view stock).
2. **Checkout Begins** → Exclusive lock on item (prevents updates by others).
3. **Payment Success** → `COMMIT`: Updates inventory and releases lock.
4. **Payment Fails** → `ROLLBACK`: Inventory remains unchanged, lock released.

#### Concurrency Side Effects and Solutions

| Issue                   | Description                                                                  | Solution                      |
| ----------------------- | ---------------------------------------------------------------------------- | ----------------------------- |
| **Dirty Read**          | Reads **uncommitted** data from another transaction                          | Use **exclusive write locks** |
| **Non-Repeatable Read** | Reads the **same row returns different results** in one transaction          | Use **shared read locks**     |
| **Phantom Rows**        | **Different row sets** are returned from the same query within a transaction | Use **range locks**           |

#### Transaction Control

| Command     | Description                                      |
| ----------- | ------------------------------------------------ |
| `COMMIT`    | Saves all changes made during the transaction.   |
| `ROLLBACK`  | Reverts all changes made during the transaction. |
| `SAVEPOINT` | Sets a checkpoint within a transaction.          |

#### Summary

* **Concurrency** boosts performance but must be managed to prevent **data inconsistencies**.
* Use **transactions** to group operations atomically.
* Apply **locking mechanisms** (shared/exclusive) to manage access.
* Mitigate concurrency side effects like **dirty reads**, **non-repeatable reads**, and **phantom rows** using appropriate **locking strategies**.

### Section 2: Persistence in Databases and Systems

#### What Is Persistence?

* **Persistence** refers to the **continued existence** of a process or object **beyond the termination** of its parent program or system shutdown.
* Achieved via **non-volatile storage** (e.g., hard drives), not volatile memory (e.g., RAM).

#### Real-World Example

* A browser like Chrome crashes and reopens tabs after restart → Tabs = **persistent state**.
* The state was saved in **persistent storage** and retrieved after failure.

#### Types of Persistence

| Type                    | Description                                                               |
| ----------------------- | ------------------------------------------------------------------------- |
| **Object Persistence**  | Object remains in memory or storage beyond its parent process's lifetime. |
| **Process Persistence** | System processes remain active or recoverable unless explicitly killed.   |

#### Object Persistence in Databases

* **Persistent Object**: Continues to exist and remain accessible **after the program ends**.
* Requires storage beyond traditional RDBMS, as **objects ≠ records/tables**.

| Database Type | Description                                                                                 |
| ------------- | ------------------------------------------------------------------------------------------- |
| **OODBMS**    | Object-Oriented DBMS, stores data as objects with features like inheritance, encapsulation. |
| **ORDBMS**    | Object-Relational DBMS, merges RDBMS structure with object-like capabilities.               |

#### Importance of Persistent Data

* **Static**: Does not change automatically with time.
* **Stable**: Not deleted unless by user or authorized process.
* **Time-Independent**: Persists beyond parent process's lifespan.
* **Non-Volatile**: Survives system restarts and power outages.
* **Recoverable**: Data is retained even after failures.
* **Cross-Platform Accessible**: Format is stable and universally accessible.

#### Persistent Databases vs. Transient Data

| Type                | Behavior                                                              |
| ------------------- | --------------------------------------------------------------------- |
| **Persistent Data** | Exists beyond transaction boundaries, stored in non-volatile storage. |
| **Transient Data**  | Temporary, lost when the transaction or session ends.                 |

#### Object Persistence Models

| Model      | Features                                                                                                        |
| ---------- | --------------------------------------------------------------------------------------------------------------- |
| **OODBMS** | Full object support (encapsulation, inheritance, polymorphism). Uses unique object IDs. Better for new systems. |
| **ORDBMS** | Blends object features with SQL and relational models. Useful for legacy systems and SQL compatibility.         |

#### Summary

* **Persistence** ensures data or processes outlive their parent environment.
* **Process persistence** preserves system function across reboots or failures.
* **Object persistence** ensures data longevity and cross-application accessibility.
* Use **OODBMS** for new, object-oriented systems and **ORDBMS** for extending SQL-based legacy systems into object-based environments.

### Section 3: Data Integrity and Two-Phased Locking (2PL)

#### What Is Data Integrity?

* **Data integrity** ensures that **data is accurate, consistent, and reliable** over its lifecycle.
* A database lacking integrity may display **non-existent** or **inconsistent** data during or across transactions.

#### Key Terms

| Term                            | Definition                                                                             |
| ------------------------------- | -------------------------------------------------------------------------------------- |
| **Transaction**                 | An indivisible unit of work (e.g., transfer of funds). Either fully succeeds or fails. |
| **Concurrency**                 | Multiple users/processes accessing shared data simultaneously.                         |
| **Database Lock**               | Mechanism to restrict access to shared data to maintain integrity.                     |
| **Transaction Isolation Level** | Determines **visibility of data** between concurrent transactions.                     |
| **Multi-user System**           | Supports multiple concurrent users, where integrity challenges are more likely.        |

#### Lock Types

| Lock Type             | Behavior                                                          |
| --------------------- | ----------------------------------------------------------------- |
| **Read (Shared)**     | Allows multiple concurrent reads; no updates allowed during read. |
| **Write (Exclusive)** | Only one transaction can access; blocks all other reads/writes.   |

#### Transaction Isolation Levels

| Level                | Description                                                      |
| -------------------- | ---------------------------------------------------------------- |
| **Read Uncommitted** | Can read uncommitted (dirty) data → Low integrity.               |
| **Read Committed**   | Reads only committed data; may still allow non-repeatable reads. |
| **Repeatable Read**  | Prevents non-repeatable reads; not phantom reads.                |
| **Serializable**     | Highest isolation; prevents all anomalies → Lower concurrency.   |

#### Two-Phased Locking (2PL)

* **2PL Protocol** has two phases:

  * **Growing Phase**: Acquire locks (read/write).
  * **Shrinking Phase**: Release locks; no new locks allowed.
* Guarantees **serializability**, ensuring transaction results match serial execution.

##### Deadlocks in 2PL

* **Deadlock**: Two transactions wait for each other's locked resources indefinitely.
* **Example**:

  * T1 locks A, then requests B.
  * T2 locks B, then requests A → Both wait forever.

##### Resolving Deadlocks

| Method                        | Description                                                                                                |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Conservative 2PL**          | Acquire all locks **before** transaction starts. Abort if not all are available.                           |
| **Strict 2PL (S2PL)**         | **Exclusive locks held** until transaction commits or rolls back. Prevents cascading rollbacks.            |
| **Strong Strict 2PL (SS2PL)** | **All locks (read + write)** held until transaction ends. Ensures total isolation and strict commit order. |

#### Summary

* **Data integrity** is preserved through proper **transactions, locks**, and **isolation levels**.
* **2PL** is foundational for achieving **serializable** transaction schedules.
* Variants like **S2PL** and **SS2PL** add protection against cascading rollbacks and ensure commit order.
* Proper configuration of these mechanisms ensures **integrity, concurrency, and performance** in multi-user databases.

### Section 4: Database Transactions and ACID Properties

#### What Is a Transaction?

* A **database transaction** is a **group of related tasks** that results in **reading or writing data**.
* Common in real-world scenarios: banking, shopping, course registration.
* A transaction must **complete all tasks** successfully to preserve **data integrity**.

#### Real-World Example

* John's grading transaction:

  1. Complete exam
  2. Script marked
  3. Marks recorded in master file
  4. Report generated
* **All must succeed**; failure in one means no grade → Transaction fails.

#### ACID Properties of Transactions

| Property        | Description                                                                                                                            |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Atomicity**   | **All or nothing**: Every task in the transaction must complete successfully, or the transaction is aborted.                           |
| **Consistency** | The database must move from one **valid state to another**, adhering to all **integrity rules**.                                       |
| **Isolation**   | Transactions must execute **without interference**. One transaction cannot access data being modified by another until it's completed. |
| **Durability**  | Once a transaction is **committed**, its changes are **permanent**, even if a system crash occurs.                                     |

#### Example Breakdown

| Property        | Scenario                                                                                            |
| --------------- | --------------------------------------------------------------------------------------------------- |
| **Atomicity**   | John’s exam gets graded, but marks aren’t recorded → entire process fails, so no grade issued.      |
| **Consistency** | Membership expiration date calculated incorrectly as 13/01/2016 → violates date rule → abort.       |
| **Isolation**   | Karen’s \$300 and \$500 checks processed simultaneously → concurrency control ensures proper order. |
| **Durability**  | \$300 deducted from Karen’s account → system crash → deduction still persists post-restart.         |

#### Summary

* Transactions in databases must uphold **ACID properties** to ensure **data reliability, integrity, and consistency**.
* Multi-user environments with **concurrent transactions** demand mechanisms like **concurrency control** and **transaction management** to enforce these principles.

### Section 5: SQL Cursors

#### What Is SQL?

* **SQL (Structured Query Language)** is used to **store, retrieve, and manipulate data** in relational databases.
* Developed by **IBM in the early 1970s**, commercialized by **Oracle in 1979**, and now widely adopted.

#### What Is a Cursor?

* A **cursor** is a **database pointer** that marks a specific position in a result set from a query.
* Think of it like a **mouse pointer**, but in a database — it tracks **which row** is currently being accessed.
* Used to **traverse query results** **row by row**, especially when **sequential processing** is needed.

#### When to Use a Cursor

* Best used when:

  * **Multiple rows** are returned and must be processed **individually**.
  * **Procedural logic** must be applied to each row.
* Usually **avoided** unless absolutely necessary due to **performance overhead**.

#### SQL Server Cursor Syntax

```sql
DECLARE EmployeeCursor CURSOR FOR
SELECT EmployeeID, Title FROM EmployeeTable;

OPEN EmployeeCursor;

FETCH NEXT FROM EmployeeCursor;

WHILE @@FETCH_STATUS = 0
BEGIN
    -- Process each row here
    FETCH NEXT FROM EmployeeCursor;
END

CLOSE EmployeeCursor;
DEALLOCATE EmployeeCursor;
GO
```

| Command          | Purpose                                                                 |
| ---------------- | ----------------------------------------------------------------------- |
| `DECLARE CURSOR` | Defines and names the cursor, associating it with a `SELECT` statement. |
| `OPEN`           | Opens the cursor and evaluates the query.                               |
| `FETCH NEXT`     | Retrieves the **next row** from the result set.                         |
| `@@FETCH_STATUS` | Checks the status of the last `FETCH`.                                  |
| `CLOSE`          | Closes the cursor after use.                                            |
| `DEALLOCATE`     | Frees system resources used by the cursor.                              |

#### Cursor Use in Stored Procedures

* Cursors can be embedded in **stored procedures** using `CREATE PROCEDURE`.
* Useful when automating **row-by-row operations** like custom updates, logging, or conditional processing.

#### Summary

* **Cursors** offer **row-by-row access** to query results in SQL.
* Essential for **sequential processing**, though **rarely preferred** due to performance costs.
* Syntax includes declaring, opening, fetching, and deallocating the cursor — with `@@FETCH_STATUS` guiding loop control.

#### What Does SQL Cursor Syntax Look Like?
* In Microsoft Transact-SQL (SQL Server's variant), cursors affect a number of commands. They include:

`CLOSE` - terminates use of a cursor once you have finished with it.
`CREATE PROCEDURE` - create a stored procedure for use with a database.
`DEALLOCATE` - returns the memory used by a cursor to the system.
`DECLARE CURSOR` - defines a cursor and associates a name with it. This is the first command you must execute for a cursor.
`DELETE` - removes a row in a table.
`FETCH` - retrieves the information stored at the position indicated by a cursor.
`OPEN` - creates a connection to the cursor so it can be used.
`UPDATE` - changes the information in a record.
`SET` - associates information with various internal SQL values.

### Section 6: Roles and Responsibilities of a Database Administrator (DBA)

#### Who Is a DBA?

* A **Database Administrator (DBA)** is the **custodian of organizational data**, responsible for both **technical management** and **administrative oversight** of databases.
* Key focus areas: **configuration, security, access control, and documentation**.

#### Core Responsibilities of a DBA

| Responsibility                        | Description                                                                                                                |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Database Configuration**            | Install, configure, and maintain database environments (hardware + software).                                              |
| **Security Management**               | Enforce **least privilege** access, manage user roles, permissions, and authentication.                                    |
| **Access Control**                    | Use **schemas, roles, groups**, or **users** to grant appropriate access levels.                                           |
| **Documentation**                     | Maintain comprehensive and updated documentation on system architecture, security, and changes.                            |
| **Backup and Recovery**               | Define and manage **backup schedules**, **transaction log management**, and ensure recovery processes are well-documented. |
| **Monitoring and Auditing**           | Track changes, maintain **logs**, and manage incidents and audit trails.                                                   |
| **Restoration and Disaster Recovery** | Rebuild or reconfigure systems after failures, using proper documentation.                                                 |

#### Principle of Least Privilege

* Users are only granted the **minimum access** required for their role.
* Reduces chances of **accidental or malicious misuse**.
* Managed more effectively through **roles/groups/schemas** than assigning permissions directly to users.

#### Security Policy Documentation Requirements

| Element                         | Description                                                              |
| ------------------------------- | ------------------------------------------------------------------------ |
| **Security Mechanisms**         | Methods used (e.g., roles, users, schemas)                               |
| **Permissions Mapping**         | Privileges assigned to each security principle                           |
| **Change History**              | Records of modifications to access/security policies                     |
| **Breach Logs and Resolutions** | Documentation of any access/security incidents and how they were handled |

#### Database System Documentation Essentials

| Component                  | Description                                                             |
| -------------------------- | ----------------------------------------------------------------------- |
| **Hardware Requirements**  | Server specs, memory, disk, OS version, clustering details              |
| **Software Requirements**  | DBMS version, required tools, configuration details                     |
| **Database Configuration** | Storage layout, transaction log settings, resource management           |
| **Database Objects**       | Tables, columns, keys, constraints, views, triggers                     |
| **E-R Diagrams**           | Visual representation of relationships; helpful in small/medium systems |
| **Job Schedules**          | Backup schedules, system updates, batch job timings                     |
| **Change Logs**            | Patch applications, schema changes, user account updates                |
| **Responsibility Matrix**  | Who handles what aspects of the database                                |

#### Tools for Documentation

| Tool                | Platform Support                        | Features                                            |
| ------------------- | --------------------------------------- | --------------------------------------------------- |
| **Redgate SQL Doc** | SQL Server                              | Auto-documentation of schema and relationships      |
| **ApexSQL Doc**     | SQL Server                              | Rich UI and detailed configuration support          |
| **Elasoft SqlSpec** | Multi-platform                          | Lightweight, auto-generates technical documentation |
| **Dataedo**         | Multi-platform (free version available) | Interactive diagrams, cross-platform support        |

#### Summary

* DBAs play a crucial role in **managing, securing, and documenting** database systems.
* They enforce **least privilege**, maintain detailed **access controls**, and ensure **disaster recovery readiness**.
* Effective use of **documentation tools** and procedures enables **system restoration**, training, audits, and compliance tracking.

### Section 7: Database Security

#### Definition

**Database Security**: The collective processes, policies, and technologies used to protect a database from compromise in **confidentiality, integrity, and availability (CIA Triad)**. It involves securing the **data**, **DBMS**, **application interfaces**, and **physical infrastructure**.

---

#### Major Threats and Vulnerabilities

| Type                         | Description                                                                                   |
| ---------------------------- | --------------------------------------------------------------------------------------------- |
| **SQL/NoSQL Injection**      | Attackers insert malicious queries via user input fields.                                     |
| **Buffer Overflow**          | Attackers exceed input size limits to overwrite adjacent memory and potentially execute code. |
| **Insider Attacks**          | Threats from within the organization. Includes:                                               |
| - Malicious Users            | Intentional sabotage or theft of data.                                                        |
| - Compromised Users          | Credentials stolen and used maliciously.                                                      |
| - Unintentional Threats      | Human error due to lack of training or awareness.                                             |
| **Malware**                  | Includes viruses, ransomware, spyware, and backdoors.                                         |
| **Denial-of-Service (DoS)**  | Flooding the system with requests, making it unavailable to real users.                       |
| **Software Vulnerabilities** | Bugs and exploits in DBMS or OS that allow privilege escalation or data theft.                |
| **Physical Damage/Loss**     | Theft or destruction of servers, hard drives, or other storage media.                         |

---

#### Database Security Best Practices

| Practice                    | Description                                                                                      |
| --------------------------- | ------------------------------------------------------------------------------------------------ |
| **Encryption**              | Encrypt data **in transit and at rest**. Protect encryption keys separately.                     |
| **Authentication**          | Use **multi-factor authentication (MFA)**, strong passwords, and **least privilege** policies.   |
| **Physical Security**       | Secure server locations with locks, access logs, and surveillance. Critical for on-prem servers. |
| **Firewalls**               | Use network and application-level firewalls to restrict traffic to the database.                 |
| **Auditing**                | Track access, changes, and anomalies through **regular audit logs and reports**.                 |
| **Backups**                 | Regular encrypted backups with **routine recovery testing** to ensure data reliability.          |
| **Server Separation**       | Isolate the database from web/app servers to reduce attack surface.                              |
| **Cybersecurity Insurance** | Provides financial coverage in the event of a breach or data loss.                               |

---

#### Importance of Database Security

| Reason                     | Impact                                                                                      |
| -------------------------- | ------------------------------------------------------------------------------------------- |
| **Data Value**             | Intellectual property, financial records, and personal data are invaluable.                 |
| **Compliance**             | Avoid fines for breaches of HIPAA, GDPR, CCPA, etc.                                         |
| **Reputation Management**  | Data loss can erode customer trust and damage brand integrity.                              |
| **Operational Continuity** | Downtime from breaches can halt operations and revenue generation.                          |
| **Cost of Recovery**       | Expenses from forensics, legal fees, infrastructure replacement, and customer compensation. |

---

#### Lesson Summary

* **Database security** encompasses safeguarding all components of the database system — including data, software, hardware, and access points.
* It guards against **external and internal threats**, including injection attacks, malware, and human error.
* **Best practices** like encryption, MFA, backups, and isolation ensure the **CIA triad** is maintained.
* With data becoming increasingly valuable, the consequences of security failures can be **catastrophic** — financially, legally, and reputationally.
