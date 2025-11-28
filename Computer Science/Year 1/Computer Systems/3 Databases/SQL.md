 #cs 

### Database Languages 

Expected features:
- can create DB, define properties
- data management and simple or complex queries
- easy to learn and use
- standardised language

**SQL** (Structured Query Language):
- most common DB lang 
- simple syntax
- made up of DDL and DML

**DDL** (Data Definition Language):
- define relation **schema** (attributes)
- define attribute **domain** (types for attribute values)
- specify **integrity constraints** (primary/foreign keys)

**DML** (Data Manipulation Language):
- **insert/update/delete/retrieve** data from DB
- **query language**: retrieval part of DML

Two types of DB langs - declarative and procedural
- SQL is **declarative**
- query transformed to **procedural** form
- different transformations $\rightarrow$ optimise performance![[Screenshot 2025-05-16 at 14.23.37.png]]
### SQL Statements

Statements consist of:
- **reserved words** e.g. SELECT, WHERE etc
- **user-defined words**: names of relations, attributes etc
- **literals**: non-numeric\string literals must be enclosed in 'single quotes', numeric literals must not be![[Screenshot 2025-05-16 at 14.29.48.png]]
Most components **case-insensitive**
- except for table names and character literals ('SMITH' vs 'smith')

SQL is **free-format**
- line breaks, white space and indents do not matter
- statements chained and terminated with **semicolon;**
- semicolon required in some implementations

### Data Manipulation Language (DML)

| Statement | Purpose                             |
| --------- | ----------------------------------- |
| SELECT    | query data in DB                    |
| INSERT    | insert new data into existing table |
| UPDATE    | update data in existing table       |
| DELETE    | delete data from existing table     |

### SELECT Statement

```SELECT 

SELECT     [ DISTINCT ]{ * | column1 [ AS newName ][, ...]}
FROM       table1[ alias ][, ...]
[ WHERE    conditions ]
[ GROUP BY columnList ]
[ HAVING   conditions ]
[ ORDER BY columnList [ ASC | DESC ]]
```
- `FROM`: specifies table(s) to be used
- `WHERE`: filters rows subject to condition
- `GROUP BY`: forms groups of rows with same column value
- `HAVING`: filters groups subject to condition
- `SELECT`: specifies column to appear in output
- `ORDER BY`: specifies output order

If variable contains /, is **derived** (calculated)
- can assign different name with `AS` clause

Cannot reuse alias in `WHERE`/`GROUP BY`/`HAVING`
```
SELECT staffNo, fName, lName, salary/12 AS monthlySalary  
FROM Staff  
WHERE salary/12 < 1500  
```
- use salary/12 again instead of monthlySalary to ensure value has been determined upon evaluation

`DISTINCT` used to eliminate duplicates
- normalised relations don't contain duplicate rows
- `SELECT` result can have duplicate rows so use `DISTINCT` to eliminate

### Constructing Conditions

Comparison operators:

| Operator | Purpose                   |
| -------- | ------------------------- |
| =        | equal                     |
| <        | less than                 |
| >        | greater than              |
| <=       | less or equal             |
| >=       | greater or equal          |
| <>       | not equal (standard)      |
| !=       | not equal (some dialects) |

Range:
- x `BETWEEN` y `AND` z
- includes min/max

Set membership:
- `IN` (x, y, z, ...)

Pattern matching:
- `LIKE` 'some pattern'
- $\%$ (percent) represents **sequence** of zero or more characters (some dialects use $*$)
- $\_$ (underscore) represents arbitrary **single character** (some dialects use $?$)
- `LIKE 'H%'` means: first character is 'H' but rest can be anything
- `LIKE 'H___'` means: exactly 4 characters, first being 'H'
- `LIKE '%e'` means: any string ending in 'e'
- `NOT LIKE 'H%'` means: first character is not 'H'

Testing for NULL:
- `IS NULL`/`IS NOT NULL`
- has its own special condition because NULL not a value

Combining conditions:
- `AND` (conjunction)
- `OR` (disjunction)
- `NOT` (negation)
- use () to group expressions to make them more readable
	- technically priority hierarchy is `NOT` $\rightarrow$ `AND` $\rightarrow$ `OR`


`ORDER BY` clause:
- used to sort rows of table returned by `SELECT`query
- sort according to particular set of columns
- columns do not have to appear in result
```
SELECT   fName, lName, gender
FROM     Staff
ORDER BY gender ASC, fName DESC
```
- use ASC and DESC for ascending/descending

### Aggregate Functions 

Aggregate functions operate on a **single column** and return a **single value**

