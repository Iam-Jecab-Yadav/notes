

**1.  Introduction to Databases** [[Database Overview]]

*   **Database:** An organized collection of structured information, or data, typically stored electronically in a computer system.
*   **DBMS (Database Management System):** Software used to create, manage, and access databases (e.g., MySQL, PostgreSQL, SQL Server, Oracle).
*   **RDBMS (Relational Database Management System):** A DBMS based on the relational model. Data is organized into tables (relations) which consist of rows (tuples) and columns (attributes). Relationships between tables are established using keys.
*   **MySQL:**
    *   An open-source RDBMS.
    *   Widely popular, especially for web applications (often part of the LAMP/LEMP stack).
    *   Known for its speed, reliability, and ease of use.
    *   Supports various storage engines, with InnoDB being the default (ACID compliant).
    *   Cross-platform (runs on Linux, Windows, macOS, etc.).
    *   Owned by Oracle Corporation.

**2. Installation & Setup (Brief Overview)**

*   **Official Downloads:** Get MySQL Community Server from `dev.mysql.com`.
*   **Installation:** Varies by OS. Installers usually guide you through setting a root password and configuring basic settings.
*   **Key Components:**
    *   **MySQL Server (`mysqld`):** The core database server daemon.
    *   **MySQL Client (`mysql`):** A command-line tool to connect to the server and execute SQL.
    *   **Configuration File:** `my.cnf` (Linux/macOS) or `my.ini` (Windows) controls server behavior.
*   **Starting/Stopping Server:**
    *   Linux (systemd): `sudo systemctl start mysqld`, `sudo systemctl stop mysqld`
    *   Windows: Via Services.msc or `net start mysql`, `net stop mysql` (service name might vary).
*   **Connecting:** `mysql -u username -p` (will prompt for password). For root: `mysql -u root -p`.

**3. Core Database Concepts**

