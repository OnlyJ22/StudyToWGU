Look at  204 || 303 -> Ch4.md for more content

### Section 1: SQL Databases and Relationships

#### What Is SQL?

* **SQL (Structured Query Language)**: A language used to manage and manipulate **relational databases**.
* Stores **data in tables** and defines **relationships** between tables via **keys**.

#### SQL Relationships Overview

* SQL databases support three primary types of **relationships** (also known as **cardinality**):

  * **One-to-One (1:1)**
  * **One-to-Many (1\:N)**
  * **Many-to-Many (M\:N)**

#### Primary and Foreign Keys

* **Primary Key**:

  * Uniquely identifies each row in a table.
  * Example: `StudentID` in the `Students` table.
* **Foreign Key**:

  * References a primary key in another table.
  * Enforces **referential integrity**.
  * Example: `StudentID` in `StudentCourses` references `Students`.

#### Entity Tables

* Core tables:

  * **Students** (`StudentID`, Name, etc.)
  * **Courses** (`CourseID`, Title, etc.)
  * **Lecturers** (`LecturerID`, Name, etc.)

#### Intersection Tables

* Required to model **many-to-many (M\:N)** relationships:

  * **Students ↔ Courses**:

    * Table: `StudentCourses`
    * Fields: `StudentID`, `CourseID`, `Semester`, `StudentCourseID`
    * Composite Key: `StudentID + CourseID`
  * **Lecturers ↔ Courses**:

    * Table: `CourseLecturers`
    * Fields: `LecturerID`, `CourseID`
    * Composite Key: `LecturerID + CourseID`

#### Relationship Examples

| Relationship                                    | Type | Implementation                                                  |
| ----------------------------------------------- | ---- | --------------------------------------------------------------- |
| One student registers for many courses          | 1\:N | `StudentCourses` links `Students` to `Courses`                  |
| One lecturer teaches many courses               | 1\:N | `CourseLecturers` links `Lecturers` to `Courses`                |
| One course can have many students and lecturers | M\:N | Both `StudentCourses` and `CourseLecturers` intersection tables |

#### Key Design Principles

* **Avoid duplication**: Never store multiple courses in a single field or repeat student info for each course.
* Use **intersection tables** for M\:N relationships.
* Maintain **data integrity** through primary and foreign keys.

#### Summary

* SQL databases model data using **tables** and **relationships**.
* Relationships (1:1, 1\:N, M\:N) are managed using **primary** and **foreign keys**.
* **Intersection tables** enable accurate modeling of M\:N relationships.
* Proper relational design ensures data consistency, scalability, and integrity.
