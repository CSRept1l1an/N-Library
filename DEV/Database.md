#Dev 
### 1. **Database Concepts**
- **Database**: A structured collection of data.
- **DBMS (Database Management System)**: Software for creating and managing databases (e.g., MySQL, PostgreSQL, Oracle).
- **[[SQL]] (Structured Query Language)**: Standard language for managing and manipulating databases.

### 2. **Data Models**
- **Relational Model**: Uses tables (relations) to represent data and relationships.
- **NoSQL Models**: 
  - Document (e.g., MongoDB)
  - Key-Value (e.g., Redis)
  - Column Family (e.g., Cassandra)
  - Graph (e.g., Neo4j)

### 3. **Database Normalization**
- **1NF (First Normal Form)**: Ensure each column contains atomic values.
- **2NF (Second Normal Form)**: Meet all 1NF requirements and remove partial dependencies.
- **3NF (Third Normal Form)**: Meet all 2NF requirements and remove transitive dependencies.
- **BCNF (Boyce-Codd Normal Form)**: A stronger version of 3NF.

### 4. **[[SQL]] Basics**
- **Data Definition Language (DDL)**:
  - `CREATE TABLE table_name (...);`
  - `ALTER TABLE table_name ADD column_name datatype;`
  - `DROP TABLE table_name;`
- **Data Manipulation Language (DML)**:
  - `INSERT INTO table_name (columns) VALUES (values);`
  - `UPDATE table_name SET column = value WHERE condition;`
  - `DELETE FROM table_name WHERE condition;`
- **Data Query Language (DQL)**:
  - `SELECT columns FROM table_name WHERE condition;`
- **Data Control Language (DCL)**:
  - `GRANT permission ON object TO user;`
  - `REVOKE permission ON object FROM user;`

### 5. **Advanced [[SQL]]**
- **Joins**:
  - `INNER JOIN`: Selects records with matching values in both tables.
  - `LEFT JOIN (or LEFT OUTER JOIN)`: Selects all records from the left table, and matched records from the right table.
  - `RIGHT JOIN (or RIGHT OUTER JOIN)`: Selects all records from the right table, and matched records from the left table.
  - `FULL JOIN (or FULL OUTER JOIN)`: Selects all records when there is a match in either left or right table.
- **Subqueries**: A query nested inside another query.
- **Indexes**: Improves query performance by reducing the amount of data scanned.
  - `CREATE INDEX index_name ON table_name (column_name);`
- **Views**: A virtual table based on the result set of a SQL query.
  - `CREATE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;`

### 6. **Transactions**
- **ACID Properties**:
  - **Atomicity**: All operations in a transaction are completed; if not, the transaction is aborted.
  - **Consistency**: Ensures that the database properly changes states upon a successfully committed transaction.
  - **Isolation**: Transactions occur independently without interference.
  - **Durability**: Ensures that the results of a completed transaction are permanent.
- **Transaction Control Commands**:
  - `BEGIN TRANSACTION;`
  - `COMMIT;`
  - `ROLLBACK;`

### 7. **NoSQL Databases**
- **Document Stores**: Store data as documents (e.g., JSON, BSON).
  - Example: MongoDB
- **Key-Value Stores**: Data is stored as key-value pairs.
  - Example: Redis
- **Column-Family Stores**: Data is stored in columns rather than rows.
  - Example: Cassandra
- **Graph Databases**: Store data in graph structures with nodes, edges, and properties.
  - Example: Neo4j

### 8. **Database Security**
- **Authentication**: Verify the identity of users.
- **Authorization**: Define what an authenticated user is allowed to do.
- **Encryption**: Protect data at rest and in transit.
- **Backup and Recovery**: Regularly back up data and have a recovery plan in place.

### 9. **Common Database Functions**
- **Aggregate Functions**:
  - `COUNT()`: Returns the number of rows.
  - `SUM()`: Returns the sum of a numeric column.
  - `AVG()`: Returns the average value of a numeric column.
  - `MIN()`: Returns the minimum value.
  - `MAX()`: Returns the maximum value.
- **String Functions**:
  - `CONCAT()`: Concatenate strings.
  - `LENGTH()`: Return the length of a string.
  - `UPPER()`, `LOWER()`: Convert to upper or lower case.
- **Date Functions**:
  - `NOW()`: Returns the current date and time.
  - `DATE_ADD()`, `DATE_SUB()`: Add or subtract dates.
  - `DATEDIFF()`: Returns the difference between two dates.

### 10. **Performance Tuning**
- **Query Optimization**: Writing efficient queries and using proper indexing.
- **Database Design**: Proper schema design, normalization, and choosing the right data types.
- **Caching**: Using in-memory caches to reduce database load.
- **Load Balancing**: Distributing database load across multiple servers.

### 11. **Backup and Recovery**
- **Full Backup**: Complete backup of the entire database.
- **Incremental Backup**: Backup of only the data that has changed since the last backup.
- **Point-in-Time Recovery**: Restoring the database to a specific point in time.

### 12. **Tools and Utilities**
- **Database Management Tools**: phpMyAdmin, pgAdmin, SQL Server Management Studio (SSMS).
- **Backup Tools**: mysqldump, pg_dump, Oracle RMAN.
- **Monitoring Tools**: Nagios, Zabbix, Prometheus.

This cheat sheet can be expanded with examples, diagrams, and more specific details tailored to your needs and the databases you work with.