### 🧠 Section 1: Intro

#### 📘 What Is Data?

* **Data** are raw facts or values (e.g., numbers, text, signals).
* In scientific and computing contexts, “data” is **plural** (e.g., “the data are accurate”), but casual usage may treat it as singular.
* Data by itself doesn’t have meaning—until it’s processed or contextualized.

#### 🔄 Analog vs. Digital Data

* **Analog Data**:

  * **Continuous**, flowing, and often natural (e.g., human voice, light, temperature).
  * Infinite variation is possible.
* **Digital Data**:

  * **Discrete**, with defined steps or values (e.g., 0s and 1s).
  * Computers can only process digital data.
  * Real-world analog signals are **sampled** and **converted** into digital data for storage and processing.

#### 🧠 Types of Digital Data

* All types—text, numbers, images, audio, video—are **ultimately stored in binary**.
* Each data type requires specific **encoding methods** (e.g., ASCII for text, RGB for images, MP3 for audio).
* As technology advanced, we moved from simple text/numbers to **rich multimedia**.

#### 🗂️ Databases and Their Structure

* A **database** is a structured collection of data, typically organized for easy retrieval and use.
* Most use **tables** to structure data:

  * **Fields** = columns (data categories, like "Name" or "Phone Number").
  * **Records** = rows (each entry or person).
  * **Header row** names each field.
* Example: Customer database might include ID, Name, Phone, Address, Purchase History, etc.

#### 🧰 Database Management System (DBMS)

* Specialized software that allows users to:

  * **Input** new data
  * **Store** data securely
  * **Retrieve** data efficiently
  * **Manage** updates and relationships between data
* Examples: MySQL, Microsoft Access, Oracle DB, PostgreSQL

#### ℹ️ Data vs. Information

* **Data** = raw and context-less (e.g., “42”, “Alice”).
* **Information** = data + context/structure (e.g., “Alice is 42 years old”).
* What counts as “information” depends on **your goal**. For example:

  * If you’re making sales calls, names and numbers may not be enough—you need buying history, industry, and preferences.

### 🧠 Section 2: Data Storage

#### 💾 What Is Data Storage?

* **Data storage** is the process of saving and retrieving digital information in a way that computers can process.
* While ancient methods like cave paintings and paper stored information physically, modern data storage is **electronic** and optimized for **speed, capacity, and accessibility**.

---

#### 🧪 Early Electronic Memory

* **Pre-electronic storage**: Stone, paper, and **punched cards** (used to input data via hole patterns).
* **First true electronic storage**:

  * **Williams-Kilburn tube** (1947) – used cathode ray tubes to store binary data.
  * Introduced the concept of **random access** to stored bits.
* Followed by:

  * **Magnetic tape** (like audio cassettes)
  * **Magnetic drums** – early forms of memory with rotating cylinders

---

#### 🧲 Hard Drives (HDDs)

* Invented to provide **long-term, high-capacity** data storage.
* Data is stored **magnetically** on spinning platters.
* Accessed via a **mechanical arm** with a read/write head.
* Known for:

  * **High capacity**
  * **Mechanical reliability**, though prone to wear and physical damage
  * Still in use, especially in servers or backup systems

---

#### ⚡ Solid State Drives (SSDs)

* Use **flash memory** (no moving parts).
* Advantages over HDDs:

  * Faster boot-up and file access
  * More **shock-resistant**
  * Smaller and lighter
* **M.2 SSDs** connect directly to the motherboard and use **NVMe** for ultra-fast data transfers.
* Downsides:

  * Can be more expensive per GB than HDDs
  * Often have **lower total capacity** for the same price

---

#### 📼 Historical Disk Storage

* **Floppy disks** (1980s–early 2000s):

  * First major portable storage format
  * Low capacity (1.44MB typical), but revolutionary at the time
* **Optical Discs**:

  * **CDs** (up to 700MB), **DVDs** (up to 4.7GB), **Blu-rays** (25GB+)
  * Used lasers to read/write data
  * Common for music, movies, software
  * Now largely obsolete for everyday use

---

#### 🔌 Portable Flash Storage

* Enabled **mobile and removable** data storage.
* Key examples:

  * **USB flash drives** – plug-and-play, small and convenient
  * **SD cards** – widely used in phones, cameras, drones
  * **External SSDs/HDDs** – for portable large-capacity backups

---

