l
#### **Part 1: Introduction and Core Concepts**

**1.1. What is a Database?**
A database is ==a collection of data, typically stored electronically, that can be easily accessed, managed, and updated.==

**1.2. What is a *Relational* Database?**
A relational database is a specific type of database that organizes data into one or more **tables** (or "relations"). Each table consists of **rows** and **columns**. The "relational" aspect comes from the ability to link, or create relationships between, these tables using common fields.

The model was first proposed by E. F. Codd of IBM in 1970. It is the foundation for the most widely used databases today.

**1.3. The Building Blocks (Core Terminology)**

*   **Entity:** A real-world object or concept about which we store data. *Examples: `Customer`, `Product`, `Order`.*
*   **Attribute:** A property or characteristic of an entity. This becomes a column in a table. *Examples: A `Customer` entity might have attributes like `FirstName`, `LastName`, and `EmailAddress`.*
*   **Table (or Relation):** The primary data storage structure. A table is a two-dimensional grid consisting of columns and rows.
    *   **Columns (or Attributes/Fields):** A vertical entity in a table that contains all information of a specific type for all records. It has a name and a data type (e.g., `VARCHAR`, `INT`, `DATE`).
    *   **Rows (or Tuples/Records):** A horizontal entity in a table. It represents a single instance of the entity. For example, one row in a `Customers` table represents one specific customer.
*   **Schema:** The formal definition or "blueprint" of a database's structure. It defines the tables, the columns in each table, their data types, constraints, and the relationships between tables.
*   **Data Types:** Constraints that specify the type of data a column can hold. This is crucial for maintaining **data integrity**. Common types include:
    *   `INTEGER` or `INT`: Whole numbers.
    *   `VARCHAR(n)`: Variable-length character strings (up to `n` characters).
    *   `CHAR(n)`: Fixed-length character strings.
    *   `TEXT`: Long-form text.
    *   `DATE` / `TIME` / `DATETIME`: Date and time values.
    *   `BOOLEAN`: True or False values.
    *   `FLOAT` / `DECIMAL`: Floating-point or fixed-point numbers.

---

#### **Part 2: Keys and Relationships - The "Relational" Core**

Keys are special columns used to enforce uniqueness and link tables together. This is the most critical concept in the relational model.

**2.1. Types of Keys**

*   **Primary Key (PK):**
    *   **Definition:** A column (or set of columns) that uniquely identifies every row in a table.
    *   **Properties:**
        1.  **Must be UNIQUE:** No two rows can have the same primary key value.
        2.  **Must NOT be NULL:** Every row must have a value for its primary key.
    *   *Example:* In a `Students` table, `StudentID` would be the primary key.

*   **Foreign Key (FK):**
    *   **Definition:** A column (or set of columns) in one table that refers to the Primary Key of another table.
    *   **Purpose:** It creates a link or a relationship between the two tables.
    *   *Example:* In an `Orders` table, you might have a `CustomerID` column. This `CustomerID` is a Foreign Key that refers to the `CustomerID` (the Primary Key) in the `Customers` table. This links an order to the customer who placed it.

*   **Composite Key:** A primary key that consists of two or more columns combined to uniquely identify a row. This is used when a single column is not sufficient for unique identification.

*   **Candidate Key:** Any column (or set of columns) that *could* qualify as a primary key (i.e., it is unique and not null). A table can have multiple candidate keys. The one chosen to be the main identifier is the Primary Key.

*   **Superkey:** A set of one or more attributes that, taken collectively, can uniquely identify a row. A Primary Key is a minimal superkey (i.e., you cannot remove any attribute from it and still have it be a unique identifier).

**2.2. Types of Relationships**

These are established using Primary and Foreign Keys.

*   **One-to-One (1:1):** Each record in Table A can be linked to one, and only one, record in Table B, and vice-versa. This is less common.
    *   *Example:* A `Users` table and a `UserProfiles` table. Each user has exactly one profile. The `UserID` in `UserProfiles` would be both a Primary Key and a Foreign Key referencing `Users`.

