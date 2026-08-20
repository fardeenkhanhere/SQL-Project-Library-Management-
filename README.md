# SQL-Project-Library-Management-
📚 SQL Library Management System
A complete SQL Library Management System project designed to demonstrate practical SQL skills using a real-world database scenario.

This project covers everything from database creation and table design to advanced SQL concepts such as joins, subqueries, CTEs, window functions, stored procedures, triggers, views, and transactions.

It is an ideal project for showcasing SQL knowledge as part of a Data Analyst portfolio, GitHub portfolio, or SQL learning journey.

🎯 Project Objective
The main objective of this project is to design and build a relational database for managing a library.

The system helps manage:

👥 Library Members

✍️ Authors

📚 Books

🔄 Book Borrowing and Return Records

Through this project, I have applied various SQL concepts ranging from basic data manipulation to advanced database operations.

🛠️ Technologies Used
SQL

MySQL

🗄️ Database Structure
The project consists of the following main tables:

Table Name	Description
Members	Stores information about library members
Authors	Stores information about book authors
Books	Stores book details, categories, prices, and availability
Borrow	Stores book borrowing and return transactions
🔗 Database Relationships
The database follows a relational structure using Primary Keys and Foreign Keys.

Authors
   │
   │ AuthorID
   ▼
Books
   │
   │ BookID
   ▼
Borrow
   ▲
   │
Members
Relationships
Books.AuthorID → Authors.AuthorID

Borrow.MemberID → Members.MemberID

Borrow.BookID → Books.BookID
🧱 Database Schema
Members
Stores information about library members.

Example fields:

MemberID

MemberName

Email

Phone

JoinDate

Authors
Stores information about book authors.

Example fields:

AuthorID

AuthorName

Country

Books
Stores information about books available in the library.

Example fields:

BookID

Title

AuthorID

Category

Price

AvailableQuantity

Borrow
Stores book borrowing and return transactions.

Example fields:

BorrowID

MemberID

BookID

BorrowDate

ReturnDate

Status

📊 Sample Data
The database contains sample records for:

5 Library Members

5 Authors

5 Books

7 Borrowing Transactions

Sample books used in this project include:

Five Point Someone

Harry Potter

The Da Vinci Code

The Monk Who Sold His Ferrari

The Alchemist

📚 SQL Concepts Covered
This project covers a wide range of SQL concepts.

🔹 Basic SQL
CREATE DATABASE

CREATE TABLE

ALTER TABLE

DROP TABLE

Primary Keys

Foreign Keys

Constraints

🔹 CRUD Operations
Create
INSERT INTO Books
VALUES (...);
Read
SELECT * 
FROM Books;
Update
UPDATE Books
SET Price = 500
WHERE BookID = 1;
Delete
DELETE FROM Books
WHERE BookID = 1;
🔍 Filtering and Sorting
The project demonstrates data filtering using:

WHERE

AND

OR

IN

BETWEEN

LIKE

ORDER BY

LIMIT

Example
Find books with a price greater than 400:

SELECT *
FROM Books
WHERE Price > 400;
📊 Aggregate Functions
The following aggregate functions are used:

COUNT()

SUM()

AVG()

MIN()

MAX()

Example: Average Book Price
SELECT AVG(Price) AS AveragePrice
FROM Books;
📈 GROUP BY and HAVING
The project performs category-level analysis using GROUP BY and HAVING.

Example: Count Books by Category
SELECT Category,
       COUNT(*) AS TotalBooks
FROM Books
GROUP BY Category;
Example: Categories Having More Than One Book
SELECT Category,
       COUNT(*) AS TotalBooks
FROM Books
GROUP BY Category
HAVING COUNT(*) > 1;
🔗 SQL Joins
The project demonstrates different types of joins.

INNER JOIN

LEFT JOIN

RIGHT JOIN

FULL OUTER JOIN

Example: Display Books with Author Names
SELECT 
    b.Title,
    a.AuthorName
FROM Books b
INNER JOIN Authors a
ON b.AuthorID = a.AuthorID;
🔎 Subqueries
Subqueries are used to perform advanced data filtering and analysis.

Example
Find books with a price higher than the average book price.

SELECT *
FROM Books
WHERE Price > (
    SELECT AVG(Price)
    FROM Books
);
✅ EXISTS
The EXISTS operator is used to check whether related records exist.

Example
Find members who have borrowed at least one book.

SELECT *
FROM Members m
WHERE EXISTS (
    SELECT 1
    FROM Borrow b
    WHERE b.MemberID = m.MemberID
);
🔀 CASE Statements
CASE statements are used to categorize data.

Example
Categorize books based on their price.

SELECT 
    Title,
    Price,
    CASE
        WHEN Price >= 500 THEN 'Expensive'
        WHEN Price >= 300 THEN 'Moderate'
        ELSE 'Affordable'
    END AS PriceCategory