#### ☁️ Cloud Storage

* Stores data on **remote servers** accessed via the internet.
* Key benefits:

  * Access your data from **any device, anywhere**
  * Often includes **automatic backup and syncing**
* Examples: Google Drive, Dropbox, iCloud, OneDrive
* Relies on physical data centers filled with HDDs and SSDs—but **abstracts the hardware** for the user.

---

#### 📘 Summary of Key Transitions

| Era           | Storage Medium                  | Key Characteristics                     |
| ------------- | ------------------------------- | --------------------------------------- |
| 1940s–50s     | Williams-Kilburn, punched cards | First binary data storage               |
| 1960s–70s     | Magnetic tape/drums             | Sequential access, early computers      |
| 1980s–90s     | HDDs, floppy disks              | Larger capacity, portable               |
| 2000s–2010s   | CDs, DVDs, USBs                 | Optical storage, flash memory           |
| 2010s–present | SSDs, M.2, cloud storage        | Fast, reliable, scalable, remote access |

### 🧠 Section 3: Data Storage Devices and Types

#### 🧾 Definition of a Data Storage Device

* A **data storage device** is a **technology used to hold information**, either temporarily or permanently.
* Data is **organized** (structured) in such a way that it can be easily retrieved later.
* A helpful analogy: storage devices are like a **dresser**—each drawer (or storage location) holds specific content you can access when needed.

---

#### ⏱️ The Pace of Information

* In our high-speed digital world, data is generated **constantly and rapidly** (e.g., stock tickers, weather feeds, news updates).
* This constant stream of information isn't discarded—it’s **stored** in structured devices for later use, analysis, or backup.

---

#### 🧠 Two Main Categories of Data Storage

1. **Dynamic Storage**

   * Requires **power** to retain information.
   * Volatile—data is lost when power is turned off.
   * Example: **RAM (Random Access Memory)**

     * Used for temporary, fast-access operations while a computer is running.

2. **Static Storage**

   * Retains information **even when power is off**.
   * Used for long-term data retention.

---

#### 🧲 Types of Static Storage

1. **Magnetic Storage**

   * Data encoded using **magnetism on metal/plastic surfaces**.
   * Examples:

     * Floppy disks
     * Hard disks (HDDs)
     * Magnetic tapes (cassette tapes, DATs)
   * Legacy tech but still used for **backups and archival storage**.

2. **Optical Storage**

   * Data stored as patterns (bumps or pits) read with **lasers**.
   * Examples:

     * **CDs** (700 MB)
     * **DVDs** (4.7–8.5 GB)
     * **Blu-ray discs** (25–50 GB+)
   * Once common, now less used due to flash/cloud alternatives.

3. **Flash Storage**

   * Uses **flash memory chips**; no moving parts.
   * Maintains data with power off.
   * Examples:

     * **USB flash drives**
     * **SD cards**
     * **Solid State Drives (SSDs)**
   * Fast, reliable, and compact—now dominant in consumer devices.

4. **Cloud Storage**

   * Stores data **remotely** on physical servers accessed over the internet.
   * Examples:

     * **Amazon AWS**, **Google Cloud**, **Microsoft Azure**
   * Allows on-demand access, syncing across devices, and remote backups.

5. **Paper Storage**

   * Historical method using **punched holes in cards or tape**.
   * Example: **punch cards**
   * Largely obsolete, but foundational in early computing.

---

#### ⚖️ Why So Many Storage Types?

System designers must balance **three key factors**:

1. **Speed**

   * Some operations (like backups) can tolerate slower speeds.
   * Others (like live editing or gaming) demand **fast access**.

2. **Cost**

   * Faster storage is usually **more expensive**.
   * Mixing storage types helps **reduce overall system cost**.

3. **Evolution**

   * As **technology advances**, new storage forms emerge, while older ones become obsolete or niche.
   * Designers must keep systems **current and compatible**.

---

#### 📘 Final Summary

* A **data storage device** holds digital information in a structured way.
* Storage can be **dynamic (temporary)** or **static (permanent)**.
* Static storage includes **magnetic, optical, flash, cloud**, and even **paper-based** methods.
* The variety exists to **balance speed, cost, and technological advancement**—a constant goal in system design.

### 🧠 Section 4: Databases and Their Types

#### 📘 What Is a Database?