*   **One-to-Many (1:M):** The most common relationship. One record in Table A can be linked to many records in Table B, but each record in Table B can only be linked to one record in Table A.
    *   *Example:* One `Customer` can have many `Orders`. The `Orders` table would contain a `CustomerID` (FK) to link back to the single customer in the `Customers` table.

*   **Many-to-Many (M:N):** One record in Table A can be related to many records in Table B, and one record in Table B can be related to many records in Table A.
    *   **Implementation:** This cannot be implemented directly. It requires a third table, known as a **Junction Table** or **Linking Table**.
    *   *Example:* `Students` and `Courses`. A student can enroll in many courses, and a course can have many students.
        1.  `Students` Table (PK: `StudentID`)
        2.  `Courses` Table (PK: `CourseID`)
        3.  `Enrollments` Table (Junction Table): Contains `StudentID` (FK) and `CourseID` (FK). The combination of (`StudentID`, `CourseID`) would be its composite primary key.

---

#### **Part 3: Data Integrity**

Data integrity refers to the accuracy, consistency, and reliability of data. Relational databases enforce this through constraints.

*   **Entity Integrity:** Enforced by the **Primary Key**. It ensures that there are no duplicate rows in a table and that the PK field is not empty (NULL).
*   **Referential Integrity:** Enforced by the **Foreign Key**. It ensures that a relationship between two tables remains consistent. A value entered as a foreign key must already exist as a primary key in the parent table (or be NULL, if allowed).
    *   This prevents "orphan records," such as an `Order` for a `CustomerID` that doesn't exist.
    *   **Cascading Actions:** You can define what happens if a referenced PK is updated or deleted (e.g., `ON DELETE CASCADE` would delete all related orders if a customer is deleted).
*   **Domain Integrity:** Enforces the validity of entries for a given column. It's enforced by:
    *   **Data Types:** `INT` column won't accept 'hello'.
    *   **NOT NULL Constraint:** Ensures a column cannot have a NULL value.
    *   **UNIQUE Constraint:** Ensures all values in a column are unique (but allows one NULL).
    *   **CHECK Constraint:** Ensures values meet a specific condition (e.g., `Age > 18`).
    *   **DEFAULT Constraint:** Provides a default value for a column when none is specified.

---

#### Part 4: [[Normalization]]

Normalization is the process of organizing columns and tables in a relational database to minimize **data redundancy** and improve **data integrity**. It aims to prevent data anomalies.

