#Database 
# Database Concepts and Techniques

## 1. Database Fundamentals
### Database
A database is a structured collection of data that can be easily accessed, managed, and updated. Databases store information in a way that supports efficient retrieval and manipulation.

### DBMS (Database Management System)
A DBMS is software that interacts with users, applications, and the database itself to capture and analyze data. Examples include:
- **MySQL**: An open-source relational database management system.
- **PostgreSQL**: An open-source object-relational database system.
- **Oracle**: A multi-model database management system produced by Oracle Corporation.
- [[SQLite]] : A self-contained, serverless, zero-configuration, transactional SQL database engine.
- **MS SQL (Microsoft SQL Server)**: A relational database management system developed by Microsoft.

### [[SQL]] (Structured Query Language)
SQL is a standardized language used to manage and manipulate relational databases. It includes commands for querying data, defining data structures, and controlling access.

## 2. Data Models
### Relational Model
The relational model organizes data into tables (relations) with rows (tuples) and columns (attributes). Each table represents an entity, and relationships between tables are established through foreign keys.

### NoSQL Models
- **Document**: Stores data as documents, often in JSON or BSON format.
	- Example: [[MongoDB]]
	- Use Case: Flexible schema design, hierarchical data storage.
- **Key-Value**: Stores data as key-value pairs, where a key is a unique identifier for a value.
	- Example: Redis
	- Use Case: High-speed data retrieval, caching.
- **Column Family**: Stores data in columns rather than rows, optimized for read and write performance.
	- Example: Cassandra
	- Use Case: Handling large volumes of data across many servers.
- **Graph**: Uses graph structures with nodes, edges, and properties to represent and store data.
	- Example: Neo4j
	- Use Case: Complex relationship queries, social networks.

## 3. Database Normalization
### 1NF (First Normal Form)
- Ensure that each column contains atomic (indivisible) values.
- Example: A table of customers where each customer has a single phone number per record.

### 2NF (Second Normal Form)
- Meet all 1NF requirements.
- Remove partial dependencies (a non-key attribute is dependent on part of a composite key).
- Example: Splitting a table with customer information and orders into two tables, one for customers and one for orders, linked by a customer ID.

### 3NF (Third Normal Form)
- Meet all 2NF requirements.
- Remove transitive dependencies (a non-key attribute is dependent on another non-key attribute).
- Example: Removing a dependency where a customer's city is determined by their postal code, storing postal code and city information in a separate table.

### BCNF (Boyce-Codd Normal Form)
- A stronger version of 3NF where every determinant is a candidate key.
- Example: Ensuring that all functional dependencies are resolved, and the table structure supports unique identifiers for all records.

## 4. SQL Basics
### Data Definition Language (DDL)
- **CREATE TABLE**: Defines a new table.
```sql
CREATE TABLE employees (
  employee_id INT PRIMARY KEY,
  name VARCHAR(100),
  position VARCHAR(50),
  hire_date DATE
);
```
- **ALTER TABLE**: Modifies an existing table.
```sql
ALTER TABLE employees ADD COLUMN salary DECIMAL(10, 2);
```
- **DROP TABLE**: Deletes a table.
```sql
DROP TABLE employees;
```

### Data Manipulation Language (DML)
- **INSERT INTO**: Adds new rows to a table.
```sql
INSERT INTO employees (employee_id, name, position, hire_date) VALUES (1, 'Alice', 'Manager', '2020-01-15');
```
- **UPDATE**: Modifies existing rows in a table.
```sql
UPDATE employees SET salary = 75000 WHERE employee_id = 1;
```
- **DELETE**: Removes rows from a table.
```sql
DELETE FROM employees WHERE employee_id = 1;
```

### Data Query Language (DQL)
- **SELECT**: Retrieves data from one or more tables.
```sql
SELECT name, position FROM employees WHERE hire_date > '2021-01-01';
```

### Data Control Language (DCL)
- **GRANT**: Assigns permissions to users.
```sql
GRANT SELECT, INSERT ON employees TO user_name;
```
- **REVOKE**: Removes permissions from users.
```sql
REVOKE INSERT ON employees FROM user_name;
```

## 5. Advanced SQL
### Joins
- **INNER JOIN**: Selects records with matching values in both tables.
```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```

- **LEFT JOIN (or LEFT OUTER JOIN)**: Selects all records from the left table and matched records from the right table.
```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.department_id;
```

- **RIGHT JOIN (or RIGHT OUTER JOIN)**: Selects all records from the right table and matched records from the left table.
```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments ON employees.department_id = departments.department_id;
```

- **FULL JOIN (or FULL OUTER JOIN)**: Selects all records when there is a match in either left or right table.
```sql
SELECT employees.name, departments.department_name
FROM employees
FULL OUTER JOIN departments ON employees.department_id = departments.department_id;
```

### Subqueries
A query nested inside another query.
```sql
SELECT name FROM employees WHERE salary > (SELECT AVG(salary) FROM employees);
```

### Indexes
Improve query performance by reducing the amount of data scanned.
```sql
CREATE INDEX idx_name ON employees (name);
```

### Views
A virtual table based on the result set of a SQL query.
```sql
CREATE VIEW high_salary_employees AS
SELECT name, salary FROM employees WHERE salary > 70000;
```