* A **database** is a computer-based structure that **saves, organizes, protects, and delivers data**.
* Think of it like a digital **library for data**—structured for easy access and management.
* The **Database Management System (DBMS)** is the software that allows users and programs to interact with one or more databases.

---

#### 📊 Types of Databases

1. **Text Databases**

   * Basic storage using **plain text files** in rows and columns.
   * Each line = one **record**.
   * Minimal features but functional for simple tasks (e.g., Linux’s `/etc/passwd`).

2. **Desktop Database Programs**

   * Designed for **single-user** use on local machines.
   * Examples: **Microsoft Access**, **Excel**
   * Better performance and structure than text files; suitable for small-scale projects.

3. **Relational Databases (RDBMS)**

   * The most **common** type of database.
   * Examples: **MySQL**, **SQL Server**, **Oracle**, **PostgreSQL**
   * Organizes data into **tables** made up of **columns** and **rows**.
   * Key features:

     * **Multiple user support**
     * **Security controls**
     * **Data normalization**
     * High performance for structured data

4. **NoSQL and Object-Oriented Databases**

   * **NoSQL**:

     * Focused on scalability, flexibility, and speed.
     * Data is **denormalized** (stored in large chunks for speed).
     * Ideal for big data and real-time applications.
   * **Object-Oriented**:

     * Stores data as **objects**, closely matching how programming languages (like Java) model data.

---

#### 🧱 Key Concept: Normalization

* **Normalization** breaks data into the **smallest possible pieces**.
* Example: Instead of storing “John Smith” in one field, it would be split into “First Name: John” and “Last Name: Smith.”
* Ensures **efficient sorting, searching, and updating**.
* Required in RDBMS, but **not** in NoSQL systems.

---

#### 🗃️ Database Design Categories

1. **Operational (Transactional) Databases**

   * Used for **day-to-day tasks** and real-time data processing.
   * Require **fast reads/writes**.
   * Examples: Inventory systems, e-commerce platforms.
   * Support **transactions**: Ensure all parts of a process succeed before saving.

2. **Data Warehouses**

   * Store **historical versions** of data.
   * Not used for real-time interaction, but for **trend analysis and reporting**.
   * Example: A customer’s old and new last names with timestamps.
   * Supports **Business Intelligence (BI)** and long-term decision-making.

---

#### 🖼️ Common Symbol

* Databases are typically represented by a **cylindrical icon** in diagrams and models.

### 🧠 Section 5: Database Structures, Data vs. Information, and DBMS

#### 🔹 What Are Data?

* **Data** are raw facts or values without context.
* Every computer process involves working with data.
* **In formal usage**, "data" is plural (e.g., *"the data are stored"*), though casual usage often treats it as singular.

---

#### 🗃️ Database Structure: Organizing Data

* A **database** is an **organized collection of data**, designed for easy access, updating, and management.
* **Tables** are the primary structure used in databases to store data.

  * A **table** is like a **two-dimensional array**, using **rows and columns**.
  * Each **row** = a **record**, also called an **object** or **entity**.
  * Each **column** = a **field**, also called an **attribute**.

##### 🧩 Example Breakdown:

* A **customer database** might have:

  * **Fields**: Customer ID, Name, Phone Number
  * **Records**: Each customer’s details
  * The **first row** is usually a **header** indicating field names.

##### Key Properties of Tables:

1. **Uniform Field Types**: All entries in a column are of the same type (e.g., all numbers, all text).
2. **Mixed Record Types**: Rows may contain different types (text + number).
3. **No Blank Records or Fields**: Though individual values can be missing, there are no entirely empty rows or columns.
4. **Data Integrity**: The structure enforces constraints (e.g., only numbers in phone number fields).

---

#### 🧰 DBMS: Database Management System

* A **DBMS** is specialized software that manages databases.

  * Functions: **input, store, retrieve, manage** data.
  * Supports **multi-user access**, **security**, **performance optimization**.
* Examples of DBMS software: MySQL, Oracle, PostgreSQL, Microsoft SQL Server.

##### 🗂️ Database Files:

* A **database file** is like any other file—it can be copied, moved, or deleted.
* File formats vary by DBMS (e.g., `.mdb` for Microsoft Access, `.sqlite` for SQLite).

---

#### 🔍 Data vs. Information

* **Data** = Raw, unstructured facts (e.g., a list of stock prices)
* **Information** = Data that has been **processed and given context**, helping answer questions or support decisions.

