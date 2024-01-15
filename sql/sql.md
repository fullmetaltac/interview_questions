# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Install sandbox db with docker](#install-sandbox-db-with-docker)
  - [SQL](#sql)
    - [What is Data Integrity?](#what-is-data-integrity)
    - [What is an Alias in SQL?](#what-is-an-alias-in-sql)
    - [What are the TRUNCATE, DELETE and DROP statements??](#what-are-the-truncate-delete-and-drop-statements)
    - [What are HAVING and WHERE commands?](#what-are-having-and-where-commands)
    - [What are UNION and INTERSECT commands?](#what-are-union-and-intersect-commands)
    - [What are Constraints in SQL?](#what-are-constraints-in-sql)
    - [What is a Join? List its different types.](#what-is-a-join-list-its-different-types)
    - [What is a Cross-Join?](#what-is-a-cross-join)
    - [What is a Subquery? What are its types?](#what-is-a-subquery-what-are-its-types)
    - [What is an Index? Explain its different types.](#what-is-an-index-explain-its-different-types)
    - [What is the difference between Clustered and Non-clustered index?](#what-is-the-difference-between-clustered-and-non-clustered-index)
    - [What is Cursor? How to use a Cursor?](#what-is-cursor-how-to-use-a-cursor)
    - [What is a Function?](#what-is-a-function)
    - [What is a Stored Procedure?](#what-is-a-stored-procedure)
  - [References](#references)



## Install sandbox db with docker


```shell
# download postgres docker image:
docker pull postgres
# build and run postgres container
docker run -d --name pg -p 5432:5432 -e POSTGRES_PASSWORD=secret postgres
# create dvdrental db
docker exec -i pg psql -h localhost -U postgres -c "CREATE DATABASE dvdrental;"
# populate db with data from the backup file
docker exec -i pg pg_restore -U postgres -v -d dvdrental < dvdrental.tar
# run sample queries
docker exec -i pg psql -h localhost -U postgres -d dvdrental \
 -c "SELECT first_name, last_name FROM customer LIMIT 2;"
```

```shell
# output
 first_name | last_name
------------+-----------
 Jared      | Ely
 Mary       | Smith
(2 rows)
```
```shell
# or use interactive session
docker exec -it pg psql -h localhost -U postgres -d dvdrental
```

---

## SQL

### What is Data Integrity?
Data Integrity is the assurance of accuracy and consistency of data over its entire life-cycle and is a critical aspect of the design, implementation, and usage of any system which stores, processes, or retrieves data. It also defines integrity constraints to enforce business rules on the data when it is entered into an application or a database.

---

###  What is an Alias in SQL?

A column alias allows you to assign a column or an expression in the select list of a `SELECT` statement a temporary name. The column alias exists temporarily during the execution of the query.

```sql
SELECT 
   first_name, 
   last_name AS surname
FROM customer
LIMIT 2;
```

```shell
# output
 first_name | surname
------------+---------
 Jared      | Ely
 Mary       | Smith
(2 rows)
```

---

### What are the TRUNCATE, DELETE and DROP statements??

:bulb: `DELETE` statement is used to delete rows from a table.

```sql
DELETE FROM Candidates
WHERE CandidateId > 1000;
```

:bulb: `TRUNCATE` command is used to delete all the rows from the table and free the space containing the table.

```sql
TRUNCATE TABLE Candidates;
```

:bulb: `DROP` command is used to remove an object from the database. If you drop a table, all the rows in the table are deleted and the table structure is removed from the database.

```sql
DROP TABLE Candidates;
```

---

### What are HAVING and WHERE commands?

- The `SELECT` statement returns all rows from one or more columns in a table. To select rows that satisfy a specified condition, you use a `WHERE` clause.


```sql
SELECT
	first_name,
	last_name
FROM
	customer
WHERE
	last_name = 'Rodriguez' OR 
	first_name = 'Adam';
```

```shell
# output
 first_name | last_name 
------------+-----------
 Laura      | Rodriguez
 Adam       | Gooch
(2 rows)
```

- The `HAVING` clause specifies a search condition for a group or an aggregate. The `HAVING` clause is often used with the `GROUP BY` clause to filter groups or aggregates based on a specified condition.

```sql
SELECT
	customer_id,
	SUM (amount)
FROM
	payment
GROUP BY
	customer_id
HAVING
	SUM (amount) > 200;
```

```shell
# output
 customer_id |  sum
-------------+--------
         526 | 208.58
         148 | 211.55
(2 rows)
```

:memo: The `WHERE` clause allows you to filter rows based on a specified condition. However, the `HAVING` clause allows you to filter groups of rows according to a specified condition.

---

### What are UNION and INTERSECT commands?   


- The `UNION` operator combines and returns the result-set retrieved by two or more `SELECT` statements.
- The `MINUS` operator in SQL is used to remove duplicates from the result-set obtained by the second `SELECT` query from the result-set obtained by the first `SELECT` query and then return the filtered results from the first.
- The `INTERSECT` clause in SQL combines the result-set fetched by the two `SELECT` statements where records from one match the other and then returns this intersection of result-sets.

:bulb: *Example*

The following statements create two tables: `top_rated_films` and `most_popular_films`, and insert data into these tables:

```sql
DROP TABLE IF EXISTS top_rated_films;
CREATE TABLE top_rated_films(
	title VARCHAR NOT NULL,
	release_year SMALLINT
);

DROP TABLE IF EXISTS most_popular_films;
CREATE TABLE most_popular_films(
	title VARCHAR NOT NULL,
	release_year SMALLINT
);

INSERT INTO 
   top_rated_films(title,release_year)
VALUES
   ('The Shawshank Redemption',1994),
   ('The Godfather',1972),
   ('12 Angry Men',1957);

INSERT INTO 
   most_popular_films(title,release_year)
VALUES
   ('An American Pickle',2020),
   ('The Godfather',1972),
   ('Greyhound',2020);
```

:bulb: *UNION*

The following statement uses the `UNION` operator to combine data from both tables:

```sql
SELECT * FROM top_rated_films
UNION
SELECT * FROM most_popular_films;
```

```shell
# output
          title           | release_year
--------------------------+--------------
 An American Pickle       |         2020
 Greyhound                |         2020
 The Shawshank Redemption |         1994
 The Godfather            |         1972
 12 Angry Men             |         1957
```

:bulb: *INTERSECT*

To get popular films which are also top rated films, you use the `INTERSECT` operator as follows:

```sql
SELECT *
FROM most_popular_films 
INTERSECT
SELECT *
FROM top_rated_films;
```

```shell
# output
     title     | release_year
---------------+--------------
 The Godfather |         1972
(1 row)
```
---

### What are Constraints in SQL?

Constraints are used to specify the rules concerning data in the table. It can be applied for single or multiple fields in an SQL table during the creation of the table or after creating using the ALTER TABLE command. The constraints are:

:bulb: *PRIMARY KEY*
> Uniquely identifies each record in a table.

The following statement creates a purchase order (PO) header table with the name `po_headers`.

```sql
CREATE TABLE po_headers (
        po_no INTEGER PRIMARY KEY,
        vendor_no INTEGER,
        description TEXT,
        shipping_address TEXT
);
```
The `po_no` is the primary key of the `po_headers` table, which uniquely identifies purchase order in the `po_headers` table.

:bulb: *FOREIGN KEY*
> Ensures referential integrity for a record in another table.

The following statements create the `customers` and `contacts` tables:

```sql
DROP TABLE IF EXISTS customers;
DROP TABLE IF EXISTS contacts;

CREATE TABLE customers(
   customer_id INT GENERATED ALWAYS AS IDENTITY,
   customer_name VARCHAR(255) NOT NULL,
   PRIMARY KEY(customer_id)
);

CREATE TABLE contacts(
   contact_id INT GENERATED ALWAYS AS IDENTITY,
   customer_id INT,
   contact_name VARCHAR(255) NOT NULL,
   phone VARCHAR(15),
   email VARCHAR(100),
   PRIMARY KEY(contact_id),
   CONSTRAINT fk_customer
      FOREIGN KEY(customer_id) 
	  REFERENCES customers(customer_id)
);
```

In this example, the `customers` table is the parent table and the `contacts` table is the child table.

Each customer has zero or many contacts and each contact belongs to zero or one customer.

The `customer_id` column in the `contacts` table is the *foreign key* column that references the *primary key* column with the same name in the `customers` table.

:bulb: *CHECK*
> Verifies that all values in a field satisfy a condition.

Typically, you use the `CHECK` constraint at the time of creating the table using the `CREATE TABLE` statement.

The following statement defines an `employees` table.

```sql
DROP TABLE IF EXISTS employees;
CREATE TABLE employees (
	id SERIAL PRIMARY KEY,
	first_name VARCHAR (50),
	last_name VARCHAR (50),
	birth_date DATE CHECK (birth_date > '1900-01-01'),
	joined_date DATE CHECK (joined_date > birth_date),
	salary numeric CHECK(salary > 0)
);
```

The `employees` table has three `CHECK` constraints:

- First, the birth date (`birth_date`) of the employee must be greater than `01/01/1900`. If you try to insert a birth date before `01/01/1900`, you will receive an error message.
- Second, the joined date (`joined_date`) must be greater than the birth date (`birth_date`). - This check will prevent from updating invalid dates in terms of their semantic meanings.
- Third, the salary must be greater than zero, which is obvious.

:bulb: *UNIQUE*
>  Ensures unique values to be inserted into the field.

The following statement creates a new table named `person` with a `UNIQUE` constraint for the `email` column.

```sql
CREATE TABLE person (
	id SERIAL PRIMARY KEY,
	first_name VARCHAR (50),
	last_name VARCHAR (50),
	email VARCHAR (50) UNIQUE
);
```

:bulb: *NOT NULL*
> Ensures unique values to be inserted into the field.

The following `CREATE TABLE` statement creates a new table name `invoices` with the not-null constraints.

```sql
CREATE TABLE invoices(
  id SERIAL PRIMARY KEY,
  product_id INT NOT NULL,
  qty numeric NOT NULL CHECK(qty > 0),
  net_price numeric CHECK(net_price > 0) 
);
```
This example uses the NOT NULL keywords that follow the data type of the product_id and qty columns to declare NOT NULL constraints.

---

### What is a Join? List its different types.

PostgreSQL join is used to combine columns from one (self-join) or more tables based on the values of the common columns between related tables. 

PostgreSQL supports inner join, left join, right join, full outer join, cross join, natural join, and a special kind of join called self-join.

![joins](https://www.postgresqltutorial.com/wp-content/uploads/2018/12/PostgreSQL-Joins.png)

:bulb: *Example*

Suppose that you have two tables `films` and `film_reviews` like this:

```sql
DROP TABLE IF EXISTS films;
DROP TABLE IF EXISTS film_reviews;

CREATE TABLE films(
   film_id SERIAL PRIMARY KEY,
   title varchar(255) NOT NULL
);

INSERT INTO films(title)
VALUES('Joker'),
      ('Avengers: Endgame'),
      ('Parasite');

CREATE TABLE film_reviews(
   review_id SERIAL PRIMARY KEY,
   film_id INT,
   review VARCHAR(255) NOT NULL	
);

INSERT INTO film_reviews(film_id, review)
VALUES(1, 'Excellent'),
      (1, 'Awesome'),
      (2, 'Cool'),
      (NULL, 'Beautiful');
```

The following statement uses the `RIGHT JOIN` to select data from the `films` and `film_reviews` tables:

```sql
SELECT 
   review, 
   title
FROM 
   films
RIGHT JOIN film_reviews 
   ON film_reviews.film_id = films.film_id
LIMIT 2;
```

```shell
# output
  review   | title
-----------+-------
 Excellent | Joker
 Awesome   | Joker
(2 rows)
```

---

### What is a Cross-Join?

A `CROSS JOIN` clause allows you to produce a Cartesian Product of rows in two or more tables.

![cross join](https://www.postgresqltutorial.com/wp-content/uploads/2016/06/PostgreSQL-CROSS-JOIN-illustration.png)

:bulb: *Example*

The following `CREATE TABLE` statements create `T1` and `T2` tables and insert some sample data for the cross-demonstration.

```sql
DROP TABLE IF EXISTS T1;
CREATE TABLE T1 (label CHAR(1) PRIMARY KEY);

DROP TABLE IF EXISTS T2;
CREATE TABLE T2 (score INT PRIMARY KEY);

INSERT INTO T1 (label)
VALUES
	('A'),
	('B');

INSERT INTO T2 (score)
VALUES
	(1),
	(2),
	(3);
```

The following statement uses the `CROSS JOIN` operator to join table `T1` with table `T2`.

```sql
SELECT *
FROM T1
CROSS JOIN T2;
```

```shell
 label | score
-------+-------
 A     |     1
 B     |     1
 A     |     2
 B     |     2
 A     |     3
 B     |     3
(6 rows)
```

---

### What is a Subquery? What are its types?

A subquery is a query within another query, also known as a *nested query* or *inner query*.

- A **correlated** subquery cannot be considered as an independent query, but it can refer to the column in a table listed in the FROM of the main query.
- A **non-correlated** subquery can be considered as an independent query and the output of the subquery is substituted in the main query.

```sql
SELECT
	film_id,
	title,
	rental_rate
FROM
	film
WHERE
	rental_rate > (
		SELECT
			AVG (rental_rate)
		FROM
			film
	)
LIMIT 2;
```

```shell
# output
 film_id |      title       | rental_rate
---------+------------------+-------------
     133 | Chamber Italian  |        4.99
     384 | Grosse Wonderful |        4.99
(2 rows)
```

---

### What is an Index? Explain its different types.

PostgreSQL indexes are effective tools to enhance database performance. Indexes help the database server find specific rows much faster than it could do without indexes. 

:bulb: *Example*

To show the query plan, you use the `EXPLAIN` statement as follows:

```sql
EXPLAIN SELECT *
FROM address
WHERE phone = '223664661973';
```

```shell
                       QUERY PLAN
---------------------------------------------------------
 Seq Scan on address  (cost=0.00..15.54 rows=1 width=61)
   Filter: ((phone)::text = '223664661973'::text)
(2 rows)
```

To create an index for the values in the `phone` column of the `address` table, you use the following statement:

```sql
CREATE INDEX idx_address_phone 
ON address(phone);
```

Now, if you execute the query again, you will find that the database engine uses the index for lookup:

```shell
                                    QUERY PLAN
----------------------------------------------------------------------------------
 Index Scan using idx_address_phone on address  (cost=0.28..8.29 rows=1 width=61)
   Index Cond: ((phone)::text = '223664661973'::text)
(2 rows)
```

An index is a separated data structure that speeds up the data retrieval on a table at the cost of additional writes and storage to maintain it.

:bulb: *B-tree indexes*

> B-tree is a self-balancing tree that maintains sorted data and allows searches, insertions, deletions, and sequential access in logarithmic time.

:bulb: *Hash indexes*

> Hash indexes can handle only simple equality comparison (=). It means that whenever an indexed column is involved in a comparison using the equal(=) operator, the query planner will consider using a hash index.

:bulb: *GIN indexes*

> GIN stands for generalized inverted indexes. It is commonly referred to as GIN.

:bulb: *BRIN*

> BRIN stands for block range indexes. BRIN is much smaller and less costly to maintain in comparison with a B-tree index.

:bulb: *GiST Indexes*

> GiST stands for Generalized Search Tree. GiST indexes allow the building of general tree structures. GiST indexes are useful in indexing geometric data types and full-text searches.

:bulb: *SP-GiST Indexes*

> SP-GiST stands for space-partitioned GiST. SP-GiST supports partitioned search trees that facilitate the development of a wide range of different non-balanced data structures.

---

### What is the difference between Clustered and Non-clustered index?

- Clustered index modifies the way records are stored in a database based on the indexed column. A non-clustered index creates a separate entity within the table which references the original table.
- Clustered index is used for easy and speedy retrieval of data from the database, whereas, fetching records from the non-clustered index is relatively slower.
- In SQL, a table can have a single clustered index whereas it can have multiple non-clustered indexes.
---

### What is Cursor? How to use a Cursor?

A Cursor in PostgreSQL is used to process large tables. Suppose if a table has 10 million or billion rows. While performing a `SELECT` operation on the table it will take some time to process the result and most likely give an “out of memory” error and the program will be terminated.

A Cursor can only be declared inside a transaction. The cursor does not calculate the data but only prepares the query so that your data can be created when `FETCH` is called. In the end, simply commit the transaction.

```sql
BEGIN;

DECLARE 
    cur_film CURSOR FOR SELECT film_id, title FROM film;
```

```sql
FETCH NEXT FROM cur_film;
```

```shell
# output
 film_id |      title
---------+------------------
     133 | Chamber Italian

(1 row)
```
```sql
FETCH 2 FROM cur_film;
```
```shell
# output
 film_id |       title
---------+-------------------
     384 | Grosse Wonderful
       8 | Airport Pollock
(2 rows)
```

```sql
COMMIT;
```

---

### What is a Function?

PL/pgSQL is a procedural programming language for the PostgreSQL database system.

PL/pgSQL was designed to :

  - Create user-defined functions, stored procedures, and triggers.
  - Extend standard SQL by adding control structures such as if, case, and loop statements.
  - Inherit all user-defined functions, operators, and types.

```sql
CREATE OR REPLACE FUNCTION film_count()
RETURNS integer AS $total$
declare
	total integer;
BEGIN
   SELECT count(*) into total FROM film;
   RETURN total;
END;
$total$ LANGUAGE plpgsql;
```

```sql
select film_count();
```

```shell
# output
 film_count
------------
       1000
(1 row)
```

---

### What is a Stored Procedure?

A drawback of user-defined functions is that they cannot execute transactions. In other words, inside a user-defined function, you cannot start a transaction, and commit or rollback it.

PostgreSQL 11 introduced stored procedures that support transactions.

```sql
CREATE TABLE invoices (
  invoice_id SERIAL PRIMARY KEY,
  customer_name TEXT NOT NULL,
  total_amount NUMERIC NOT NULL,
  invoice_date DATE NOT NULL,
  is_paid BOOLEAN DEFAULT FALSE
);
```
```sql
CREATE OR REPLACE PROCEDURE create_invoice(
  IN customer_name TEXT,
  IN total_amount NUMERIC,
  IN invoice_date DATE
)
LANGUAGE plpgsql
AS $$
BEGIN
  INSERT INTO invoices (customer_name, total_amount, invoice_date)
  VALUES (customer_name, total_amount, invoice_date);
END;
$$
```

```sql
CALL create_invoice('Customer 1', 100, '2023-07-20');
```

```sql
select * FROM invoices;
```

```shell
# output
 invoice_id | customer_name | total_amount | invoice_date | is_paid 
------------+---------------+--------------+--------------+---------
          1 | Customer 1    |          100 | 2023-07-20   | f
(1 row)
```


---

## References
- https://www.postgresqltutorial.com/
- https://www.interviewbit.com/sql-interview-questions/ 