## 6. Transactions
### ACID Properties
- **Atomicity**: All operations in a transaction are completed; if not, the transaction is aborted.
- **Consistency**: Ensures that the database properly changes states upon a successfully committed transaction.
- **Isolation**: Transactions occur independently without interference.
- **Durability**: Ensures that the results of a completed transaction are permanent.

### Transaction Control Commands
- **BEGIN TRANSACTION**: Starts a new transaction.
```sql
BEGIN TRANSACTION;
```
- **COMMIT**: Saves all changes made in the transaction.
```sql
COMMIT;
```
- **ROLLBACK**: Reverts all changes made in the transaction.
```sql
ROLLBACK;
```

## 7. NoSQL Databases
### Document Stores
Store data as documents (e.g., JSON, BSON).
- **Example**: MongoDB
- **Use Case**: Flexible schema design, hierarchical data storage.

### Key-Value Stores
Data is stored as key-value pairs.
- **Example**: Redis
- **Use Case**: High-speed data retrieval, caching.

### Column-Family Stores
Data is stored in columns rather than rows, optimized for read and write performance.
- **Example**: Cassandra
- **Use Case**: Handling large volumes of data across many servers.

### Graph Databases
Store data in graph structures with nodes, edges, and properties.
- **Example**: Neo4j
- **Use Case**: Complex relationship queries, social networks.

## 8. Database Security
### Authentication
Verify the identity of users.
- **Example**: Username and password, multi-factor authentication.

### Authorization
Define what an authenticated user is allowed to do.
- **Example**: Role-based access control (RBAC).

### Encryption
Protect data at rest and in transit.
- **Example**: AES encryption for data at rest, SSL/TLS for data in transit.

### Backup and Recovery
Regularly back up data and have a recovery plan in place.
- **Example**: Full, incremental, and differential backups.

## 9. Common Database Functions
### Aggregate Functions

- **COUNT()**: Returns the number of rows.
```sql
SELECT COUNT(*) FROM employees;
```

- **SUM()**: Returns the sum of a numeric column.
```sql
SELECT SUM(salary) FROM employees;
```

- **AVG()**: Returns the average value of a numeric column.
```sql
SELECT AVG(salary) FROM employees;
```

- **MIN()**: Returns the minimum value.
```sql
SELECT MIN(salary) FROM employees;
```

- **MAX()**: Returns the maximum value.
```sql
SELECT MAX(salary) FROM employees;
```

### String Functions

- **CONCAT()**: Concatenate strings.
```sql
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;
```

- **LENGTH()**: Return the length of a string.
```sql
SELECT LENGTH(name) FROM employees;
```

- **UPPER()**, **LOWER()**: Convert to upper or lower case.
```

sql
SELECT UPPER(name) FROM employees;
```

### Date Functions

- **NOW()**: Returns the current date and time.
```sql
SELECT NOW();
```

- **DATE_ADD()**, **DATE_SUB()**: Add or subtract dates.
```sql
SELECT DATE_ADD(hire_date, INTERVAL 1 YEAR) FROM employees;
```

- **DATEDIFF()**: Returns the difference between two dates.
```sql
SELECT DATEDIFF(NOW(), hire_date) FROM employees;
```

## 10. Performance Tuning
### Query Optimization
- Write efficient queries and use proper indexing to reduce the amount of data scanned.
- Example: Use indexed columns in `WHERE` clauses.

### Database Design
- Proper schema design, normalization, and choosing the right data types.
- Example: Use integer data types for numeric IDs rather than strings.

### Caching
- Use in-memory caches to reduce database load.
- Example: Redis for caching frequently accessed data.

### Load Balancing
- Distribute database load across multiple servers.
- Example: Use a load balancer to route queries to different database replicas.

## 11. Backup and Recovery
### Full Backup
- Complete backup of the entire database.
- Example: `mysqldump` for MySQL, `pg_dump` for PostgreSQL.

### Incremental Backup
- Backup of only the data that has changed since the last backup.
- Example: Backup tools that support incremental backups, such as Oracle RMAN.

### Point-in-Time Recovery
- Restoring the database to a specific point in time.
- Example: Using transaction logs to restore to a specific time.

## 12. Tools and Utilities
### Database Management Tools
- **phpMyAdmin**: Web-based MySQL administration tool.
- **pgAdmin**: Management tool for PostgreSQL.
- **SQL Server Management Studio (SSMS)**: Integrated environment for managing Microsoft SQL Server.
- **DB Browser for SQLite**: High quality, visual, open-source tool to create, design, and edit database files compatible with SQLite.
- [[SQLAlchemy]]: A SQL toolkit and Object-Relational Mapping (ORM) library for Python, which provides a full suite of well-known enterprise-level persistence patterns.

### Backup Tools
- **mysqldump**: Command-line utility for MySQL backups.
- **pg_dump**: Command-line utility for PostgreSQL backups.
- **Oracle RMAN**: Backup and recovery manager for Oracle databases.
- **SQLite Backup API**: Tools and utilities provided by SQLite for backing up database files.

### Monitoring Tools
- **Nagios**: Monitoring system for networks, systems, and infrastructure.
- **Zabbix**: Enterprise-level monitoring solution.
- **Prometheus**: Monitoring and alerting toolkit designed for reliability and scalability.