##### Example:

* Raw data: `145.32, 147.20, 149.00`
* Information: *"Apple's stock rose from \$145.32 to \$149.00 over three days."*

> 📌 **Perspective matters**: What’s information for one purpose (e.g., stock price trends) might still be unprocessed data for another (e.g., assessing company financial health).

---

#### 🧾 Summary of Key Elements

| **Concept**     | **Explanation**                                      |
| --------------- | ---------------------------------------------------- |
| **Data**        | Basic facts/values, unstructured                     |
| **Information** | Data processed with context                          |
| **Database**    | Organized structure for storing data                 |
| **Table**       | Two-dimensional structure (records + fields)         |
| **Record**      | A row in a table (one entity)                        |
| **Field**       | A column in a table (one attribute of all records)   |
| **DBMS**        | Software for managing and interacting with databases |


### 🧠 Section 6: Database Terminology & Relationships

#### 🗃️ What Is a Database?

* A **database** is a **structured collection of data**, typically organized into **tables** (rows and columns).
* Each individual piece of data is stored at the intersection of a **row (record)** and a **column (field)**.
* Fields are defined with **data types** (e.g., text, integer, date) to ensure consistency and validity.

---

#### 🔑 Keys in Databases

1. **Primary Key**

   * A **unique identifier** for each record in a table.
   * Ensures **no duplicates** and allows each record to be accessed or related precisely.
   * Example: `CustomerID` or `Email`

2. **Foreign Key**

   * A field in one table that refers to the **primary key in another table**.
   * Establishes **relationships** between tables.
   * Helps link data across multiple tables without duplication.

---

#### 💬 SQL: Structured Query Language

* **SQL** is the standard language used to **interact with databases**.
* Used for tasks like retrieving, adding, updating, or deleting data.

#### 💻 SQL Categories:

| Type                                   | Function            | Keywords                               |
| ------------------------------------   | ----------------    | -------------------------------------- |
| **DML (Data Manipulation Language)**   | Modify data         | `SELECT`, `INSERT`, `UPDATE`, `DELETE` |
| **DDL (Data Definition Language)**     | Modify structure    | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`  |
| **DCL (Data Control Language)**        | Manage permissions  | `GRANT`, `REVOKE`                      |
| **TCL (Transaction Control Language)** | Manage transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT`      |
| **Joins (Query Technique)**            | Manage table data   | `INNER JOIN`,`LEFT JOIN`,`RIGHT JOIN`,`FULL JOIN`,`CROSS JOIN`,`SELF JOIN` |

* **Select Statement**: Retrieves and displays data (e.g., `SELECT * FROM Customers;`)

---

#### 🧩 Types of Relationships Between Tables

1. **One-to-One**

   * Each record in Table A matches exactly one in Table B.
   * Example: One person ↔ One passport

2. **One-to-Many** (most common)

   * One record in Table A can relate to **many** in Table B.
   * Example: One customer ↔ Many orders

3. **Many-to-Many**

   * Records in Table A relate to many in Table B, and vice versa.
   * Example: Students ↔ Courses
   * **Junction Table** is used to manage this relationship by breaking it into two one-to-many relationships.

     * Contains foreign keys from both related tables
     * Composite primary key = (ForeignKeyA + ForeignKeyB)

---

#### 🧰 DBMS: Database Management System

* **DBMS** is software that:

  * Stores, retrieves, and manages data
  * Allows users to **query**, update, and manipulate databases
* Examples: **MySQL**, **PostgreSQL**, **Oracle**, **Microsoft SQL Server**

---

#### 🧾 Summary of Key Terms

| Term                 | Definition                                                 |
| -------------------- | ---------------------------------------------------------- |
| **Database**         | Organized collection of structured data                    |
| **Table**            | Data structure of rows and columns                         |
| **Record (Row)**     | One complete entry in a table                              |
| **Field (Column)**   | One data point or attribute per record                     |
| **Primary Key**      | Unique identifier for a record                             |
| **Foreign Key**      | Reference to a primary key in another table                |
| **SQL**              | Language to interact with databases                        |
| **DML**              | SQL commands to change data (`INSERT`, `UPDATE`)           |
| **DDL**              | SQL commands to change table structure (`CREATE`, `DROP`)  |
| **Select Statement** | SQL query to retrieve data                                 |
| **Junction Table**   | Intermediary table for managing many-to-many relationships |