*   **Update Anomaly:** If data is duplicated, updating it in one place but not others leads to inconsistencies.
*   **Insertion Anomaly:** Inability to add a new record because some data is missing (e.g., you can't add a new course until a student enrolls in it if both are in the same table).
*   **Deletion Anomaly:** Deleting one piece of data unintentionally causes other, unrelated data to be deleted.

**The Normal Forms (NF):**

*   **First Normal Form (1NF):**
    1.  The table must have a primary key.
    2.  Each cell must hold a single, **atomic** value (no lists or repeating groups in a single cell).
    *   *Bad:* A `PhoneNumbers` column with "555-1234, 555-5678".
    *   *Good:* Create a separate `PhoneNumbers` table linked by `CustomerID`.

*   **Second Normal Form (2NF):**
    1.  Must be in 1NF.
    2.  All non-key attributes must be **fully functionally dependent** on the *entire* primary key. (This rule only applies to tables with composite primary keys).
    *   *Explanation:* No non-key column should depend on only a *part* of the composite primary key.
    *   *Example:* A table `OrderDetails` has a composite PK (`OrderID`, `ProductID`). If it also has `ProductPrice` and `ProductName`, these depend only on `ProductID`, not the whole key. This is a partial dependency.
    *   *Solution:* Move `ProductPrice` and `ProductName` to a separate `Products` table with `ProductID` as the PK.

*   **Third Normal Form (3NF):**
    1.  Must be in 2NF.
    2.  There should be no **transitive dependencies**.
    *   *Explanation:* A non-key attribute cannot depend on another non-key attribute.
    *   *Example:* A `Students` table has `StudentID` (PK), `StudentName`, `DepartmentID`, and `DepartmentName`. Here, `DepartmentName` depends on `DepartmentID`, which in turn depends on `StudentID`. This is a transitive dependency.
    *   *Solution:* Move `DepartmentID` and `DepartmentName` to a separate `Departments` table. The `Students` table will just hold `DepartmentID` as a foreign key.

*For most applications, achieving 3NF is sufficient.* Higher normal forms (BCNF, 4NF, 5NF) exist for more complex scenarios.

---

#### **Part 5: SQL - The Language of Relational Databases**

**SQL (Structured Query Language)** is the standard language for communicating with a relational database. It is divided into sub-languages:

*   **Data Definition Language (DDL):** Defines the database schema.
    *   `CREATE TABLE/DATABASE`: Creates a new table or database.
    *   `ALTER TABLE`: Modifies an existing table (add/drop a column, change data type).
    *   `DROP TABLE`: Deletes a table.
    *   `TRUNCATE TABLE`: Deletes all data from a table (faster than `DELETE`).

*   **Data Manipulation Language (DML):** Used to manage data within the tables.
    *   `SELECT`: Retrieves data from tables. The most used command.
    *   `INSERT INTO`: Adds new rows to a table.
    *   `UPDATE`: Modifies existing rows.
    *   `DELETE`: Deletes rows from a table.

*   **Data Control Language (DCL):** Manages user access and permissions.
    *   `GRANT`: Gives a user permission to perform specific actions.
    *   `REVOKE`: Removes a user's permissions.

*   **Transaction Control Language (TCL):** Manages transactions.
    *   `COMMIT`: Saves all the work done in a transaction.
    *   `ROLLBACK`: Undoes all work done since the last `COMMIT`.
    *   `SAVEPOINT`: Sets a point within a transaction to which you can later roll back.

---

#### **Part 6: Transactions and the ACID Properties**

A **transaction** is a sequence of one or more database operations that are executed as a single logical unit of work. Relational databases guarantee the reliability of transactions through the **ACID** properties.

*   **Atomicity:** "All or nothing." A transaction is an indivisible unit. Either all of its operations are successfully completed, or none of them are. If any part fails, the entire transaction is rolled back.
*   **Consistency:** A transaction brings the database from one valid state to another. It preserves all database rules and constraints (like primary keys and foreign keys).
*   **Isolation:** The results of a transaction are invisible to other concurrent transactions until it is complete (committed). This prevents "dirty reads" where one transaction reads uncommitted data from another.
*   **Durability:** Once a transaction has been committed, its changes are permanent and will survive any subsequent system failure (e.g., power outage, crash).

---

#### **Part 7: Advantages and Disadvantages of the Relational Model**

**Advantages:**

*   **Data Integrity and Consistency:** Enforced through keys, constraints, and ACID properties.
*   **Reduced Redundancy:** Normalization minimizes duplicated data.
*   **Standardization:** SQL is a powerful, well-defined, and universally accepted standard.
*   **Flexibility:** Complex queries can be written to retrieve data from multiple tables in various ways.
*   **Security:** DCL provides granular control over user access.

**Disadvantages:**

*   **Schema Rigidity:** The schema is predefined and can be difficult and costly to change once the database is populated with data.
*   **Scalability Challenges:** Scaling a relational database typically involves **vertical scaling** (upgrading to a more powerful server), which can be expensive. **Horizontal scaling** (distributing the load across multiple servers) is more complex than with NoSQL databases.
*   **Object-Relational Impedance Mismatch:** The tabular, relational structure does not map cleanly to the object-oriented programming models used in many modern applications.
*   **Complexity:** Can be overly complex for simple datasets or unstructured data.

---

#### **Part 8: Common RDBMS Examples**

*   **MySQL:** The world's most popular open-source RDBMS, widely used for web applications (part of the LAMP stack).
*   **PostgreSQL:** An advanced, open-source RDBMS known for its feature richness, extensibility, and standards compliance.
*   **Microsoft SQL Server:** A powerful, proprietary RDBMS from Microsoft, widely used in enterprise environments.
*   **Oracle Database:** A high-performance, proprietary RDBMS from Oracle, dominant in the large-scale enterprise market.
*   **SQLite:** A serverless, self-contained, transactional SQL database engine. It is file-based and commonly embedded in mobile apps and small applications.