FROM Books;
👁️ Views
A view is created to simplify frequently used queries.

Example
CREATE VIEW BookDetails AS
SELECT
    b.BookID,
    b.Title,
    a.AuthorName,
    b.Category,
    b.Price
FROM Books b
JOIN Authors a
ON b.AuthorID = a.AuthorID;
The view can then be queried using:

SELECT *
FROM BookDetails;
⚙️ Advanced SQL Concepts
This project also includes the following advanced SQL features:

Stored Procedures
Stored procedures are used to execute reusable SQL operations.

Functions
Custom functions are created for calculations such as total book prices.

Triggers
Triggers are used to automatically update book stock when borrowing transactions occur.

Transactions
Transactions are used to ensure data consistency.

Commands demonstrated include:

START TRANSACTION;

COMMIT;

ROLLBACK;
🧩 Common Table Expressions (CTEs)
CTEs are used to simplify complex queries.

Example
WITH BookPriceAnalysis AS (
    SELECT
        Title,
        Price,
        AVG(Price) OVER() AS AveragePrice
    FROM Books
)
SELECT *
FROM BookPriceAnalysis;
🏆 Window Functions and Ranking
Window functions are used for analytical operations.

Example: Rank Books by Price
SELECT
    Title,
    Price,
    RANK() OVER (
        ORDER BY Price DESC
    ) AS Ranking
FROM Books;
📄 Pagination
The project also demonstrates retrieving data in smaller chunks using pagination.

Example:

SELECT *
FROM Books
LIMIT 5 OFFSET 0;
📁 Project Structure
SQL-Library-Management-System/
│
├── Library_Management.sql
│
├── SQL_Project_Library_Management.docx
│
└── README.md
Library_Management.sql
Contains:

Database creation

Table creation

Constraints

Sample data

CRUD operations

Joins

Subqueries

Aggregate functions

Views

Stored procedures

Functions

Triggers

Transactions

CTEs

Window functions

SQL_Project_Library_Management.docx
Contains detailed project documentation and explanations of the SQL concepts used in the project.

README.md
Provides an overview of the project, database design, SQL concepts, and project objectives.

🚀 How to Use This Project
Step 1: Clone the Repository
git clone <your-github-repository-url>
Step 2: Open Your SQL Environment
You can use:

MySQL Workbench

SQL Server Management Studio

DBeaver

phpMyAdmin

Any compatible SQL environment

Step 3: Run the SQL File
Open:

Library_Management.sql
Execute the script to:

Create the database

Create the tables

Apply constraints

Insert sample data

Run SQL queries and analysis

💡 Key Learning Outcomes
Through this project, I practiced and strengthened my understanding of:

Relational Database Design

Primary and Foreign Keys

Database Constraints

CRUD Operations

Data Filtering and Sorting

Aggregate Functions

GROUP BY and HAVING

SQL Joins

Subqueries

EXISTS

CASE Statements

Views

Stored Procedures

Functions

Triggers

Transactions

CTEs

Window Functions

Ranking

Pagination

🔮 Future Improvements
Possible future enhancements for this project include:

Adding more members and books

Implementing book reservation functionality

Adding late-return tracking

Automatically calculating late fees

Creating member-wise borrowing analysis

Creating author-wise book performance analysis

Adding monthly borrowing trends

Building a Library Analytics Dashboard using Power BI

Creating stored procedures for common library operations

Adding user authentication and role-based access

📊 Potential Analytics Questions
Some business questions that can be explored using this database include:

Which books are borrowed the most?

Which members borrow books most frequently?

Which authors have the highest number of books in the library?

What is the average price of books by category?

Which books are currently unavailable?

Which members have not returned books?

Which categories contain the most books?

Which books are the most expensive?

What are the monthly borrowing trends?

🎓 Purpose of This Project
I created this project as part of my SQL learning and portfolio development journey.

The goal was to build a practical project that demonstrates SQL concepts in a structured and easy-to-understand way, while applying them to a real-world Library Management scenario.

This project can be useful for:

SQL Beginners

Aspiring Data Analysts

Students learning SQL

SQL Interview Preparation

Data Analytics Portfolio Projects

GitHub Portfolio Development

👨‍💻 About Me
I am an aspiring Data Analyst with an interest in:

SQL

Excel

Power BI

Python

Data Analysis

Database Management

I am continuously working on practical projects to strengthen my technical skills and build a professional data analytics portfolio.

⭐ If You Found This Project Useful
If you found this project helpful or interesting, please consider giving the repository a Star ⭐.

It motivates me to continue building and sharing more data analytics and SQL projects.

📌 Connect With Me
Feel free to connect with me and explore my other projects on GitHub.