### 🧠 Section 7: Database Records & Record Data

#### 📘 What Is a Record?

* A **record** (also called a **tuple** in relational databases) is a **single row** in a database table.
* Each record contains **related data points** that represent one **object**, **entity**, or **entry**—such as a person, product, or item.
* In a **table**, records are organized **horizontally** (row by row), while fields (also called **attributes**) are organized **vertically** (column by column).

##### Example:

In a customer table, one record might include:

* `Customer ID`: 1025
* `Name`: Jane Doe
* `Email`: [jane.doe@example.com](mailto:jane.doe@example.com)
* `Phone`: 555-1234
* `Birthdate`: 1990-07-15

---

#### 🗂️ Records vs. Fields

| Term                            | Description                                                       |
| ------------------------------- | ----------------------------------------------------------------- |
| **Record (Row / Tuple)**        | A complete entry in a table representing one entity               |
| **Field (Column / Attribute)**  | A specific piece of information in the record (e.g., Name, Email) |
| **Table (Relation / Data Set)** | A collection of records stored together                           |

---

#### 🧩 Records in Practice

* **Tables** can hold hundreds or millions of records.
* A good design includes a **primary key**:

  * A **unique identifier** for each record (e.g., ID numbers)
  * Often **auto-incremented** (e.g., 1, 2, 3, …)
* **Database tools** (like Microsoft Access or MySQL) allow you to easily define primary keys and manage records.

---

#### 🧪 Record Data Types

Each field in a record can hold **different types of data**, depending on what it represents. Here are common examples from a **CD collection table**:

| Field        | Data Type        | Example          |
| ------------ | ---------------- | ---------------- |
| ID           | Number (Integer) | 1                |
| Artist Name  | Text             | Taylor Swift     |
| Album Title  | Text             | Midnights        |
| Genre        | Text             | Pop              |
| Release Date | Date/Time        | 2022-10-21       |
| Rating       | Number           | 9                |
| Length       | Text (or Time)   | 44:00            |
| Label        | Text             | Republic Records |

---

#### 🎯 Why Records Matter

* **Usability**: Records help store and retrieve individual entities easily.
* **Data Integrity**: Through proper structure (e.g., using primary keys), records prevent duplication and inconsistency.
* **Flexibility**: Each record can combine data types (e.g., numbers, dates, text) to describe complex objects like a music album or a customer profile.

---

#### 🧾 Summary of Key Terms

| Term                  | Meaning                                                       |
| --------------------- | ------------------------------------------------------------- |
| **Record (Tuple)**    | A row of data in a table; one complete entry                  |
| **Field (Attribute)** | A column; one type of data across all records                 |
| **Table (Relation)**  | A set of records and fields                                   |
| **Primary Key**       | A unique field that identifies each record                    |
| **Data Type**         | The kind of data stored in a field (text, number, date, etc.) |


### 🧠 Section 8: Database Fields and Field Types

#### 📘 What Are Database Fields?

* A **field** in a database table is a **column** that stores a specific type of data for each record (row).
* Fields are also called **attributes** because they describe characteristics of the record.
* Think of fields as **containers** that define **what kind of data** is stored (e.g., student names, dates of purchase, email addresses).

##### Example:

In a **Student** table:

* `student-id`: Numeric ID
* `student-name`: Alphabetic characters (first and last name)
* `student-email`: Text (email address)

Each of these **fields** holds one **type of data** for **every student (record)** in the table.

---

#### 🧩 Field Characteristics

* **Each field has a unique role** – only one field per type of information in a table (e.g., one student-id field).
* **All values in a field share the same data type** (e.g., all student-ids are numbers).
* **Every row (record)** in the table will contain **a value (or null)** for each field.

---

#### 🔠 Database Field Types

Field types (or **data types**) define **what kind of data can be stored** in a field. This prevents errors and helps the database operate efficiently.

| Field Type           | Description                                  | Example Use                    |
| -------------------- | -------------------------------------------- | ------------------------------ |
| **Character / Text** | Stores alphabetic characters or text strings | Names, addresses, labels       |
| **Boolean**          | Stores only `true` or `false` values         | Flags, yes/no fields           |
| **Integer**          | Stores whole numbers only                    | Student IDs, quantities        |
| **Decimal**          | Stores numbers with decimals                 | Prices, weights                |
| **Date**             | Stores calendar dates                        | Birthdate, purchase date       |
| **Timestamp**        | Stores date and time values                  | Log entries, transaction times |