*   **Database (Schema):** A container for tables and other database objects. In MySQL, `CREATE DATABASE` and `CREATE SCHEMA` are synonyms.
*   **Table:** A collection of related data entries organized in rows and columns.
    *   **Columns (Fields/Attributes):** Define the type of data a table can hold (e.g., `UserID`, `FirstName`, `BirthDate`). Each column has a specific data type.
    *   **Rows (Records/Tuples):** Represent individual entries in a table (e.g., a specific user's information).
*   **Primary Key (PK):**
    *   A column (or set of columns) whose values uniquely identify each row in a table.
    *   Cannot contain `NULL` values.
    *   A table can have only one primary key.
    *   Often an `INT` or `BIGINT` with `AUTO_INCREMENT`.
    *   Example: `UserID` in a `Users` table.
*   **Foreign Key (FK):**
    *   A column (or set of columns) in one table that refers to the Primary Key in another table.
    *   Establishes a link (relationship) between two tables.
    *   Enforces referential integrity (ensures that a value in the FK column matches an existing value in the referenced PK column, or is `NULL` if allowed).
    *   Example: `UserID` in an `Orders` table referencing the `UserID` in the `Users` table.
*   **Constraints:** Rules enforced on data columns in a table.
    *   `NOT NULL`: Ensures a column cannot have a `NULL` value.
    *   `UNIQUE`: Ensures all values in a column (or set of columns) are distinct.
    *   `PRIMARY KEY`: A combination of `NOT NULL` and `UNIQUE`.
    *   `FOREIGN KEY`: Enforces referential integrity.
    *   `CHECK`: Ensures values in a column satisfy a specific condition (more broadly supported in newer MySQL versions).
    *   `DEFAULT`: Sets a default value for a column if no value is specified during insertion.
*   **`AUTO_INCREMENT`:** Attribute for numeric columns (usually PKs) that automatically generates a new sequential number when a new row is inserted.

**4. MySQL Data Types**

*   **Numeric Types:**
    *   `TINYINT`: -128 to 127 (signed), 0 to 255 (unsigned).
    *   `SMALLINT`: -32768 to 32767 (signed), 0 to 65535 (unsigned).
    *   `MEDIUMINT`: -8388608 to 8388607 (signed), 0 to 16777215 (unsigned).
    *   `INT` or `INTEGER`: -2147483648 to 2147483647 (signed), 0 to 4294967295 (unsigned).
    *   `BIGINT`: Very large integer.
    *   `DECIMAL(M,D)` or `NUMERIC(M,D)`: Fixed-point number. `M` is total digits, `D` is digits after decimal. Good for currency.
    *   `FLOAT(M,D)`: Single-precision floating-point number. Imprecise.
    *   `DOUBLE(M,D)` or `REAL`: Double-precision floating-point number. Imprecise.
    *   `BIT(M)`: Stores M bit values (1 to 64).
    *   `BOOL` or `BOOLEAN`: Synonyms for `TINYINT(1)`. 0 is false, non-zero is true.

*   **String Types:**
    *   `CHAR(M)`: Fixed-length string (1 to 255 characters). Padded with spaces if shorter.
    *   `VARCHAR(M)`: Variable-length string (1 to 65,535 characters). Stores actual length + 1 or 2 bytes for length.
    *   `TINYTEXT`: Max 255 characters.
    *   `TEXT`: Max 65,535 characters.
    *   `MEDIUMTEXT`: Max 16,777,215 characters.
    *   `LONGTEXT`: Max 4,294,967,295 characters.
    *   `BINARY(M)`: Fixed-length binary string (like `CHAR` but stores binary byte strings).
    *   `VARBINARY(M)`: Variable-length binary string (like `VARCHAR`).
    *   `TINYBLOB`, `BLOB`, `MEDIUMBLOB`, `LONGBLOB`: For binary large objects (images, files).
    *   `ENUM('val1', 'val2', ...)`: A string object that can have only one value, chosen from a list of allowed values.
    *   `SET('val1', 'val2', ...)`: A string object that can have zero or more values, each chosen from a list of allowed values.

*   **Date and Time Types:**
    *   `DATE`: 'YYYY-MM-DD' format. Range '1000-01-01' to '9999-12-31'.
    *   `TIME`: 'HH:MM:SS' format. Range '-838:59:59' to '838:59:59'.
    *   `DATETIME(fsp)`: 'YYYY-MM-DD HH:MM:SS' format. Range '1000-01-01 00:00:00' to '9999-12-31 23:59:59'. `fsp` is fractional seconds precision (0-6).
    *   `TIMESTAMP(fsp)`: 'YYYY-MM-DD HH:MM:SS' format. Range '1970-01-01 00:00:01' UTC to '2038-01-19 03:14:07' UTC. Stores as UTC, converts to/from session time zone. Can auto-update on row modification.
    *   `YEAR`: YYYY format. Range 1901 to 2155, or 0000.

*   **Spatial Data Types:** For geographic data (e.g., `GEOMETRY`, `POINT`, `LINESTRING`, `POLYGON`).
*   **JSON Data Type:** (MySQL 5.7.8+) Stores JSON documents. Provides functions for manipulation and searching.

**5. SQL (Structured Query Language) Basics**

SQL commands are categorized:

*   **DDL (Data Definition Language):** Defines or modifies database structure.
    *   `SHOW DATABASES;`
        *   Lists all databases on the server.
    *   `CREATE DATABASE database_name;`
        *   Creates a new database.
        *   `CREATE DATABASE IF NOT EXISTS database_name;` (avoids error if it exists)
    *   `USE database_name;`
        *   Selects the default database for subsequent commands.
    *   `DROP DATABASE database_name;`
        *   Deletes an entire database and all its objects. **Use with extreme caution!**
        *   `DROP DATABASE IF EXISTS database_name;`
    *   `SHOW TABLES;`
        *   Lists tables in the current (selected) database.
    *   `CREATE TABLE table_name (
          column1_name data_type [constraints],
          column2_name data_type [constraints],
          ...,
          [PRIMARY KEY (column_name)],
          [FOREIGN KEY (column_name) REFERENCES other_table(other_column_name)],
          [CONSTRAINT constraint_name UNIQUE (column_name)]
        );`
        *   Example:
            ```sql
            CREATE TABLE Employees (
                EmployeeID INT AUTO_INCREMENT PRIMARY KEY,
                FirstName VARCHAR(50) NOT NULL,
                LastName VARCHAR(50) NOT NULL,
                Email VARCHAR(100) UNIQUE,
                HireDate DATE,
                Salary DECIMAL(10, 2) DEFAULT 30000.00,
                DepartmentID INT,
                FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
            );
            ```
    *   `DESCRIBE table_name;` or `DESC table_name;`
        *   Shows the structure of a table (columns, data types, keys, etc.).
    *   `ALTER TABLE table_name action;`
        *   Modifies an existing table.
        *   `ADD COLUMN column_name data_type [constraints];`
            ```sql
            ALTER TABLE Employees ADD COLUMN PhoneNumber VARCHAR(20);
            ```
        *   `DROP COLUMN column_name;`
            ```sql
            ALTER TABLE Employees DROP COLUMN PhoneNumber;
            ```
        *   `MODIFY COLUMN column_name new_data_type [constraints];`
            ```sql
            ALTER TABLE Employees MODIFY COLUMN FirstName VARCHAR(60) NOT NULL;
            ```
        *   `CHANGE COLUMN old_column_name new_column_name new_data_type [constraints];` (renames and modifies)
            ```sql
            ALTER TABLE Employees CHANGE COLUMN HireDate EmploymentDate DATE;
            ```
        *   `ADD CONSTRAINT [constraint_name] PRIMARY KEY (column_name);`
        *   `ADD CONSTRAINT [constraint_name] FOREIGN KEY (column_name) REFERENCES other_table(other_column_name);`
        *   `ADD CONSTRAINT [constraint_name] UNIQUE (column_name);`
        *   `DROP PRIMARY KEY;`
        *   `DROP FOREIGN KEY constraint_name;`
        *   `DROP INDEX index_name;` (for unique constraints too)
        *   `RENAME TO new_table_name;`
            ```sql
            ALTER TABLE Employees RENAME TO Staff;
            ```
    *   `DROP TABLE table_name;`
        *   Deletes a table and its data. **Use with caution!**
        *   `DROP TABLE IF EXISTS table_name;`
    *   `TRUNCATE TABLE table_name;`
        *   Removes all rows from a table very quickly.
        *   Faster than `DELETE` without `WHERE` because it doesn't log individual row deletions (usually).
        *   Resets `AUTO_INCREMENT` counters.
        *   Cannot be rolled back if not part of an explicit transaction with InnoDB.

*   **DML (Data Manipulation Language):** Manipulates data within tables.
    *   `INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);`
        *   Inserts a new row. Column list is optional if values are provided for all columns in order.
        *   Example:
            ```sql
            INSERT INTO Employees (FirstName, LastName, Email, HireDate, Salary, DepartmentID)
            VALUES ('John', 'Doe', 'john.doe@example.com', '2023-01-15', 60000.00, 1);
            ```
        *   Multiple rows:
            ```sql
            INSERT INTO Employees (FirstName, LastName) VALUES
            ('Jane', 'Smith'),
            ('Peter', 'Jones');
            ```
    *   `UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition;`
        *   Modifies existing rows.
        *   **CRITICAL: Always use a `WHERE` clause unless you intend to update all rows.**
        *   Example:
            ```sql
            UPDATE Employees SET Salary = 65000.00 WHERE EmployeeID = 1;
            UPDATE Employees SET Salary = Salary * 1.05; -- Gives everyone a 5% raise
            ```
    *   `DELETE FROM table_name WHERE condition;`
        *   Removes rows from a table.
        *   **CRITICAL: Always use a `WHERE` clause unless you intend to delete all rows.**
        *   Example:
            ```sql
            DELETE FROM Employees WHERE EmployeeID = 1;
            DELETE FROM Employees WHERE HireDate < '2020-01-01';
            ```

*   **DQL (Data Query Language) - The `SELECT` Statement:** Retrieves data.
    *   `SELECT column1, column2, ... FROM table_name;`
        *   Retrieves specific columns.
    *   `SELECT * FROM table_name;`
        *   Retrieves all columns. (Avoid in production for performance and clarity if you don't need all columns).
    *   `SELECT DISTINCT column_name FROM table_name;`
        *   Returns only unique values for the specified column.
    *   `SELECT column_name AS alias_name FROM table_name;`
        *   Assigns an alias to a column (or table) in the result set.
        *   Example: `SELECT FirstName AS FName, LastName AS LName FROM Employees;`
    *   Concatenation:
        *   `SELECT CONCAT(FirstName, ' ', LastName) AS FullName FROM Employees;`
    *   Calculations:
        *   `SELECT Salary, Salary * 0.1 AS Bonus FROM Employees;`

*   **TCL (Transaction Control Language):** Manages transactions. (Primarily for InnoDB storage engine)
    *   `START TRANSACTION;` or `BEGIN;`
        *   Starts a new transaction.
    *   `COMMIT;`
        *   Saves all changes made during the current transaction permanently.
    *   `ROLLBACK;`
        *   Discards all changes made during the current transaction.
    *   `SAVEPOINT savepoint_name;`
        *   Creates a point within a transaction to which you can later roll back.
    *   `ROLLBACK TO SAVEPOINT savepoint_name;`
        *   Rolls back to a specific savepoint.
    *   `SET AUTOCOMMIT = 0;` (Disables autocommit for the current session; requires explicit `COMMIT`)
    *   `SET AUTOCOMMIT = 1;` (Enables autocommit - default behavior)

*   **DCL (Data Control Language):** Manages user access and permissions.
    *   `GRANT privilege_type ON database_name.table_name TO 'user'@'host';`
        *   Gives specific permissions to a user.
        *   Privileges: `ALL PRIVILEGES`, `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `CREATE`, `DROP`, etc.
        *   `database_name.*` means all tables in the database. `*.*` means all databases.
        *   Example: `GRANT SELECT, INSERT ON mydb.Employees TO 'app_user'@'localhost';`
    *   `REVOKE privilege_type ON database_name.table_name FROM 'user'@'host';`
        *   Removes permissions from a user.
        *   Example: `REVOKE INSERT ON mydb.Employees FROM 'app_user'@'localhost';`
    *   `CREATE USER 'username'@'host' IDENTIFIED BY 'password';`
    *   `DROP USER 'username'@'host';`
    *   `SHOW GRANTS FOR 'username'@'host';`

**6. Filtering and Sorting Data**

*   **`WHERE` Clause:** Filters rows based on a condition.
    *   Operators:
        *   `=`: Equal to
        *   `!=` or `<>`: Not equal to
        *   `<`: Less than
        *   `>`: Greater than
        *   `<=`: Less than or equal to
        *   `>=`: Greater than or equal to
        *   `BETWEEN min_val AND max_val`: Value is within a range (inclusive).
        *   `IN (val1, val2, ...)`: Value matches any in the list.
        *   `NOT IN (val1, val2, ...)`
        *   `LIKE 'pattern'`: Pattern matching.
            *   `%`: Matches any sequence of zero or more characters.
            *   `_`: Matches any single character.
            *   Example: `WHERE FirstName LIKE 'J%';` (starts with J)
            *   Example: `WHERE Email LIKE '%@example.com';` (ends with @example.com)
            *   Example: `WHERE LastName LIKE 'J_nes';` (J, any char, nes e.g., Jones)
        *   `IS NULL`: Value is `NULL`.
        *   `IS NOT NULL`: Value is not `NULL`.
    *   Logical Operators:
        *   `AND`: Both conditions must be true.
        *   `OR`: At least one condition must be true.
        *   `NOT`: Negates a condition.
        *   Parentheses `()` can be used to group conditions and control order of evaluation.
    *   Example:
        ```sql
        SELECT FirstName, LastName, Salary
        FROM Employees
        WHERE (Salary > 50000 AND DepartmentID = 2) OR HireDate < '2022-01-01';
        ```

*   **`ORDER BY` Clause:** Sorts the result set.
    *   `ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;`
    *   `ASC`: Ascending order (default).
    *   `DESC`: Descending order.
    *   Can sort by multiple columns.
    *   Example: `SELECT * FROM Employees ORDER BY LastName ASC, FirstName ASC;`
    *   Example: `SELECT * FROM Employees ORDER BY Salary DESC;`

*   **`LIMIT` Clause:** Restricts the number of rows returned.
    *   `LIMIT count;` (Returns the first `count` rows)
    *   `LIMIT offset, count;` (Skips `offset` rows, then returns `count` rows - useful for pagination)
    *   Example: `SELECT * FROM Employees ORDER BY Salary DESC LIMIT 5;` (Top 5 salaries)
    *   Example: `SELECT * FROM Employees LIMIT 10, 5;` (Rows 11-15)

**7. Aggregate Functions**

Perform calculations on a set of values and return a single summary value. Often used with `GROUP BY`.

*   `COUNT(expression)`: Counts rows.
    *   `COUNT(*)`: Counts all rows in the group/table.
    *   `COUNT(column_name)`: Counts non-NULL values in that column.
    *   `COUNT(DISTINCT column_name)`: Counts unique non-NULL values.
*   `SUM(expression)`: Calculates the sum of values. (Works on numeric columns).
*   `AVG(expression)`: Calculates the average of values. (Works on numeric columns).
*   `MIN(expression)`: Finds the minimum value.
*   `MAX(expression)`: Finds the maximum value.
*   `GROUP_CONCAT(expression [ORDER BY ...] [SEPARATOR str])`: Concatenates values from a group into a single string.

Example:
```sql
SELECT
    COUNT(*) AS TotalEmployees,
    AVG(Salary) AS AverageSalary,
    MIN(HireDate) AS EarliestHire,
    MAX(Salary) AS MaxSalary
FROM Employees;
```

**8. Grouping Data**

*   **`GROUP BY` Clause:** Groups rows that have the same values in one or more columns into summary rows.
    *   Used with aggregate functions.
    *   Columns in the `SELECT` list must either be part of the `GROUP BY` clause or be arguments to aggregate functions.
    *   Example:
        ```sql
        SELECT DepartmentID, COUNT(*) AS NumEmployees, AVG(Salary) AS AvgDeptSalary
        FROM Employees
        GROUP BY DepartmentID
        ORDER BY DepartmentID;
        ```

*   **`HAVING` Clause:** Filters groups created by `GROUP BY`.
    *   `WHERE` filters rows *before* grouping.
    *   `HAVING` filters groups *after* grouping.
    *   Can use aggregate functions in the `HAVING` condition.
    *   Example:
        ```sql
        SELECT DepartmentID, COUNT(*) AS NumEmployees, AVG(Salary) AS AvgDeptSalary
        FROM Employees
        GROUP BY DepartmentID
        HAVING COUNT(*) > 3 AND AVG(Salary) > 55000
        ORDER BY AvgDeptSalary DESC;
        ```

**9. Joins (Combining Data from Multiple Tables)**

Used to retrieve data from two or more tables based on related columns.

*   **`INNER JOIN` (or just `JOIN`):**
    *   Returns rows only when there is a match in *both* tables based on the join condition.
    *   Syntax:
        ```sql
        SELECT t1.column_name, t2.column_name
        FROM table1 t1
        INNER JOIN table2 t2 ON t1.common_column = t2.common_column;
        ```
    *   Example:
        ```sql
        SELECT E.FirstName, E.LastName, D.DepartmentName
        FROM Employees E
        INNER JOIN Departments D ON E.DepartmentID = D.DepartmentID;
        ```

*   **`LEFT JOIN` (or `LEFT OUTER JOIN`):**
    *   Returns all rows from the *left* table (table1) and the matched rows from the *right* table (table2).
    *   If there's no match in the right table, `NULL` values are returned for columns from the right table.
    *   Syntax:
        ```sql
        SELECT t1.column_name, t2.column_name
        FROM table1 t1
        LEFT JOIN table2 t2 ON t1.common_column = t2.common_column;
        ```
    *   Example: (Show all employees, and their department if they have one)
        ```sql
        SELECT E.FirstName, E.LastName, D.DepartmentName
        FROM Employees E
        LEFT JOIN Departments D ON E.DepartmentID = D.DepartmentID;
        ```

*   **`RIGHT JOIN` (or `RIGHT OUTER JOIN`):**
    *   Returns all rows from the *right* table (table2) and the matched rows from the *left* table (table1).
    *   If there's no match in the left table, `NULL` values are returned for columns from the left table.
    *   Often, a `RIGHT JOIN` can be rewritten as a `LEFT JOIN` by swapping table order, which is usually preferred for readability.
    *   Syntax:
        ```sql
        SELECT t1.column_name, t2.column_name
        FROM table1 t1
        RIGHT JOIN table2 t2 ON t1.common_column = t2.common_column;
        ```
    *   Example: (Show all departments, and their employees if any)
        ```sql
        SELECT E.FirstName, E.LastName, D.DepartmentName
        FROM Employees E
        RIGHT JOIN Departments D ON E.DepartmentID = D.DepartmentID;
        ```

*   **`FULL OUTER JOIN` (or `FULL JOIN`):**
    *   Returns all rows from *both* tables.
    *   If there's a match, columns from both tables are populated.
    *   If there's no match for a row in one table, `NULL`s are returned for columns from the other table.
    *   **MySQL does not directly support `FULL OUTER JOIN`**. It can be emulated using `LEFT JOIN UNION RIGHT JOIN`:
        ```sql
        SELECT t1.col, t2.col FROM table1 t1 LEFT JOIN table2 t2 ON t1.id = t2.id
        UNION ALL -- Use UNION to remove duplicates from the join keys if needed
        SELECT t1.col, t2.col FROM table1 t1 RIGHT JOIN table2 t2 ON t1.id = t2.id
        WHERE t1.id IS NULL; -- To avoid duplicating INNER JOIN rows
        ```
        A more common emulation:
        ```sql
        SELECT * FROM table1 A
        LEFT JOIN table2 B ON A.key = B.key
        UNION
        SELECT * FROM table1 A
        RIGHT JOIN table2 B ON A.key = B.key;
        ```

*   **`CROSS JOIN` (or Cartesian Product):**
    *   Returns every possible combination of rows from both tables.
    *   Generally used sparingly as it can produce very large result sets.
    *   Syntax: `SELECT * FROM table1 CROSS JOIN table2;` or `SELECT * FROM table1, table2;` (implicit).

*   **`SELF JOIN`:**
    *   Joins a table to itself. Requires using table aliases.
    *   Useful for querying hierarchical data or comparing rows within the same table.
    *   Example: (Find employees and their managers, assuming `ManagerID` in `Employees` table refers to another `EmployeeID`)
        ```sql
        SELECT
            e.FirstName AS EmployeeName,
            m.FirstName AS ManagerName
        FROM Employees e
        INNER JOIN Employees m ON e.ManagerID = m.EmployeeID;
        ```

*   **`USING` Clause:** A shorthand for `ON` when the join columns have the same name in both tables.
    *   Example: `... FROM Employees E JOIN Departments D USING (DepartmentID);`

*   **`NATURAL JOIN`:** Joins tables based on all columns that have the same name in both tables. **Generally discouraged** as it can lead to unexpected results if table structures change.

**10. Subqueries (Nested Queries)**

A query embedded within another SQL query.

*   **Types:**
    *   **Scalar Subquery:** Returns a single value (one row, one column). Can be used where a single value is expected.
        ```sql
        SELECT FirstName, LastName, Salary
        FROM Employees
        WHERE Salary > (SELECT AVG(Salary) FROM Employees); -- Scalar subquery in WHERE
        ```
    *   **Column Subquery:** Returns a single column of one or more rows. Often used with `IN`, `ANY`, `ALL`.
        ```sql
        SELECT * FROM Products
        WHERE ProductID IN (SELECT ProductID FROM OrderDetails WHERE Quantity > 100);
        ```
    *   **Row Subquery:** Returns a single row of one or more columns.
    *   **Table Subquery (Derived Table):** Returns a virtual table. Must be aliased and used in the `FROM` clause.
        ```sql
        SELECT d.DepartmentName, dep_summary.AvgSalary
        FROM Departments d
        JOIN (
            SELECT DepartmentID, AVG(Salary) AS AvgSalary
            FROM Employees
            GROUP BY DepartmentID
        ) AS dep_summary ON d.DepartmentID = dep_summary.DepartmentID;
        ```

*   **Correlated Subquery:**
    *   A subquery that references columns from the outer query.
    *   The subquery is re-evaluated for each row processed by the outer query. Can be less efficient.
    *   Example: (Find employees whose salary is higher than the average salary in their own department)
        ```sql
        SELECT e1.FirstName, e1.LastName, e1.Salary, e1.DepartmentID
        FROM Employees e1
        WHERE e1.Salary > (
            SELECT AVG(e2.Salary)
            FROM Employees e2
            WHERE e2.DepartmentID = e1.DepartmentID -- Correlation
        );
        ```

*   **`EXISTS` and `NOT EXISTS` Operators:**
    *   Used with subqueries to check if the subquery returns any rows.
    *   `EXISTS` is true if the subquery returns one or more rows.
    *   Often more efficient than `IN` for large subquery results.
    *   Example: (Find departments that have at least one employee)
        ```sql
        SELECT DepartmentName
        FROM Departments d
        WHERE EXISTS (
            SELECT 1 FROM Employees e WHERE e.DepartmentID = d.DepartmentID
        );
        ```

**11. Common Table Expressions (CTEs)**

*   A temporary, named result set that you can reference within a single `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement.
*   Defined using the `WITH` clause.
*   Improves readability and maintainability of complex queries.
*   Can be recursive (for hierarchical data).
*   Syntax:
    ```sql
    WITH CteName AS (
        SELECT ... -- CTE query definition
    )
    SELECT ... FROM CteName ...; -- Main query using the CTE
    ```
*   Example (similar to derived table example):
    ```sql
    WITH DepartmentAvgSalary AS (
        SELECT DepartmentID, AVG(Salary) AS AvgSalary
        FROM Employees
        GROUP BY DepartmentID
    )
    SELECT d.DepartmentName, das.AvgSalary
    FROM Departments d
    JOIN DepartmentAvgSalary das ON d.DepartmentID = das.DepartmentID;
    ```
*   **Recursive CTE Example (Employee Hierarchy):**
    ```sql
    WITH RECURSIVE EmployeeHierarchy AS (
        -- Anchor member: selects the top-level employees (e.g., CEO)
        SELECT EmployeeID, FirstName, ManagerID, 0 AS Level
        FROM Employees
        WHERE ManagerID IS NULL

        UNION ALL

        -- Recursive member: joins back to EmployeeHierarchy
        SELECT e.EmployeeID, e.FirstName, e.ManagerID, eh.Level + 1
        FROM Employees e
        INNER JOIN EmployeeHierarchy eh ON e.ManagerID = eh.EmployeeID
    )
    SELECT * FROM EmployeeHierarchy ORDER BY Level, EmployeeID;
    ```

**12. `UNION` and `UNION ALL`**

Combines the result sets of two or more `SELECT` statements.

*   **`UNION`:**
    *   Combines results and removes duplicate rows.
    *   The `SELECT` statements must have the same number of columns.
    *   The columns must have similar data types.
    *   Column names in the final result are taken from the first `SELECT` statement.
*   **`UNION ALL`:**
    *   Combines results and includes all duplicate rows.
    *   Generally faster than `UNION` because it doesn't need to sort and check for duplicates.
*   Example:
    ```sql
    SELECT CustomerID, CompanyName, City, 'Customer' AS Type FROM Customers
    UNION ALL
    SELECT SupplierID, CompanyName, City, 'Supplier' AS Type FROM Suppliers
    ORDER BY City;
    ```

**13. Views**

*   A virtual table based on the result-set of a stored `SELECT` query.
*   Does not store data itself (unless it's a materialized view, which MySQL doesn't support directly but can be emulated).
*   **Benefits:**
    *   **Simplicity:** Hides complex query logic.
    *   **Security:** Can restrict access to certain columns or rows.
    *   **Consistency:** Provides a consistent data representation even if underlying tables change (as long as view definition remains valid).
*   **Creating a View:**
    ```sql
    CREATE VIEW EmployeeDepartmentView AS
    SELECT E.EmployeeID, E.FirstName, E.LastName, D.DepartmentName, E.Salary
    FROM Employees E
    JOIN Departments D ON E.DepartmentID = D.DepartmentID
    WHERE E.Salary > 50000;
    ```
*   **Querying a View:**
    ```sql
    SELECT * FROM EmployeeDepartmentView WHERE DepartmentName = 'Sales';
    ```
*   **Modifying a View:** `CREATE OR REPLACE VIEW ...` or `ALTER VIEW ...`
*   **Dropping a View:** `DROP VIEW view_name;`
*   **Updatable Views:** Some simple views can be updated (i.e., `INSERT`, `UPDATE`, `DELETE` through the view), but complex views (with joins, aggregates, `DISTINCT`, etc.) are generally not updatable.

**14. Indexes**

*   Special lookup tables that the database search engine can use to speed up data retrieval operations.
*   Analogous to an index in a book.
*   When you create an index on a column (or columns), MySQL creates a data structure (commonly a B-Tree) that stores the column values and pointers to the actual table rows.
*   **Primary Keys are automatically indexed.**
*   **Unique Constraints are automatically indexed.**
*   **Benefits:**
    *   Faster `SELECT` queries (especially with `WHERE`, `JOIN ON`, `ORDER BY` clauses on indexed columns).
    *   Enforce uniqueness (for unique indexes).
*   **Drawbacks:**
    *   Slower `INSERT`, `UPDATE`, `DELETE` operations because indexes also need to be updated.
    *   Consume disk space.
*   **When to Create Indexes:**
    *   Columns frequently used in `WHERE` clauses.
    *   Columns used in `JOIN` conditions (foreign keys are good candidates, though InnoDB often creates them automatically).
    *   Columns frequently used in `ORDER BY` or `GROUP BY` clauses.
    *   Avoid indexing small tables or columns with very few distinct values (low cardinality).
*   **Creating an Index:**
    ```sql
    CREATE INDEX idx_lastname ON Employees (LastName);
    CREATE UNIQUE INDEX idx_email ON Employees (Email); -- If not already unique constraint
    CREATE INDEX idx_dept_salary ON Employees (DepartmentID, Salary); -- Composite index
    ```
*   **Dropping an Index:**
    ```sql
    DROP INDEX idx_lastname ON Employees;
    ALTER TABLE Employees DROP INDEX idx_email;
    ```
*   **Showing Indexes:**
    ```sql
    SHOW INDEXES FROM Employees;
    ```
*   **Types of Indexes (MySQL):**
    *   `PRIMARY KEY`: Unique, no NULLs.
    *   `UNIQUE`: All values unique, can have one NULL (multiple NULLs allowed in some configurations/versions for non-PK unique indexes).
    *   `INDEX` (or `KEY`): Non-unique index.
    *   `FULLTEXT`: For full-text searching on `CHAR`, `VARCHAR`, `TEXT` columns (uses specific algorithms).
    *   `SPATIAL`: For spatial data types.

**15. Transactions and ACID Properties**

(Primarily applicable to the InnoDB storage engine, which is the default in MySQL)

*   **Transaction:** A sequence of one or more SQL operations treated as a single, atomic unit of work. Either all operations succeed (`COMMIT`), or none of them do (`ROLLBACK`).
*   **ACID Properties:** Guarantee data integrity and reliability.
    *   **Atomicity:** A transaction is an "all or nothing" affair. If any part fails, the entire transaction is rolled back.
    *   **Consistency:** A transaction brings the database from one valid state to another. All defined rules (constraints, triggers) must be maintained.
    *   **Isolation:** Concurrent transactions should not interfere with each other. Each transaction should appear to execute in isolation. MySQL provides different isolation levels (e.g., `READ COMMITTED`, `REPEATABLE READ` (default), `SERIALIZABLE`).
    *   **Durability:** Once a transaction is committed, its changes are permanent and will survive system failures (e.g., power outage, crash). This is usually achieved through write-ahead logging.

*   **TCL Commands (recap):** `START TRANSACTION`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`.

**16. Stored Procedures**

*   A set of SQL statements stored in the database and executed as a single unit.
*   Can accept input parameters (`IN`), return output parameters (`OUT`), and have in/out parameters (`INOUT`).
*   Do not directly return a value like functions, but can return result sets.
*   **Benefits:**
    *   **Reusability:** Write once, call many times.
    *   **Performance:** Pre-compiled (to some extent), reduces network traffic.
    *   **Security:** Can grant `EXECUTE` permission on a procedure without granting direct table access.
    *   **Encapsulation:** Hides complex logic.
*   **`DELIMITER`:** The `mysql` client uses `;` to end statements. Since procedures contain `;` internally, you need to change the delimiter temporarily.
*   **Syntax:**
    ```sql
    DELIMITER //

    CREATE PROCEDURE GetEmployeeByDept (IN deptID INT)
    BEGIN
        SELECT EmployeeID, FirstName, LastName, Salary
        FROM Employees
        WHERE DepartmentID = deptID;
    END //

    DELIMITER ;
    ```
*   **Calling a Procedure:**
    ```sql
    CALL GetEmployeeByDept(1);
    ```
*   **Procedure with OUT parameter:**
    ```sql
    DELIMITER //
    CREATE PROCEDURE CountEmployeesInDept (IN deptID INT, OUT empCount INT)
    BEGIN
        SELECT COUNT(*) INTO empCount
        FROM Employees
        WHERE DepartmentID = deptID;
    END //
    DELIMITER ;

    CALL CountEmployeesInDept(1, @employee_count);
    SELECT @employee_count;
    ```
*   **Dropping a Procedure:** `DROP PROCEDURE IF EXISTS procedure_name;`
*   **Showing Procedures:** `SHOW PROCEDURE STATUS WHERE Db = 'your_database_name';`
*   **Showing Procedure Code:** `SHOW CREATE PROCEDURE procedure_name;`

**17. Stored Functions**

*   Similar to stored procedures, but **must return a single value**.
*   Can be used in SQL expressions where a value is expected (e.g., in `SELECT` list, `WHERE` clause).
*   Cannot produce result sets directly (though they can query tables).
*   **Benefits:** Similar to procedures, especially for encapsulating calculations.
*   **Syntax:**
    ```sql
    DELIMITER //

    CREATE FUNCTION GetEmployeeFullName (empID INT)
    RETURNS VARCHAR(100)
    DETERMINISTIC -- Or READS SQL DATA, MODIFIES SQL DATA
    BEGIN
        DECLARE fullName VARCHAR(100);
        SELECT CONCAT(FirstName, ' ', LastName) INTO fullName
        FROM Employees
        WHERE EmployeeID = empID;
        RETURN fullName;
    END //

    DELIMITER ;
    ```
    *   `DETERMINISTIC`: Means the function always returns the same result for the same input parameters.
    *   `READS SQL DATA`: Means the function reads data but doesn't modify it.
    *   `MODIFIES SQL DATA`: Means the function modifies data (less common for functions).
*   **Using a Function:**
    ```sql
    SELECT GetEmployeeFullName(1) AS FullName;
    SELECT EmployeeID, Salary FROM Employees WHERE Salary > GetAverageSalaryForDept(DepartmentID); -- Hypothetical
    ```
*   **Dropping a Function:** `DROP FUNCTION IF EXISTS function_name;`
*   **Showing Functions:** `SHOW FUNCTION STATUS WHERE Db = 'your_database_name';`
*   **Showing Function Code:** `SHOW CREATE FUNCTION function_name;`

**18. Triggers**

*   A stored program automatically executed (fired) by MySQL in response to certain events on a particular table.
*   Events: `INSERT`, `UPDATE`, `DELETE`.
*   Timing: `BEFORE` or `AFTER` the event.
*   For each row affected by the event.
*   **`NEW` and `OLD` Keywords:**
    *   `NEW.column_name`: Refers to the value of a column in the row to be inserted (for `INSERT` triggers) or the new value after an update (for `UPDATE` triggers).
    *   `OLD.column_name`: Refers to the value of a column in the row being deleted (for `DELETE` triggers) or the old value before an update (for `UPDATE` triggers).
*   **Use Cases:**
    *   Auditing changes (logging to an audit table).
    *   Maintaining data integrity or derived data.
    *   Enforcing complex business rules.
*   **Syntax:**
    ```sql
    DELIMITER //

    CREATE TRIGGER AfterEmployeeInsert
    AFTER INSERT ON Employees
    FOR EACH ROW
    BEGIN
        -- Example: Log the new employee insertion into an audit table
        INSERT INTO AuditLog (TableName, Action, RecordID, LogTime)
        VALUES ('Employees', 'INSERT', NEW.EmployeeID, NOW());
    END //

    DELIMITER ;
    ```
    ```sql
    DELIMITER //
    CREATE TRIGGER BeforeEmployeeUpdate
    BEFORE UPDATE ON Employees
    FOR EACH ROW
    BEGIN
        -- Example: Prevent salary decrease
        IF NEW.Salary < OLD.Salary THEN
            SIGNAL SQLSTATE '45000' -- Custom error state
            SET MESSAGE_TEXT = 'Salary cannot be decreased.';
        END IF;
    END //
    DELIMITER ;
    ```
*   **Dropping a Trigger:** `DROP TRIGGER IF EXISTS trigger_name;`
*   **Showing Triggers:** `SHOW TRIGGERS [FROM database_name] [LIKE 'pattern'];`

**19. User Management and Privileges (Recap & Detail)**

*   **Creating Users:**
    ```sql
    CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'strong_password';
    CREATE USER 'remoteuser'@'%' IDENTIFIED BY 'another_password'; -- '%' allows connection from any host
    CREATE USER 'specific_ip_user'@'192.168.1.100' IDENTIFIED BY 'securepass';
    ```
*   **Granting Privileges:**
    *   Syntax: `GRANT privilege_list ON object_type TO user_specification;`
    *   `privilege_list`: `ALL PRIVILEGES`, `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `CREATE`, `DROP`, `ALTER`, `INDEX`, `EXECUTE` (for procedures/functions), `REFERENCES` (for FKs), etc.
    *   `object_type`:
        *   `*.*`: Global (all databases, all tables).
        *   `database_name.*`: All tables/objects in a specific database.
        *   `database_name.table_name`: A specific table.
        *   `PROCEDURE database_name.procedure_name`: A specific procedure.
        *   `FUNCTION database_name.function_name`: A specific function.
    *   Examples:
        ```sql
        GRANT SELECT, INSERT, UPDATE ON myapp_db.Customers TO 'app_user'@'localhost';
        GRANT EXECUTE ON PROCEDURE myapp_db.ProcessOrder TO 'app_user'@'localhost';
        GRANT ALL PRIVILEGES ON test_db.* TO 'developer'@'localhost' WITH GRANT OPTION;
        -- WITH GRANT OPTION allows the user to grant their own privileges to others. Use carefully.
        ```
*   **Revoking Privileges:**
    ```sql
    REVOKE INSERT, UPDATE ON myapp_db.Customers FROM 'app_user'@'localhost';
    REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'developer'@'localhost'; -- Must revoke GRANT OPTION separately
    ```
*   **Viewing Privileges:**
    ```sql
    SHOW GRANTS FOR 'app_user'@'localhost';
    ```
*   **Changing Passwords:**
    ```sql
    ALTER USER 'username'@'host' IDENTIFIED BY 'new_strong_password';
    -- For older MySQL versions, you might use:
    -- SET PASSWORD FOR 'username'@'host' = PASSWORD('new_strong_password'); (PASSWORD() function is deprecated)
    ```
*   **Renaming Users:**
    ```sql
    RENAME USER 'olduser'@'host' TO 'newuser'@'newhost';
    ```
*   **Dropping Users:**
    ```sql
    DROP USER 'username'@'host';
    ```
*   **`FLUSH PRIVILEGES;`**: Reloads the grant tables. Usually needed only if you modify grant tables directly (e.g., via `INSERT`/`UPDATE` on `mysql.user` table, which is generally not recommended). `GRANT`, `REVOKE`, `CREATE USER` typically don't require it.

**20. Backup and Restore**

*   **Logical Backups (using `mysqldump`):**
    *   Creates SQL statements that can recreate the database objects and/or data.
    *   Platform-independent.
    *   Slower for very large databases compared to physical backups.
    *   **Backup a single database:**
        ```bash
        mysqldump -u username -p database_name > backup_file.sql
        ```
    *   **Backup specific tables:**
        ```bash
        mysqldump -u username -p database_name table1 table2 > backup_file.sql
        ```
    *   **Backup all databases:**
        ```bash
        mysqldump -u username -p --all-databases > all_databases_backup.sql
        ```
    *   **Backup structure only (no data):**
        ```bash
        mysqldump -u username -p --no-data database_name > structure_backup.sql
        ```
    *   **Backup data only (no structure):**
        ```bash
        mysqldump -u username -p --no-create-info database_name > data_backup.sql
        ```
    *   **Important options for InnoDB (consistent backups):**
        *   `--single-transaction`: Issues a `START TRANSACTION` before dumping, ensuring a consistent snapshot for InnoDB tables without locking them for long.
        *   `--routines`: Include stored procedures and functions.
        *   `--triggers`: Include triggers.
        *   `--events`: Include scheduled events.
        ```bash
        mysqldump -u root -p --single-transaction --routines --triggers --events my_database > my_database_full_backup.sql
        ```
*   **Restoring from a `mysqldump` file:**
    *   Using the `mysql` client:
        ```bash
        mysql -u username -p database_name < backup_file.sql
        ```
        (The database `database_name` should typically exist, or the dump file should contain `CREATE DATABASE` and `USE` statements).
*   **Physical Backups:** (e.g., MySQL Enterprise Backup, Percona XtraBackup)
    *   Copy the actual data files.
    *   Faster for very large databases.
    *   More complex, often requires the server to be offline or uses specialized tools for hot backups.
*   **Binary Logging (for Point-in-Time Recovery - PITR):**
    *   MySQL server can log all changes that modify data (inserts, updates, deletes) to binary log files.
    *   Used for replication and PITR.
    *   To perform PITR, you restore the last full backup and then apply binary logs up to the desired point.
    *   Enable in `my.cnf`/`my.ini`: `log_bin = /path/to/mysql-bin.log` (or just `log_bin = mysql-bin`).

**21. Common MySQL Tools**

*   **`mysql` (Command-Line Client):** The standard CLI for interacting with MySQL.
*   **MySQL Workbench:** Official GUI tool for database design, development, administration.
*   **phpMyAdmin:** Popular web-based administration tool, often found in web hosting environments.
*   **DBeaver:** Free, multi-platform universal database tool.
*   **DataGrip (JetBrains):** Commercial, powerful IDE for databases.
*   **HeidiSQL (Windows):** Free, lightweight GUI client.
*   **Sequel Pro / Sequel Ace (macOS):** Popular macOS native clients.

**22. Storage Engines (Briefly: InnoDB vs. MyISAM)**

MySQL supports multiple storage engines, which handle how data is stored, indexed, and managed.

*   **InnoDB:**
    *   **Default storage engine** in modern MySQL.
    *   **ACID compliant** (supports transactions, commit, rollback, crash recovery).
    *   **Row-level locking:** Better concurrency for high write loads.
    *   **Foreign key constraints:** Enforces referential integrity.
    *   Generally preferred for most applications due to its reliability and feature set.
*   **MyISAM:**
    *   Older default engine.
    *   **No transaction support.**
    *   **Table-level locking:** Can be a bottleneck for concurrent writes.
    *   Faster for certain read-heavy workloads, especially full-text searches (though InnoDB also supports full-text).
    *   Less crash-resistant.
    *   Generally not recommended for new applications requiring data integrity and transactions.
*   **Other Engines:** `MEMORY` (in-memory tables, very fast, data lost on restart), `CSV`, `ARCHIVE`, etc.
*   **Checking/Setting Engine for a Table:**
    ```sql
    SHOW CREATE TABLE table_name; -- Shows current engine
    ALTER TABLE table_name ENGINE = InnoDB;
    ```

**23. Best Practices and Tips**

*   **Normalization:** Design your database schema to reduce data redundancy and improve data integrity (e.g., 1NF, 2NF, 3NF).
*   **Choose Appropriate Data Types:** Use the smallest data type that can reliably hold your data to save space and improve performance.
*   **Use `NOT NULL` where applicable:** Enforces data presence.
*   **Index Wisely:** Index columns used in `WHERE`, `JOIN`, `ORDER BY`, but don't over-index.
*   **Write Clear and Readable SQL:** Use aliases, comments, and consistent formatting.
*   **Avoid `SELECT *` in production code:** Only select the columns you need.
*   **Be Cautious with `UPDATE` and `DELETE` without `WHERE`:** Double-check before running.
*   **Use Transactions for Atomic Operations:** Especially when multiple DML statements must succeed or fail together.
*   **Secure Your Server:**
    *   Use strong passwords for `root` and other users.
    *   Remove anonymous users.
    *   Limit user privileges to the minimum required (`Principle of Least Privilege`).
    *   Consider network security (firewalls, bind-address).
*   **Regular Backups:** Essential for disaster recovery. Test your restore process.
*   **Monitor Performance:** Use tools like `EXPLAIN` to analyze query performance, and monitor server metrics.
*   **Keep MySQL Updated:** Apply security patches and bug fixes.
*   **Use Prepared Statements/Parameterized Queries in Application Code:** Prevents SQL injection vulnerabilities.
*   **Understand Character Sets and Collations:** Crucial for multi-lingual data (e.g., `utf8mb4` for full Unicode support).

---