| Function   | Operation                                   |
| ---------- | ------------------------------------------- |
| SUM        | **sum** of (numeric) values in column       |
| AVG        | **average** value of column                 |
| MIN        | **smallest** value in column                |
| MAX        | **largest** value in column                 |
| COUNT      | **number of values** in column (excl. NULL) |
| COUNT($*$) | **number of rows** in table (incl. NULL)    |
```EXAMPLES 
SELECT  AVG(salary) FROM Staff
SELECT  SUM(salary) FROM Staff
SELECT  SUM(salary)/COUNT(salary) FROM Staff
SELECT  COUNT(DISTINCT salary) FROM Staff
```

To find average salary of managers:
```
SELECT AVG(salary) AS managerSalary
FROM Staff
WHERE position = 'Manager'
```

### GROUP BY Clause

Used in **combination** with aggregate functions
- first groups rows by attribute(s)
- aggregate functions applied to each group separately
- e.g. "List average salary **separately** for different **positions** and order result in descending order"
```
SELECT    position, AVG(salary)
FROM      Staff
GROUP BY  position
ORDER BY  AVG(salary) DESC
```
![[Screenshot 2025-05-16 at 15.21.05.png]]

### JOIN

Combining **multiple tables** into a single query
- can combine all combinations of all rows
- can append one table to another


