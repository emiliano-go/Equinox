---
tags:
  - sql
  - databases
  - concept
created: 2026-04-28
---

SQL stands for **Structured Query Language**. It is the standard language to communicate with [[Relational Databases]]. It's used to read, manipulate and manage data stored in tables.

### Basic Queries

A standard SQL query usually follows the following structure:

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY columnX;
```

**SELECT** indicates the columns you're gonna use
**FROM** specifies the table where does columns exist
**WHERE** filters rows following the condition
**ORDER BY** orders the results

Let's say we have a table called `Clients` with columns `Name`, `Age`, and `City`.

```sql
SELECT Name, City
FROM Clients
WHERE Age >= 18
ORDER BY Age
```

The result would look akin to:

| Name  | City   |
| ----- | ------ |
| Carol | Berlin |
| Bob   | Paris  |
| Dave  | Rome   |

If you want instead number of people per city:

```sql
SELECT City, COUNT(*) AS NumberOfPeople
FROM Clients
WHERE Age >= 18
GROUP BY City;
```

This would result in:

|City|NumberOfPeople|
|---|--:|
|Berlin|1|
|Paris|2|
|Rome|1|

## DDL vs DML

DDL stands for **Data Definition Language**, DML stands for **Data Manipulation Language.**

### DDL
DDL is used to define and modify the structure of the database. It uses keywords like `CREATE`, `ALTER` or `DROP`.

```sql
CREATE TABLE Productos (
  id INT PRIMARY KEY,
  nombre VARCHAR(100),
  precio DECIMAL(10,2)
);
```

### DML
DML is used to manipulate data inside tables. Uses keywords like `INSERT`, `UPDATE`, `DELETE` and `SELECT`.

```sql
INSERT INTO Productos (id, nombre, precio)
VALUES (1, 'Laptop', 1200.00);
```

## Primary and Foreign Keys

To relate entities, we use two types of keys:
- [[Primary Key|Primary Keys]]: identify with a unique constraint each row of a table
- [[Foreign key|Foreign Keys]]: references the primary key of **another table**, creating a relationship.

## Syntax

### SELECT
Used to extract data from one or more tables.

```sql
SELECT name, age FROM employees;
```

### DISTINCT
Eliminates duplicate rows in the query result.

```sql
SELECT DISTINCT city FROM clients;
```

### WHERE
Filter rows following a **logical condition**.

```sql
SELECT * FROM sales where amount > 1000;
```

#### Logical Operators
As all logical evaluators, the WHERE clause accepts logical operators:
- AND
- OR
- NOT

### ORDER BY
Orders results based on one or more columns.

```sql
SELECT name, salary FROM employees ORDER BY salary DESC
```

### LIMIT
Limits the number of results returned.

```sql
SELECT * FROM sales ORDER BY fecha DESC LIMIT 5;
```