> 📝 Note: Field type **names vary by DBMS**

* **Text** in Access = **VARCHAR** in Oracle = **String** in some NoSQL databases.

---

#### 🏠 Field Definition Analogy

* Creating a database table is like **designing a house**:

  * You decide how many **rooms (fields)** you need.
  * You define the **purpose** of each room (field type).
  * You ensure that every “room” stores the right kind of item (correct data type for the field).

---

#### 📋 Example Scenario: Sally’s Antique Store

Sally uses a table to track items and their prices:

| **Field**         | **Type**       |
| ----------------- | -------------- |
| `items-purchased` | Character/Text |
| `cost-per-item`   | Decimal        |

This setup ensures:

* Item names are stored as **text**
* Costs are stored as **decimal numbers**, ideal for currency values

---

#### 🧾 Summary of Key Concepts

| Concept                    | Description                                                           |
| -------------------------- | --------------------------------------------------------------------- |
| **Field**                  | A column in a table; holds one type of data                           |
| **Record**                 | A row in a table; one complete data entry                             |
| **Field Type (Data Type)** | Determines what kind of data the field accepts                        |
| **Field Naming**           | Should be descriptive (e.g., `student-email`, `cost-per-item`)        |
| **Field Design**           | Must be set up before entering data to ensure structure and integrity |

### 🧠 Section 9: Database Applications vs. Spreadsheets

#### 📘 What Is a Database Application?

* A **database application** is a **software program** that enables users to **access, manage, and interact with data** stored in a database.
* Its primary functions include:

  * Allowing users to **retrieve only the data they need**
  * Supporting **simultaneous access** by multiple users
  * **Filtering and protecting** data to ensure security and efficiency

##### 🏛️ Historical Note:

* The need to organize and store data goes back thousands of years (e.g., Sumerians tracking goods on clay tablets), highlighting the long-standing importance of **record-keeping systems**—which modern database applications are built to handle on a large scale.

---

#### 🧱 How Databases Work (Structure Overview)

* A **database** consists of one or more **tables**, and each table is structured with:

  * **Rows** (called **records**) — each representing one complete entry (e.g., an employee)
  * **Columns** (called **fields**) — each representing one type of data (e.g., name, hire date)
  * **Data types** assigned to fields — e.g., text, date, number

##### Example:

| employee-id | name  | position   | start-date |
| ----------- | ----- | ---------- | ---------- |
| 101         | Sarah | HR Manager | 2021-06-12 |
| 102         | James | IT Support | 2020-11-04 |

* Users access data via **queries**, which allow them to pull only the information they need, **without altering or viewing the entire dataset**.

---

#### 📊 Databases vs. Spreadsheets

| Feature                         | **Databases**                          | **Spreadsheets**                           |
| ------------------------------- | -------------------------------------- | ------------------------------------------ |
| **Designed for**                | Large-scale data storage and retrieval | Calculations, charts, data analysis        |
| **Multi-user support**          | Yes – optimized for many users at once | Limited and often slow with multiple users |
| **Data handling**               | Efficient querying and filtering       | Manual viewing/editing of data             |
| **Structure**                   | Tables with relationships              | Flat grid of cells                         |
| **Performance with large data** | Scales well with size and users        | Slows down with too many records or users  |

##### Scenario Example:

If four coworkers need to access different parts of the same dataset:

* In a **spreadsheet**, they would all be working on the same file, leading to overlap, slowdowns, or accidental changes.
* In a **database application**, each user would run their **own query**, retrieving only the records relevant to their task—fast, efficient, and secure.

---

#### 🧾 Summary of Key Concepts

| Concept                  | Definition                                                                                |
| ------------------------ | ----------------------------------------------------------------------------------------- |
| **Database Application** | Software used to access, manage, and secure data within a database                        |
| **Table**                | Structure within a database made of rows (records) and columns (fields)                   |
| **Record (Row)**         | One entry in a table (e.g., one employee)                                                 |
| **Field (Column)**       | One category of data in each record (e.g., name, email)                                   |
| **Query**                | A command used to retrieve specific data from the database                                |
| **Spreadsheet**          | A flat-file tool for displaying, analyzing, and graphing data, best for single-user tasks |

