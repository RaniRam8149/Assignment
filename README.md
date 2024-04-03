
Q1. What is a database? Differentiate between SQL and NoSQL databases.
A database is a structured collection of data that is organized in a way that allows for efficient storage, retrieval, and manipulation of data. It serves as a repository for storing various types of information, such as customer records, product catalogs, financial transactions, etc. Databases are commonly used in software applications, websites, and other digital systems to manage and process data.
SQL (Structured Query Language) and NoSQL (Not Only SQL) are two different types of database management systems, each with its own characteristics and use cases:

SQL databases:
SQL databases are relational databases that use structured query language (SQL) for defining and manipulating data.
They have a predefined schema that defines the structure of the data, including tables, columns, and relationships between tables.
SQL databases are ideal for applications that require complex queries, transactions, and strict consistency guarantees.
Examples of SQL databases include MySQL, PostgreSQL, Oracle, Microsoft SQL Server, etc.

NoSQL databases:
NoSQL databases are non-relational databases that provide a flexible schema and are designed to handle large volumes of unstructured or semi-structured data.
They can store data in various formats, such as key-value pairs, document-oriented, column-family, or graph databases.
NoSQL databases offer high scalability, availability, and performance, making them suitable for applications with large-scale distributed architectures and real-time data processing needs.
They are often used in web applications, IoT (Internet of Things), big data, and analytics applications.
Examples of NoSQL databases include MongoDB, Cassandra, Couchbase, Redis, Amazon DynamoDB, etc.


Q2. What is DDL? Explain why CREATE, DROP, ALTER, and TRUNCATE are used with an example
DDL stands for Data Definition Language. It is a subset of SQL (Structured Query Language) used to define, modify, and manage the structure of database objects, such as tables, indexes, views, and schemas. DDL statements are used to create, modify, and delete database objects, as well as to define the structure and integrity constraints of the data stored in those objects.

Here's an explanation of some common DDL statements and their usage with examples:

CREATE:
The CREATE statement is used to create new database objects, such as tables, indexes, views, or schemas.
Example: Creating a new table named "Employees" with columns for employee ID, name, and department:

CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50),
    Department VARCHAR(50)
);

DROP:
The DROP statement is used to delete existing database objects, such as tables, indexes, views, or schemas.
Example: Dropping the "Employees" table:

DROP TABLE Employees;

ALTER:
The ALTER statement is used to modify the structure of existing database objects, such as tables, by adding, modifying, or dropping columns, constraints, or indexes.
Example: Adding a new column "Salary" to the "Employees" table:

ALTER TABLE Employees
ADD Salary DECIMAL(10, 2);

TRUNCATE:
The TRUNCATE statement is used to remove all rows from a table while keeping the table structure intact. It is faster and more efficient than using DELETE to remove all rows because it does not log individual row deletions.
Example: Truncating the "Employees" table to remove all existing data:

TRUNCATE TABLE Employees;


Q3. What is DML? Explain INSERT, UPDATE, and DELETE with an example.
DML stands for Data Manipulation Language. It is a subset of SQL (Structured Query Language) used to manipulate data stored in a database. DML statements are used to insert, update, delete, and retrieve data from database tables. Here's an explanation of some common DML statements and their usage with examples:

INSERT:
The INSERT statement is used to add new rows of data into a table.
Example: Inserting a new record into the "Employees" table:

INSERT INTO Employees (EmployeeID, Name, Department, Salary)
VALUES (1, 'John Doe', 'Sales', 50000);

UPDATE:
The UPDATE statement is used to modify existing data in a table.
Example: Updating the salary of an employee in the "Employees" table:

UPDATE Employees
SET Salary = 55000
WHERE EmployeeID = 1;

DELETE:
The DELETE statement is used to remove one or more rows from a table.
Example: Deleting a record from the "Employees" table based on a condition:

DELETE FROM Employees
WHERE EmployeeID = 1;


Q4. What is DQL? Explain SELECT with an example.

DQL stands for Data Query Language. It is a subset of SQL (Structured Query Language) used to retrieve data from a database. DQL primarily consists of the SELECT statement, which is used to fetch data from one or more database tables based on specified criteria.

Here's an explanation of the SELECT statement with an example:

SELECT Statement:
The SELECT statement is used to retrieve data from one or more tables in a database.
It allows you to specify which columns you want to retrieve, as well as any filtering, sorting, or grouping criteria.
You can also perform calculations and apply functions on the selected data.

Example:
Consider a table named "Employees" with columns such as EmployeeID, Name, Department, and Salary. Here's how you can use the SELECT statement to retrieve data from this table:

SELECT * FROM Employees;


Q5. Explain Primary Key and Foreign Key.

Primary Key and Foreign Key are two important concepts in relational database design that help establish relationships between tables and maintain data integrity.

Primary Key:
A Primary Key is a column or set of columns in a table that uniquely identifies each row in the table.
It must contain unique values, and it cannot contain NULL values.
There can be only one Primary Key in a table.
Primary Keys are used to enforce entity integrity, ensuring that each record in the table is uniquely identifiable.
Typically, Primary Keys are implemented using unique constraints or indexes.
Examples of Primary Keys include employee ID, customer ID, order ID, etc.

Foreign Key:
A Foreign Key is a column or set of columns in a table that establishes a link or relationship between two tables.
It refers to the Primary Key of another table and ensures referential integrity.
Foreign Keys enforce constraints that maintain consistency between related tables.
Foreign Keys can have NULL values, indicating that the relationship is optional.
Typically, Foreign Keys are implemented using foreign key constraints.


Q6. Write a python code to connect MySQL to python. Explain the cursor() and execute() method.

import mysql.connector

mydb = mysql.connector.connect(
    host="localhost",
    user="yourusername",
    password="yourpassword",
    database="yourdatabase"
)

mycursor = mydb.cursor()

mycursor.execute("SELECT * FROM yourtable")

result = mycursor.fetchall()

for row in result:
    print(row)

mycursor.close()
mydb.close()

Explanation of cursor() and execute() methods:

cursor() method:
The cursor() method is used to create a cursor object, which allows Python code to interact with the MySQL database.
This method returns a cursor object that can execute SQL queries and fetch results from the database.
It is called on the database connection object (mydb in this case) to create a new cursor instance.

execute() method:
The execute() method is used to execute a SQL query on the database using the cursor object.
It takes a SQL query string as an argument and executes it on the database.
This method is called on the cursor object (mycursor in this case) and can be used to execute any SQL query, such as SELECT, INSERT, UPDATE, DELETE, etc.


Q7. Give the order of execution of SQL clauses in an SQL query.

In SQL, the order of execution of clauses in an SQL query generally follows this sequence:

FROM: Specifies the table(s) from which data will be retrieved.
WHERE: Filters the rows based on specified conditions.
GROUP BY: Groups the rows that have the same values into summary rows.
HAVING: Filters groups based on specified conditions.
SELECT: Specifies the columns to be retrieved.
DISTINCT: Filters duplicate rows from the result set (if used).
ORDER BY: Sorts the result set based on specified columns.
LIMIT/OFFSET: Limits the number of rows returned and optionally specifies a starting point for the result set.