> [!success] Types of Joins (Inner and Outer)
> 1. `[INNER] JOIN ON <matching_criterion>`: all matching combinations
> 2. `LEFT [OUTER] JOIN ON <matching_criterion>`: all matching combinations + entire left table
> 3. `RIGHT [OUTER] JOIN ON <matching_criterion>`: all matching combinations + entire right table
> 4. `FULL [OUTER] JOIN ON <matching_criterion>`: all matching combinations + missing records from both tables (don't combine, fill other table with NULL row)
> 
> ![[Screenshot 2025-05-16 at 16.21.28.png]]

### Inner Join 

Without JOIN:
```
SELECT  *
FROM    Staff, Branch 
WHERE   Staff.branchNo = Branch.branchNo
```

With JOIN ON:
```
SELECT  *
FROM    Staff  JOIN  Branch  ON  Staff.branchNo = Branch.branchNo
```
- equality of attributes with same name is a **natural** join.

### Outer Join 

Does an inner join first, and then adds the extra rows from the chosen (left/right/both) table(s).

Left join example:
```
SELECT   S1.fName, S1.lName, S1.salary, S2.fName, S2.lName, S2.salary
FROM     Staff S1 LEFT JOIN Staff S2
ON       S1.salary > S2.salary
ORDER BY S1.salary DESC, S2.salary DESC 
```
![[Screenshot 2025-05-16 at 16.30.09.png]]

Right join example:
```
SELECT   S1.fName, S1.lName, S1.salary, S2.fName, S2.lName, S2.salary
FROM     Staff S1 RIGHT JOIN Staff S2
ON       S1.salary > S2.salary
ORDER BY S1.salary DESC, S2.salary DESC 
```
![[Screenshot 2025-05-16 at 16.30.39.png]]

### Subqueries

**Reusing query results** in another query.
- a **single-value** (scalar) subquery (1 col, 1 row)
```
SELECT COUNT(*) AS myCount
FROM   PropertyForRent
WHERE  rent > 350
```
- a **multi-value** subquery (1 col, $*$ rows)
```
SELECT staffNo
FROM   Staff
WHERE  position = 'Manager'
```
- a **tabular** subquery ($*$ cols, $*$ rows)
```
SELECT clientNo, viewDate
FROM   Viewing
WHERE  propertyNo='PG4' AND comment IS NULL
```

In a multi-value subquery, can use `ANY` or `ALL` for comparisons
- used as an argument to a `WHERE` clause to allow nested queries

### Data Manipulation Language (DML)

Commands for modifying data in DB:
- **insert new rows** into existing table
```
INSERT INTO TableName [(columnList)]
VALUES      (valueList)
```
- **modify existing data** in a table
```
UPDATE  TableName
SET     columnName=dataValue [, ...]
[ WHERE condition ]
```
- **delete rows** from existing table
```
DELETE FROM TableName
[ WHERE     condition ]
```

`INSERT`:
- columnList is optional
	- if not specified, columns enumerated in creation order 
	- if specified, omitted columns NULL 
	- if specified, valueList must match 1-to-1 with columnList

`UPDATE`:
- `WHERE` is optional
	- if specified, only rows satisfying condition updated
	- if not specified, all rows updated
- dataValue(s) must be compatible with corresponding data type(s)

`DELETE`:
- `WHERE` is optional
	- if specified, only rows satisfying condition deleted
	- if not specified, all rows deleted
- does not delete the table

### Data Definition Language (DDL)

Commands for defining data in DB:
- `CREATE`: **Create** new table/relation and define schema
	- assign name to table/relation
	- define names and domains of columns/attributes
- `ALTER`: **Change** relation schema (table structure)
	- if design error or design change
- `DROP`: **Delete** entire table
- `CREATE VIEW`: **Define a view**
	- **virtual** table/relation that appears to user
	- derived from query on the "real table"

### SQL Domain Types 

Main:

| Domain Type  | Description                                                                                                                |
| ------------ | -------------------------------------------------------------------------------------------------------------------------- |
| CHAR(n)      | character string of fixed length n                                                                                         |
| VARCHAR(n)   | character string variable length, max length n                                                                             |
| BIT(n)       | bit string of fixed length n                                                                                               |
| INTEGER      | large positive/negative integer values                                                                                     |
| SMALLINT     | small positive/negative integer values (up to +/-32767)                                                                    |
| NUMERIC(p,d) | decimal number with at most $p$ (precision) total digits and $d$ (scale) total decimal digits (digits after decimal point) |
Can create **custom** domain types:
- rename existing type:
```
CREATE DOMAIN Postcode AS VARCHAR(8)
```
- add additional constraints:
```
CREATE DOMAIN GenderType AS CHAR(1)
CHECK  (VALUE IN ('M','F','O'))
```
- more complex (nested) definitions:
```
CREATE DOMAIN StaffNumber AS VARCHAR(5)
CHECK  (VALUE IN (SELECT staffNo FROM Staff))
```

### Integrity and Referential Constraints 

Can specify constraints when creating table:
- `PRIMARY KEY`, `FOREIGN KEY`

Can specify what to do with foreign key when primary key updated/deleted:
- `ON UPDATE`: what to do when primary key updated
- `ON DELETE`: what to do when primary key deleted

| Action option | Description                                            |
| ------------- | ------------------------------------------------------ |
| CASCADE       | if update, update foreign key. if delete, delete tuple |
| SET NULL      | set foreign key to NULL                                |
| SET DEFAULT   | set foreign key to default value                       |
| NO ACTION     | do nothing (dangerous choice!)                         |

### Creating a Table 

SQL relation defined using `CREATE TABLE` command:
```
CREATE TABLE TableName(
	Attribute Domain [NOT NULL | UNIQUE | ...]
	[, ...]
	[ # integrity and referential constraints]
)
```
- first `DROP TABLE TableName(...)`
	- `RESTRICT`: drop rejected if other objects' existence depends upon existence of TableName
	- `CASCADE` (default): drop **forced** and dependent objects **dropped recursively**

Full example:
```
DROP TABLE Person CASCADE;  

CREATE TABLE Person(  
	name VARCHAR(30) NOT NULL UNIQUE,  
	passport INTEGER,  
	ssn INTEGER,  
	age SHORTINT,  
	gender GenderType,  
	married BIT(1) DEFAULT 0,  
	PRIMARY KEY (ssn),  
	FOREIGN KEY (passport) REFERENCES PassportTable(id)  
				ON DELETE SET NULL  
				ON UPDATE CASCADE  
);
```

### Altering a Table 

Used to change schema of a relation:
- add new attributes
```
ALTER TABLE Person ADD salary INTEGER
```
- remove attributes:
```
ALTER TABLE Person DROP married CASCADE
```
- change attribute characteristics:
```
ALTER TABLE Person ALTER gender SET DEFAULT 'F'
```

### Defining Views

**View** is a table such that:
- derived from other table(s)
- not physically stored but computed on demand

Main use:
- presenting same info differently to different users 
- simplify complex queries 

Example: A view that depends on two tables:
```
Person(name, city)
Purchase(buyer, seller, product, shop)

CREATE VIEW DurhamView AS
SELECT buyer, seller product, shop
FROM   Person, Purchase
WHERE  Purchase.buyer = Person.name AND Person.city = 'Durham'
```
- creates virtual table: "purchases by people who live in Durham"
- `DurhamView(buyer, seller, product, shop)`

### Querying a View

Views can be queried
- "find all names of Durham citizens who bought shoes, and the name of the shop"
```
SELECT name, shop
FROM DurhamView, Product
WHERE DurhamView.product = Product.name AND Product.category = 'shoes'
```
- views computed on demand therefore **slower**
- queries on views translated into queries on original table(s)