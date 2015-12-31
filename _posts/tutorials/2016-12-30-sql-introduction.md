---
layout: post
title:  "Hands on SQL introduction/ tutorial"
categories: introduction 
---

Orginally created by Darrell Aucoin in conjuection with the Stats Club, find the [original here](https://github.com/uWaterlooDataTeam/IntroSQL/wiki).

## Installation of SQLite Browser


[SQLite Browser webpage](http://sqlitebrowser.org/)

### Windows

Download and install the file below

[Windows download](https://github.com/sqlitebrowser/sqlitebrowser/releases/download/v3.5.1/sqlitebrowser-3.5.1-win32.exe)

### Mac

Download and install the package below

[Mac download](https://github.com/sqlitebrowser/sqlitebrowser/releases/download/v3.5.1/sqlitebrowser-3.5.1.dmg)

### Ubuntu and Linux Mint

In terminal execute the following command

```
sudo apt-get install sqlitebrowser
```

### Get the material  

1. Go to https://github.com/NormallySane/IntroSQL
2. Download [zip
file](https://github.com/NormallySane/IntroSQL/archive/master.zip)
    ![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/IntroSQLGithub.png)
3. Unzip downloaded file in your preferred directory

### Using SQLite Browser

1. Open SQLite browser
2. Open `stats_club.db` database file in the downloaded directory
3. Click on 'Execute SQL' tab
    1. Open SQL file `IntroSQL_Presentation1.sql` file in the downloaded directory, `IntroSQL_Presentation2.sql` for second presentation.
    2. Follow along with file, executing statement as topics dictate
4. Content of the talk is on https://github.com/NormallySane/IntroSQL/wiki (open in your favorite browser)


- SQLite browser is a great tool for learning SQLite and SQL in general

### Features of SQLite Browser

- Lets you see the data structure of tables in the database

![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/dataStructure.png)

- Explore the data entered in tables

![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/exploreData.png)

- Execute SQL statements and see results

![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/executeSQL.png)

- Easily construction tables from files

![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Import_tables.png)

- If the table is already created it will just import the data into the table,
otherwise it will create a new table

![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/import_tables2.png)

- SQLite functionality can also be extended by [various user created
extensions](http://www.sqlite.org/contrib)

# Motivation

__Q:__ Why learn a database lanugage?

- Data is rarely tidy as they are in many stats courses
- Most of the time the data we want (outside of assignments) is in a database

__Q:__ Why learn SQL?

- One of the most popular data analysis tools ([O'Reilly Data Scientist Survey
for 2014](http://www.oreilly.com/data/free/2014-data-science-salary-survey.csp))
- One of the most in-demand skills for 2014
([Workopolis](http://www.workopolis.com/content/advice/article/year-in-review-
the-most-in-demand-jobs-of-2014-and-the-fastest-declining-
occupations?CID=721:19L:14946))
- SQL not only can retrieve data, but can slice, dice and transform the data as
needed

__Q:__ What is SQL?

- A programming language allowing multiple concurrent users storing,
manipulating, and querying data stored in a relational database.
- Data does not necessary have to fit into memory.

__Q:__ Why use SQLite?

- Very easy to install
- Easy to share (database is a single file)
- Good  SQL language to practice with (can easily use it to preprocess data for
kaggle competitions)

## Different Implementations of SQL

__[MySQL](http://www.mysql.com/):__ Highly popular open source SQL
implementation.

__[PostgreSQL](http://www.postgresql.org/):__ Open source SQL designed around
letting users create User Defined Functions (UDF).

__[SQLite](http://www.sqlite.org/):__ Open sources light weight SQL usually used
as an embedded database for applications (web browsers, mobile applications,
etc.), or light to medium traffic websites. Database is saved as a single file
and __only allows one writer at a time__. Various OS's have SQLite preinstalled
(type `sqlite3` in terminal for mac)

__[Oracle](http://www.oracle.com/ca-en/database/overview/index.html):__ SQL
implementation produced and marketed by Oracle Corporation.

__[Microsoft SQL Server](http://www.microsoft.com/en-ca/server-cloud/products
/sql-server/):__ SQL implementation developed by Microsoft.

__[DB2](http://www-01.ibm.com/software/data/db2/):__ SQL developed by IBM. The
database used by University of Waterloo.

# Relational Databases

__Relational Database:__ A relational database is a system organized in tables
containing records (rows) related to other records in other tables. Each entity
having attributes (columns also called fields) which give additional information
on an entity.
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/RelationalDatabase.png)
</center>

__Field, Attribute (Column)__: An individual piece of data stored in a table.

__Record (Row):__ A tuple of columns describing an entity or action of an
entity.

__Table:__ A collection of rows. Usually in reference a persistent table saved
permanently to memory

__Result set:__ A non-persistent table, usually the result of a query.

__(Virtual) View:__ A named query saved into memory and performed whenever it is
named. Some SQL servers have materialized views that permanently save the data
for faster access.

__Subquery:__ A query that returns a table to another query.

__Primary key:__ A tuple of columns that uniquely define each row in a table.

__Foreign key:__ A tuple of columns identifying a relationship to another table.

## The E-R Model

The E-R (entity-relationship) Model is an _analysis tool_ for relational
databases.
__E__ refers to _entity_: An object
__R__ refers to _relationship_: As in how objects relate to each other.

Each entity has properties associated with every instance of an object.
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/ER_Model.png)
</center>

Objects are related to each other through relationships:
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/ER_Model2.png)
</center>

## E-R Relationships

1. __One to one relationships:__ For every instance of object A, there are
exactly one instance of object B.
    - Every student has exactly one quest account
2. __One to many relationships:__ For every instance of object A, there are an
indeterminate number of instances of object B.
    - A single course section has many students

3. __Many to one relationships:__ For many instances of object A, there are a
single instance of object B.
    - Many students are enrolled in a course section

4. __Many to many relationships:__ For many instances of object A, there are a
many possible instances of object B.
    - Many students take many courses

## Normalization

__Database Normalization__ is a process in relational databases to minimize
redundacy. Data can be constructed so that additions, deletions, and
modifications can be made in just one table.

Data goes through three forms until it is fully utilizied by a  relational
database:

1. __First Normalized Form:__ Each attribute contains only atomic values and
only a single value from that domain. i.e. The data is in the form of a table
with no merged columns or rows.
2. __Second Normalized Form:__ Each attribute in the table is dependent on the
entity it is describing (dependent on the primary key).
3. __Third Normalized Form:__ All non-primary key attributes are not determined
by any other non-primary key attributes.

__Example:__ For each event for Stats Club we have:
1. a list of attendies along with some basic information (email, ect.),
2. the event's name, type (social or education), the roles for Stats Club execs
for the event, time and location of the event, and a budget,
3. as well as a list of expenses for the event

A report of the event would look something like:
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Event_report.png)
</center>

We first need to tabulate the data:
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Event_report_table.png)
</center>
However this is not enough, the data is not in a form that can be easily
recognized by computers.
- How do you add new events?
- What about members that attend multiple events?
    - that attend no events?

## 1st Normalization

__First Normalized Form:__ Each attribute contains only atomic values and only a
single value from that domain

__Example:__ To bring the data into 1st normalized form we need to break the
table into two tables: Event, and Expenses:

<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Event_report_table_1st.png)
</center>

<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Event_report_table_1st.png)
</center>
- This contains all of the information before but is more organized for the
computers to deal with
- Still not enough, a mispelling of an event or type could make the database
think there is a new event

## 2nd Normalization

__Second Normalized Form:__ Each attribute in the table is dependent on the
entity it is describing (dependent on the primary key).

__Example:__ To bring the data into 2nd normalized form, we need to break the
Event table again.
Let's break the table so we get important description of the events (name, type,
presenter, organizer, etc.) and a list of members that attended each event.

<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Event_report_table_2nd.png)
</center>

<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Event_report_table_2nd.png)
</center>
- Attendance is 2nd normalized form if we consider the primary key as the tuple
of event and quest ID.
- Attendance still has redundant information, several members can attend
multiple events or none at all

## 3rd Normalization

__Third Normalized Form:__ All non-primary key attributes are not determined by
any other non-primary key attributes.

__Example:__ The information on each member (name, email, etc.) is not
determined by the event. We need to break the attendance table to bring into 3rd
normalized form: attendance and members.

<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Event_report_table_3rd.png)
</center>

## Primary Keys and Foriegn Keys

We can reconstruct the orignal table by joining tables, foreign keys with what
they reference (primary keys).
- We can only construct an instance of a foreign keys if their is already an
instance of their reference
    - i.e. the set of foreign keys for one table is a subset of the primary keys
they reference

__Primary key:__ A tuple of columns that uniquely define each row in a table.
(Red items below)
__Foreign key:__ A tuple of columns identifying a relationship to another table.
(Blue items below)
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/primary_keys.png)
</center>

## Quiz: Normalization

Normalize the following table:

| Student Name | Quest ID | Course | Description | Section |
|--------------|----------|--------|-------------|---------|
| | | | | |

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-normalization)

## Relational Algebra Operations

__Projection:__ Returns a subset of columns.

__Selection:__ Returns only entities where some condition is true.

__Rename:__ Rename an attribute.

__Natural Join:__ Tuples from one table is joined to tuples from another table
based on common attributes (at least one column with the same name and possible
values is common between them)

Θ__-Join and Equijoin:__ Join tuples from two different tables where some binary
condition (Θ = {≥, ≤, >, <, =}) between two tables attributes is true. When Θ is
=, the join is called an equijoin.


__Set Operations:__ Set theory's unions, set difference, and cartesian product
of tuples performed on tuples of different tables.

## Quiz: Relational Algebra

__Q1:__ What kind of operation is performed on the following tables?
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/quiz2a.png)
</center>

__Q2:__ What kinds of joins can peform on tables?

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-relational-algebra)

## Constraints

Constraints limit what can be entered into fields in a table and help ensure
encapsulation:

__PRIMARY KEY constraints__  Uniquely identifies each record in a table (quickly
referencing it)

__FOREIGN KEY constraints__ Points to a PRIMARY KEY of another table, enabling
them to easily join them

__CHECK constraints__ Limits the range of values that a field can take.

__UNIQUE constraints__ Enforces uniqueness on an field (column).

__NOT NULL constraints__  Enforces a field to always contain a value.

- We can also create indexes for fields making them easily searchable

# SQL Language

- Case does not matter, for presentation purposes UPPER CASE is used for SQL key
words
- SQL statements are processed as a whole (ignoring white space and new lines)
and ends with a ';'

- We will be used a database based on Stats Club, supplied with fake data:
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/StatClubTables.png)
</center>

## Data Types

In SQLite3, there are 5 basic data types:

1. __INTEGER__ The value is a signed integer.

2. __REAL__ The value is a floating point value, stored as an 8-byte IEEE
floating point number.

3. __TEXT__ The value is a text string.

4. __BLOB__ The value is a blob of data, stored exactly as it was input.

5. __NUMERIC__ May contain integer or real values. The data is stored as text
but converted as necessary.

## SQL General Data Types

- Different implementations of SQL uses different datatypes but there are some
[general commonalities](http://www.w3schools.com/sql/sql_datatypes_general.asp):

| Data type | Description |
|-----------|-------------|
| CHAR(n) | Character string. Fixed length n |
| VARCHAR(n) | Character string.  Variable length <= n |
| BINARY(n) | Binary string. Fixed length n |
| BOOLEAN | TRUE or FALSE values |
| VARBINARY(n) | Binary string. Variable length <= n |
| INTEGER(p) | Integer numerical (no decimal). Precision p |
| SMALLINT | Integer numerical (no decimal). Precision 5 |
| INTEGER | Integer numerical (no decimal). Precision 10 |
| BIGINT | Integer numerical (no decimal). Precision 19 |
| DECIMAL(p,s) | Exact numerical. precision p, scale s |
| NUMERIC(p,s) | Exact numerical. precision p, scale s |
| FLOAT(p) | Floating point number. mantissa precision p |
| REAL | Approximate numerical. Mantissa percision 7 |
| FLOAT | Approximate numerical. Mantissa percision 16 |
| DATE | Stores year, month, and day values |
| TIME | Stores hour, minute, and second values |
| TIMESTAMP | Stores year, month, day, hour, minute, and second values |

## NULL Values

__NULL__ A NULL can be thought of as an unknown value.
- Any datatype can have NULL values
- if either x or y is NULL:  
<center>
x+y => NULL  
x>y => NULL
</center>

SQL uses a three-value logic system: TRUE, FALSE, NULL:

| AND | TRUE | FALSE | NULL |
|-----|------|-------|------|
| TRUE | T | F | NULL |
| FALSE | F | F | F |
| NULL | NULL | F | NULL |

| OR | TRUE | FALSE | NULL |
|-----|------|-------|------|
| TRUE | T | T | T |
| FALSE | T | F | NULL |
| NULL | T | NULL | NULL |

| NOT | TRUE | FALSE | NULL |
|-----|------|-------|------|
|  | F | T | NULL |

## Projection (SELECT Clause)

__SELECT Statement:__ The SELECT statement returns a table of values (sometimes
empty) as specified in the statement.

__SELECT Clause:__ The SELECT clause of a SELECT statement specifies the columns
for the result set.   

```sql
SELECT col1, col2, ...
FROM table_name;
```

- We can also specify all columns from a table

```sql
SELECT *
FROM table_name;
```

- If we leave out '`FROM table`' we are effectively taking from an empty table

In SELECT clauses, we can specify more than just columns from a table:
__Literials:__ Strings, numbers that are repeated for every row
__Expressions:__ Expressions of columns/literals
__Functions:__ Built in functions in SQL (ROUND(), etc.)
__User Defined Functions:__ Functions that a user can create within SQL to run

__Example:__ Let's try something simple: some literials and a calculation of `1
/ 2`

```sql
SELECT 1, 2, 'this is a string', 1/2;
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>1</th>
      <th>2</th>
      <th>'this is a string'</th>
      <th>1/2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> 1</td>
      <td> 2</td>
      <td> this is a string</td>
      <td> 0</td>
    </tr>
  </tbody>
</table>
</div>



__Q:__ What happened here?

__A:__ Since 1 and 2 are both integers, the expression 1/2 returns an integer.
To get 0.5, we need to use a real number (a FLOAT).

```sql
SELECT 1, 2, 'this is a string', 1/2, 4/2, 5/2, 1/2., 1./2, 1/CAST(2 AS FLOAT);
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>1</th>
      <th>2</th>
      <th>'this is a string'</th>
      <th>1/2</th>
      <th>4/2</th>
      <th>5/2</th>
      <th>1/2.</th>
      <th>1./2</th>
      <th>1/CAST(2 AS FLOAT)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> 1</td>
      <td> 2</td>
      <td> this is a string</td>
      <td> 0</td>
      <td> 2</td>
      <td> 2</td>
      <td> 0.5</td>
      <td> 0.5</td>
      <td> 0.5</td>
    </tr>
  </tbody>
</table>
</div>



SQL statements ignore white spaces and new lines, the statement is only
processed when after it sees ';'

__Example:__ The following two statements produce the same table.

```sql
SELECT 1, 2, 'this is a string', 1/2;
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>1</th>
      <th>2</th>
      <th>'this is a string'</th>
      <th>1/2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> 1</td>
      <td> 2</td>
      <td> this is a string</td>
      <td> 0</td>
    </tr>
  </tbody>
</table>
</div>



```sql
SELECT 1,
2,
             'this is a string',   1/2;
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>1</th>
      <th>2</th>
      <th>'this is a string'</th>
      <th>1/2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> 1</td>
      <td> 2</td>
      <td> this is a string</td>
      <td> 0</td>
    </tr>
  </tbody>
</table>
</div>



## SQL Functions

There are many functions in SQLite and each implementation of SQL have different
functions. Here are some random functions in SQLite:   


| Function | Description |  
|----------|-------------|  
| __ABS(col)__ | Absolute value of numeric column |  
| __LENGTH(col)__ | Return length of string column |
| __LOWER(col)__ | Return the string column in lower case |
| __UPPER(col)__ | Return the string column in upper case |
| __RANDOM()__ |        A pseudo-random integer between -9223372036854775808 and +9223372036854775807 |  


```sql
SELECT ABS(-8), LENGTH('This is a String'), LOWER('ThIS Is A StRiNg'), RANDOM();
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ABS(-8)</th>
      <th>LENGTH('This is a String')</th>
      <th>LOWER('ThIS Is A StRiNg')</th>
      <th>RANDOM()</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> 8</td>
      <td> 16</td>
      <td> this is a string</td>
      <td> 1085249690759383083</td>
    </tr>
  </tbody>
</table>
</div>



There are many more [core functions](http://www.sqlite.org/lang_corefunc.html)
within SQLite.


## Quiz: SELECT Clause

Calculate the average of 2 random numbers.



__Q:__ What is the upper and lower case for the string __'UPPER or lower'__?

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-select-clause)

## FROM Clause

__FROM Clause:__ Specifies the table: either a persistant table, or a result
set: a join of two or more tables or a subquery or some combination of the two.  

```sql
SELECT col1, col2, ...
FROM table_name;
```

__Example:__ What are the names, type, times and locations for Stats Club?

```sql
SELECT name, type, start_time, end_time, location
FROM event;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>start_time</th>
      <th>end_time</th>
      <th>location</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>             BOT</td>
      <td>      social</td>
      <td> 2015-01-28 19:00:00</td>
      <td> 2015-01-28 22:00:00</td>
      <td>   C &amp; D</td>
    </tr>
    <tr>
      <th>1</th>
      <td>             EOT</td>
      <td>      social</td>
      <td>                None</td>
      <td>                None</td>
      <td>    None</td>
    </tr>
    <tr>
      <th>2</th>
      <td> Intro to Hadoop</td>
      <td> educational</td>
      <td>                None</td>
      <td>                None</td>
      <td>    None</td>
    </tr>
    <tr>
      <th>3</th>
      <td>    Intro to SQL</td>
      <td> educational</td>
      <td> 2015-02-05 18:00:00</td>
      <td> 2015-02-05 19:30:00</td>
      <td> MC-3003</td>
    </tr>
    <tr>
      <th>4</th>
      <td>       Prof Talk</td>
      <td> educational</td>
      <td>                None</td>
      <td>                None</td>
      <td>    None</td>
    </tr>
    <tr>
      <th>5</th>
      <td>  Intro to SQL 2</td>
      <td> educational</td>
      <td>                None</td>
      <td>                None</td>
      <td>    None</td>
    </tr>
    <tr>
      <th>6</th>
      <td>     Prof Talk 2</td>
      <td> educational</td>
      <td>                None</td>
      <td>                None</td>
      <td>    None</td>
    </tr>
    <tr>
      <th>7</th>
      <td>     Prof Talk 3</td>
      <td> educational</td>
      <td>                None</td>
      <td>                None</td>
      <td>    None</td>
    </tr>
  </tbody>
</table>
</div>



## Quiz: FROM Clause

__Q:__ Who are the execs for Stats Club, and what are their positions, and
emails?
- Projection of name, position, and email from the table exec

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-from-clause)

## Aggregate Functions

__Aggregate Functions:__ Takes in the columns of a table and aggregates over the
entries.

| Function | Return value |
|----------|--------------|
| AVG(column) | Average of non-null values |
| COUNT(column) | Count of non-null values |
| MAX(column) | Maximum of values |
| MIN(column) | Minimum of values |
| SUM(column) | Sum of values |
| GROUP_CONCAT(column) | Concatenation of column strings |

- There are more aggregate functions for other implementations of SQL

More detailed descriptions of the aggregate functions within SQLite can be found
[here](http://www.sqlite.org/lang_aggfunc.html).

```sql
SELECT COUNT( 12 ), COUNT('ssdf'), COUNT(NULL), SUM(23), SUM(0), SUM(NULL),
  AVG(0), AVG(NULL);
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>COUNT( 12 )</th>
      <th>COUNT('ssdf')</th>
      <th>COUNT(NULL)</th>
      <th>SUM(23)</th>
      <th>SUM(0)</th>
      <th>SUM(NULL)</th>
      <th>AVG(0)</th>
      <th>AVG(NULL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> 1</td>
      <td> 1</td>
      <td> 0</td>
      <td> 23</td>
      <td> 0</td>
      <td> None</td>
      <td> 0</td>
      <td> None</td>
    </tr>
  </tbody>
</table>
</div>



Lets work with some aggregate functions with the table `example` below:


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>number</th>
      <th>floating</th>
      <th>string</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>    1</td>
      <td> 23.23</td>
      <td>         this</td>
    </tr>
    <tr>
      <th>1</th>
      <td> 3232</td>
      <td>-21.23</td>
      <td>           is</td>
    </tr>
    <tr>
      <th>2</th>
      <td>   11</td>
      <td> -2.00</td>
      <td>            a</td>
    </tr>
    <tr>
      <th>3</th>
      <td>  -23</td>
      <td> 54.00</td>
      <td>       string</td>
    </tr>
    <tr>
      <th>4</th>
      <td>    2</td>
      <td>   NaN</td>
      <td> concatenated</td>
    </tr>
  </tbody>
</table>
</div>



```sql
SELECT COUNT(*), COUNT(string), COUNT(floating), AVG(number), SUM(number),
GROUP_CONCAT(string, ' ')
FROM example;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>COUNT(*)</th>
      <th>COUNT(string)</th>
      <th>COUNT(floating)</th>
      <th>AVG(number)</th>
      <th>SUM(number)</th>
      <th>GROUP_CONCAT(string, ' ')</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> 5</td>
      <td> 5</td>
      <td> 4</td>
      <td> 644.6</td>
      <td> 3223</td>
      <td> this is a string concatenated</td>
    </tr>
  </tbody>
</table>
</div>



## DISTINCT Prefix

In the SELECT clause we can specify to return only distinct tuples of columns  

```sql
SELECT DISTINCT col1, col2, ...
FROM table_name;
```  

- We can also use DISTINCT within aggregate functions making them only aggregate
over distinct entries  

```sql
SELECT aggregate_function(DISTINCT column_name)
FROM table_name;
```

__Example:__ What events have members attended?
- What are the distinct events where at least one member attended?

```sql
SELECT DISTINCT event
FROM attendance;
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>event</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>    Intro to SQL</td>
    </tr>
    <tr>
      <th>1</th>
      <td>             BOT</td>
    </tr>
    <tr>
      <th>2</th>
      <td>             EOT</td>
    </tr>
    <tr>
      <th>3</th>
      <td> Intro to Hadoop</td>
    </tr>
    <tr>
      <th>4</th>
      <td>  Intro to SQL 2</td>
    </tr>
    <tr>
      <th>5</th>
      <td>       Prof Talk</td>
    </tr>
    <tr>
      <th>6</th>
      <td>     Prof Talk 2</td>
    </tr>
  </tbody>
</table>
</div>



## Quiz: DISTINCT

__Q:__ What are the __distinct__ majors of Stats Club members?


__Q:__ How many __distinct__ majors of Stats Club members are there?

- DISTINCT can be within aggregate functions

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-distinct)

## Alias

### Column Alias

To increase the readability of SQL as well as the result set, we can give
columns new names:  

```sql
SELECT col AS new_name
FROM table_name;
```  

- Column aliases make the final table more readiable and workiable for
subqueries

### Table Alias

We can also give tables new names as well:  

```sql
SELECT table_alias_1.col_name, table_alias_2.col_name, ...
FROM table_1 AS table_alias_1, table_2 AS table_alias_2;
```  

- Very useful when tables have common column names

__Note:__ We can reference what table a column is coming from by a '.'  

```python
table_name.column_name
```

__Example:__ If we give column aliases for the previous table, we make the
result more interpretiable:  

```sql
SELECT COUNT(*) AS num_rows, COUNT(string) AS num_strings,
  COUNT(floating) AS num_float, AVG(number) AS avg_integer,
  SUM(number) AS sum_int, GROUP_CONCAT(string, ' ') AS cat_string
FROM example;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>num_rows</th>
      <th>num_strings</th>
      <th>num_float</th>
      <th>avg_integer</th>
      <th>sum_int</th>
      <th>cat_string</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> 5</td>
      <td> 5</td>
      <td> 4</td>
      <td> 644.6</td>
      <td> 3223</td>
      <td> this is a string concatenated</td>
    </tr>
  </tbody>
</table>
</div>



##  Quiz: Aliases

Perform a query using a table alias, and use this table alias when referencing
the column i.e. `table_alias.column_name`
- This will be really important for bigger, more complicated queries

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-aliases)

## Selection (WHERE Clause)

__WHERE__ clauses filters the result set, removing rows where the condition
returns either FALSE or NULL.

```sql
SELECT col1, col2, ...
FROM table_name
WHERE condition;
```

__Example:__ What Stats Club events are social?

```sql
SELECT name, type, start_time, end_time, location
FROM event
WHERE type = 'social';
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>start_time</th>
      <th>end_time</th>
      <th>location</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> BOT</td>
      <td> social</td>
      <td> 2015-01-28 19:00:00</td>
      <td> 2015-01-28 22:00:00</td>
      <td> C &amp; D</td>
    </tr>
    <tr>
      <th>1</th>
      <td> EOT</td>
      <td> social</td>
      <td>                None</td>
      <td>                None</td>
      <td>  None</td>
    </tr>
  </tbody>
</table>
</div>



## Prediate Operators

| Operator | Description | Example |
|----------|-------------|---------|
| = | Equal to | WHERE gender = 'M' |
| <>, != | Not equal to | WHERE gender <> 'M' |
| > | Greater than | WHERE num > 5 |
| < | Less than | WHERE num < 5 |
| >= | Greater than or equal to | WHERE num >= 5 |
| <= | Less than or equal to | WHERE num <= 5 |
| IS NULL | Value is NULL | WHERE num IS NULL |
| IS NOT NULL | Value is not NULL | WHERE num IS NOT NULL |
| BETWEEN | Between a range | WHERE num BETWEEN 3 AND 5 |
| IN | In a list of values | WHERE num IN (3, 5, 8) |
| LIKE | Pattern Search | WHERE str LIKE 'F%' |
| EXISTS | Subquery have any rows? | WHERE EXISTS (subquery) |

### LIKE Predicate

LIKE predicates

'\_' means a character of any type
'%' means between 0 or more characters of any type

__Example:__ What Stats Club members has a name begining with F?

```sql
SELECT *
FROM member
WHERE name LIKE 'F%';
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>quest_id</th>
      <th>name</th>
      <th>email</th>
      <th>faculty</th>
      <th>major</th>
      <th>paid</th>
      <th>card</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>    fred</td>
      <td>     Fred E. Finch</td>
      <td>    fred@uwaterloo.ca</td>
      <td> Math</td>
      <td> Pure Math</td>
      <td> Y</td>
      <td> Y</td>
    </tr>
    <tr>
      <th>1</th>
      <td> frances</td>
      <td> Frances A. Miller</td>
      <td> frances@uwaterloo.ca</td>
      <td> Math</td>
      <td>     Stats</td>
      <td> Y</td>
      <td> Y</td>
    </tr>
  </tbody>
</table>
</div>

### Operator Modifiers

#### ALL, ANY or SOME Operator Modifiers

The operators =, <>, !=, >, <, >=, <= can be used with a list of values and the
operators `ALL` or `ANY / SOME`.

- SQLite does __NOT__ have `ALL` or `ANY / SOME` implemented

__ANY, SOME__ Operator returns true, if operator is true for __any__ value in the
set.


__ALL__ Operator returns true, if operator is true for __all__ values in the set.


```sql
SELECT *
FROM table_name
WHERE column_name < ALL (subquery_returning_one_column);
```

__Example:__ What are the expenses for non-social events? (`ALL`, `ANY`, and `SOME` are not implmented in SQLite)

```sql
SELECT * 
FROM expenses 
WHERE event != ALL (SELECT name 
                    FROM event
                    WHERE type = 'social');
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>event</th>
      <th>expense</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0 </th>
      <td>                   Intro to SQL</td>
      <td>   pizza</td>
      <td> 87.43</td>
    </tr>
    <tr>
      <th>1 </th>
      <td>                   Intro to SQL</td>
      <td>     pop</td>
      <td> 15.34</td>
    </tr>
    <tr>
      <th>2 </th>
      <td>                Intro to Hadoop</td>
      <td>  coffee</td>
      <td> 23.12</td>
    </tr>
    <tr>
      <th>3 </th>
      <td>                Intro to Hadoop</td>
      <td>   water</td>
      <td> 10.23</td>
    </tr>
    <tr>
      <th>4 </th>
      <td>                Intro to Hadoop</td>
      <td>  donuts</td>
      <td> 53.23</td>
    </tr>
    <tr>
      <th>5 </th>
      <td>                Intro to Hadoop</td>
      <td> cookies</td>
      <td> 10.23</td>
    </tr>
    <tr>
      <th>6 </th>
      <td>    Intro to SQL: Basic Queries</td>
      <td> cookies</td>
      <td> 10.23</td>
    </tr>
    <tr>
      <th>7 </th>
      <td>    Intro to SQL: Basic Queries</td>
      <td>  donuts</td>
      <td> 20.34</td>
    </tr>
    <tr>
      <th>8 </th>
      <td>    Intro to SQL: Basic Queries</td>
      <td>     pop</td>
      <td> 21.54</td>
    </tr>
    <tr>
      <th>9 </th>
      <td>    Intro to SQL: Basic Queries</td>
      <td>   water</td>
      <td> 10.52</td>
    </tr>
    <tr>
      <th>10</th>
      <td>                      Prof Talk</td>
      <td>     pop</td>
      <td> 20.31</td>
    </tr>
    <tr>
      <th>11</th>
      <td>                      Prof Talk</td>
      <td>   pizza</td>
      <td> 62.56</td>
    </tr>
    <tr>
      <th>12</th>
      <td>                    Prof Talk 2</td>
      <td>   pizza</td>
      <td> 61.56</td>
    </tr>
    <tr>
      <th>13</th>
      <td>                    Prof Talk 2</td>
      <td>     pop</td>
      <td> 15.65</td>
    </tr>
    <tr>
      <th>14</th>
      <td>                    Prof Talk 3</td>
      <td>   pizza</td>
      <td> 62.45</td>
    </tr>
    <tr>
      <th>15</th>
      <td>                    Prof Talk 3</td>
      <td>     pop</td>
      <td> 13.23</td>
    </tr>
    <tr>
      <th>16</th>
      <td> Intro to SQL: Advanced Queries</td>
      <td> cookies</td>
      <td> 10.23</td>
    </tr>
    <tr>
      <th>17</th>
      <td> Intro to SQL: Advanced Queries</td>
      <td>  donuts</td>
      <td> 20.34</td>
    </tr>
    <tr>
      <th>18</th>
      <td> Intro to SQL: Advanced Queries</td>
      <td>     pop</td>
      <td> 21.54</td>
    </tr>
    <tr>
      <th>19</th>
      <td> Intro to SQL: Advanced Queries</td>
      <td>   water</td>
      <td> 10.52</td>
    </tr>
  </tbody>
</table>
</div>




### AND, OR Operators

A group of filter conditions can be linked together with AND or OR operators.

```sql
SELECT col1, col2, ...
FROM table_name
WHERE (condition1 AND condition2 ) OR condition3;
```

__Example:__ What Stats Club members has a name with it's second letter as A or
ends in B?

```sql
SELECT name
FROM member
WHERE name LIKE '_a%' OR  name LIKE '%b';
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>      Darrell Aucoin</td>
    </tr>
    <tr>
      <th>1</th>
      <td>    James M. Eddings</td>
    </tr>
    <tr>
      <th>2</th>
      <td>       James A. Foxt</td>
    </tr>
    <tr>
      <th>3</th>
      <td>     Daniel J. Moore</td>
    </tr>
    <tr>
      <th>4</th>
      <td>    Nancy P. Jackson</td>
    </tr>
    <tr>
      <th>5</th>
      <td>    Ralph L. Waldrop</td>
    </tr>
    <tr>
      <th>6</th>
      <td> Tameika M. McMaster</td>
    </tr>
    <tr>
      <th>7</th>
      <td>    Janelle T. Smith</td>
    </tr>
    <tr>
      <th>8</th>
      <td>          Ruben Lamb</td>
    </tr>
    <tr>
      <th>9</th>
      <td>   Patrick Robertson</td>
    </tr>
  </tbody>
</table>
</div>



## Quiz: Filtering (WHERE Clause)

__Q:__ What events for Stats Club are introductory talks?
- Introductory talk names start with 'Intro'



__Q:__ What Stats Club members have their first name starting with a letter
__BETWEEN__ A and G?

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-filtering-where-clause)

## GROUP BY Clause

- GROUP BY clause groups the table by a column (or tuple of columns) and applies
a function to each group
    - In the SELECT portion of the statement, you can only list the grouped
column(s) and aggregate functions on them.
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/Group By.png)
</center>

```sql
SELECT col1, col2, ..., aggregate_function
FROM table_name
GROUP BY col1, col2, ...;
```

## Aggregate Functions

Recall:
__Aggregate Functions:__ Takes in the columns of a table and aggregates over the
entries.
- If we use a GROUP BY clause, the aggregation will be over those groups

| Function | Return value |
|----------|--------------|
| AVG(column) | Average of non-null values |
| COUNT(column) | Count of non-null values |
| MAX(column) | Maximum of values |
| MIN(column) | Minimum of values |
| SUM(column) | Sum of values |
| GROUP_CONCAT(column) | Concatenation of column strings |

- There are more aggregate functions for other implementations of SQL

__Example:__ What are the number of each type of event for Stats Club?

```sql
SELECT type, COUNT(*) AS num_events
FROM event
GROUP BY type;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>num_events</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> educational</td>
      <td> 6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>      social</td>
      <td> 2</td>
    </tr>
  </tbody>
</table>
</div>



## HAVING Clause

HAVING clauses are very similar to WHERE clauses but can have aggregate function
in their conditions.

You can have a WHERE and HAVING clause in the same statement.

__Example:__ How many Stats Club members are in each major where the major has
at least 2 members?

```sql
SELECT faculty, major, COUNT(*)
FROM member
GROUP BY faculty, major
HAVING COUNT(*) >= 2;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>faculty</th>
      <th>major</th>
      <th>COUNT(*)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td> Math</td>
      <td>      Act Sci</td>
      <td> 10</td>
    </tr>
    <tr>
      <th>1</th>
      <td> Math</td>
      <td> Applied Math</td>
      <td>  2</td>
    </tr>
    <tr>
      <th>2</th>
      <td> Math</td>
      <td>        C &amp; O</td>
      <td>  2</td>
    </tr>
    <tr>
      <th>3</th>
      <td> Math</td>
      <td>           CS</td>
      <td>  3</td>
    </tr>
    <tr>
      <th>4</th>
      <td> Math</td>
      <td>    Pure Math</td>
      <td>  2</td>
    </tr>
    <tr>
      <th>5</th>
      <td> Math</td>
      <td>        Stats</td>
      <td> 14</td>
    </tr>
  </tbody>
</table>
</div>



## GROUP BY with ROLLUP / CUBE

The ROLLUP operator produces a result set where the aggregate function is
applied to each level of the GROUP BY hierachy.
- The ROLLUP operator is __NOT__ implemented in SQLite
- Useful for making reports with totals and subtotals

```sql
SELECT col1, col2, ..., aggregate_function
FROM table_name
GROUP BY col1, col2, ... WITH ROLLUP;
```

__Example:__ What are the number of Stats Club members in each faculty and
major, including subtotals?

```sql
SELECT faculty, major, COUNT(*) AS num_members
FROM member
GROUP BY faculty, major WITH ROLLUP;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>faculty</th>
      <th>major</th>
      <th>num_members</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>  Art</td>
      <td>         Econ</td>
      <td>  1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>  Art</td>
      <td>         None</td>
      <td>  1</td>
    </tr>
    <tr>
      <th>2</th>
      <td> Math</td>
      <td>      Act Sci</td>
      <td> 10</td>
    </tr>
    <tr>
      <th>3</th>
      <td> Math</td>
      <td> Applied Math</td>
      <td>  2</td>
    </tr>
    <tr>
      <th>4</th>
      <td> Math</td>
      <td>        C &amp; O</td>
      <td>  2</td>
    </tr>
    <tr>
      <th>5</th>
      <td> Math</td>
      <td>           CS</td>
      <td>  3</td>
    </tr>
    <tr>
      <th>6</th>
      <td> Math</td>
      <td>    Pure Math</td>
      <td>  2</td>
    </tr>
    <tr>
      <th>7</th>
      <td> Math</td>
      <td>        Stats</td>
      <td> 14</td>
    </tr>
    <tr>
      <th>8</th>
      <td> Math</td>
      <td>         None</td>
      <td> 33</td>
    </tr>
    <tr>
      <th>9</th>
      <td> None</td>
      <td>         None</td>
      <td> 34</td>
    </tr>
  </tbody>
</table>
</div>



Note that for Art and Math in faculty there is a row which has a NULL value.
This is a total for those groups.

There is also one row with NULL values for faculty and major, this is the grand
total of all members.

## Quiz: Aggregation (GROUP BY Clause)

__Q:__ What is the attendance for each Stats Club event?

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-aggregation-group-by-clause)

## Joins

At times, we need information from multiple tables, to do this we need to join
tables together. We can do this several ways:

1. __CROSS JOIN:__ The cartesian product of rows from each table.
2. __INNER JOIN:__ Join two tables on a join-predicate, losing rows when
evaluated false/null.
3. __OUTER JOIN:__ Retains each record for the table(s) even when it has no
matching rows from the other table. The returning table has null values for
missing records.

    1. __LEFT OUTER JOIN:__ Keep each record for first table but not the table
it's joining with.

    2. __RIGHT OUTER JOIN:__ Keep each record for second table but not the table
it's joining with.

    3. __FULL OUTER JOIN:__ Keep all record for all tables.

4. __NATURAL JOIN:__ Tables with the exact same column name and datatype are
joined along that column.

## CROSS JOIN

__CROSS JOIN__ is the cartesian product of two tables  

```sql
SELECT col1, col2, ...
FROM table1 CROSS JOIN table2;
```
- if table1 has n rows and table2 has m rows, then the result set has n * m rows

We can also get a CROSS JOIN by listing the tables seperated by a ','  

```sql
SELECT col1, col2, ...
FROM table1, table2;
```

__Example:__ Suppose we are creating a games tourtament between Stats Club
members where every member play every other member once. How can we create such
a table?

```sql
SELECT m1.name AS Player_1, m2.name  AS Player_2
FROM member AS m1 CROSS JOIN member AS m2;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Player_1</th>
      <th>Player_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0   </th>
      <td>    Darrell Aucoin</td>
      <td>        Darrell Aucoin</td>
    </tr>
    <tr>
      <th>1   </th>
      <td>    Darrell Aucoin</td>
      <td>         Fred E. Finch</td>
    </tr>
    <tr>
      <th>2   </th>
      <td>    Darrell Aucoin</td>
      <td>          Ryan T. Luby</td>
    </tr>
    <tr>
      <th>3   </th>
      <td>    Darrell Aucoin</td>
      <td>       Billy L. Hunter</td>
    </tr>
    <tr>
      <th>4   </th>
      <td>    Darrell Aucoin</td>
      <td>       John J. Oquendo</td>
    </tr>
    <tr>
      <th>5   </th>
      <td>    Darrell Aucoin</td>
      <td> Stephanie R. Matthews</td>
    </tr>
    <tr>
      <th>6   </th>
      <td>    Darrell Aucoin</td>
      <td>    Robert B. Williams</td>
    </tr>
    <tr>
      <th>7   </th>
      <td>    Darrell Aucoin</td>
      <td>    Austin K. Gilliard</td>
    </tr>
    <tr>
      <th>8   </th>
      <td>    Darrell Aucoin</td>
      <td>      James M. Eddings</td>
    </tr>
    <tr>
      <th>9   </th>
      <td>    Darrell Aucoin</td>
      <td>         Elaine S. Ott</td>
    </tr>
    <tr>
      <th>10  </th>
      <td>    Darrell Aucoin</td>
      <td>         James A. Foxt</td>
    </tr>
    <tr>
      <th>11  </th>
      <td>    Darrell Aucoin</td>
      <td>       Daniel J. Moore</td>
    </tr>
    <tr>
      <th>12  </th>
      <td>    Darrell Aucoin</td>
      <td>     Kelly S. Ferguson</td>
    </tr>
    <tr>
      <th>13  </th>
      <td>    Darrell Aucoin</td>
      <td>        Joseph L. Wood</td>
    </tr>
    <tr>
      <th>14  </th>
      <td>    Darrell Aucoin</td>
      <td>      Vivian R. Donley</td>
    </tr>
    <tr>
      <th>15  </th>
      <td>    Darrell Aucoin</td>
      <td>     Frances A. Miller</td>
    </tr>
    <tr>
      <th>16  </th>
      <td>    Darrell Aucoin</td>
      <td>      Mina W. Lawrence</td>
    </tr>
    <tr>
      <th>17  </th>
      <td>    Darrell Aucoin</td>
      <td> Phillip C. Mascarenas</td>
    </tr>
    <tr>
      <th>18  </th>
      <td>    Darrell Aucoin</td>
      <td>        Jeff M. Wright</td>
    </tr>
    <tr>
      <th>19  </th>
      <td>    Darrell Aucoin</td>
      <td>   Deborah D. Helfrich</td>
    </tr>
    <tr>
      <th>20  </th>
      <td>    Darrell Aucoin</td>
      <td>      Nancy P. Jackson</td>
    </tr>
    <tr>
      <th>21  </th>
      <td>    Darrell Aucoin</td>
      <td>     Bobbie D. Mathews</td>
    </tr>
    <tr>
      <th>22  </th>
      <td>    Darrell Aucoin</td>
      <td>      Arnold J. Fuller</td>
    </tr>
    <tr>
      <th>23  </th>
      <td>    Darrell Aucoin</td>
      <td>      Melvin O. Martin</td>
    </tr>
    <tr>
      <th>24  </th>
      <td>    Darrell Aucoin</td>
      <td>      Ralph L. Waldrop</td>
    </tr>
    <tr>
      <th>25  </th>
      <td>    Darrell Aucoin</td>
      <td>  Mildred F. Hottinger</td>
    </tr>
    <tr>
      <th>26  </th>
      <td>    Darrell Aucoin</td>
      <td>   Tameika M. McMaster</td>
    </tr>
    <tr>
      <th>27  </th>
      <td>    Darrell Aucoin</td>
      <td>   Melissa R. Anderson</td>
    </tr>
    <tr>
      <th>28  </th>
      <td>    Darrell Aucoin</td>
      <td>      Janelle T. Smith</td>
    </tr>
    <tr>
      <th>29  </th>
      <td>    Darrell Aucoin</td>
      <td>     Ann W. McLaughlin</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1126</th>
      <td> Patrick Robertson</td>
      <td>       John J. Oquendo</td>
    </tr>
    <tr>
      <th>1127</th>
      <td> Patrick Robertson</td>
      <td> Stephanie R. Matthews</td>
    </tr>
    <tr>
      <th>1128</th>
      <td> Patrick Robertson</td>
      <td>    Robert B. Williams</td>
    </tr>
    <tr>
      <th>1129</th>
      <td> Patrick Robertson</td>
      <td>    Austin K. Gilliard</td>
    </tr>
    <tr>
      <th>1130</th>
      <td> Patrick Robertson</td>
      <td>      James M. Eddings</td>
    </tr>
    <tr>
      <th>1131</th>
      <td> Patrick Robertson</td>
      <td>         Elaine S. Ott</td>
    </tr>
    <tr>
      <th>1132</th>
      <td> Patrick Robertson</td>
      <td>         James A. Foxt</td>
    </tr>
    <tr>
      <th>1133</th>
      <td> Patrick Robertson</td>
      <td>       Daniel J. Moore</td>
    </tr>
    <tr>
      <th>1134</th>
      <td> Patrick Robertson</td>
      <td>     Kelly S. Ferguson</td>
    </tr>
    <tr>
      <th>1135</th>
      <td> Patrick Robertson</td>
      <td>        Joseph L. Wood</td>
    </tr>
    <tr>
      <th>1136</th>
      <td> Patrick Robertson</td>
      <td>      Vivian R. Donley</td>
    </tr>
    <tr>
      <th>1137</th>
      <td> Patrick Robertson</td>
      <td>     Frances A. Miller</td>
    </tr>
    <tr>
      <th>1138</th>
      <td> Patrick Robertson</td>
      <td>      Mina W. Lawrence</td>
    </tr>
    <tr>
      <th>1139</th>
      <td> Patrick Robertson</td>
      <td> Phillip C. Mascarenas</td>
    </tr>
    <tr>
      <th>1140</th>
      <td> Patrick Robertson</td>
      <td>        Jeff M. Wright</td>
    </tr>
    <tr>
      <th>1141</th>
      <td> Patrick Robertson</td>
      <td>   Deborah D. Helfrich</td>
    </tr>
    <tr>
      <th>1142</th>
      <td> Patrick Robertson</td>
      <td>      Nancy P. Jackson</td>
    </tr>
    <tr>
      <th>1143</th>
      <td> Patrick Robertson</td>
      <td>     Bobbie D. Mathews</td>
    </tr>
    <tr>
      <th>1144</th>
      <td> Patrick Robertson</td>
      <td>      Arnold J. Fuller</td>
    </tr>
    <tr>
      <th>1145</th>
      <td> Patrick Robertson</td>
      <td>      Melvin O. Martin</td>
    </tr>
    <tr>
      <th>1146</th>
      <td> Patrick Robertson</td>
      <td>      Ralph L. Waldrop</td>
    </tr>
    <tr>
      <th>1147</th>
      <td> Patrick Robertson</td>
      <td>  Mildred F. Hottinger</td>
    </tr>
    <tr>
      <th>1148</th>
      <td> Patrick Robertson</td>
      <td>   Tameika M. McMaster</td>
    </tr>
    <tr>
      <th>1149</th>
      <td> Patrick Robertson</td>
      <td>   Melissa R. Anderson</td>
    </tr>
    <tr>
      <th>1150</th>
      <td> Patrick Robertson</td>
      <td>      Janelle T. Smith</td>
    </tr>
    <tr>
      <th>1151</th>
      <td> Patrick Robertson</td>
      <td>     Ann W. McLaughlin</td>
    </tr>
    <tr>
      <th>1152</th>
      <td> Patrick Robertson</td>
      <td>     Judith B. Gibbons</td>
    </tr>
    <tr>
      <th>1153</th>
      <td> Patrick Robertson</td>
      <td>            Ruben Lamb</td>
    </tr>
    <tr>
      <th>1154</th>
      <td> Patrick Robertson</td>
      <td>         Dominick Byrd</td>
    </tr>
    <tr>
      <th>1155</th>
      <td> Patrick Robertson</td>
      <td>     Patrick Robertson</td>
    </tr>
  </tbody>
</table>
<p>1156 rows × 2 columns</p>
</div>



However we have have players playing themselves, and rounds with  the same
players in opposite roles. We just need to filter these out.  

```sql
SELECT m1.name AS Player_1, m2.name  AS Player_2
FROM member AS m1 CROSS JOIN member AS m2
WHERE m1.name > m2.name;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Player_1</th>
      <th>Player_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0  </th>
      <td>    Darrell Aucoin</td>
      <td>      Billy L. Hunter</td>
    </tr>
    <tr>
      <th>1  </th>
      <td>    Darrell Aucoin</td>
      <td>   Austin K. Gilliard</td>
    </tr>
    <tr>
      <th>2  </th>
      <td>    Darrell Aucoin</td>
      <td>      Daniel J. Moore</td>
    </tr>
    <tr>
      <th>3  </th>
      <td>    Darrell Aucoin</td>
      <td>    Bobbie D. Mathews</td>
    </tr>
    <tr>
      <th>4  </th>
      <td>    Darrell Aucoin</td>
      <td>     Arnold J. Fuller</td>
    </tr>
    <tr>
      <th>5  </th>
      <td>    Darrell Aucoin</td>
      <td>    Ann W. McLaughlin</td>
    </tr>
    <tr>
      <th>6  </th>
      <td>     Fred E. Finch</td>
      <td>       Darrell Aucoin</td>
    </tr>
    <tr>
      <th>7  </th>
      <td>     Fred E. Finch</td>
      <td>      Billy L. Hunter</td>
    </tr>
    <tr>
      <th>8  </th>
      <td>     Fred E. Finch</td>
      <td>   Austin K. Gilliard</td>
    </tr>
    <tr>
      <th>9  </th>
      <td>     Fred E. Finch</td>
      <td>        Elaine S. Ott</td>
    </tr>
    <tr>
      <th>10 </th>
      <td>     Fred E. Finch</td>
      <td>      Daniel J. Moore</td>
    </tr>
    <tr>
      <th>11 </th>
      <td>     Fred E. Finch</td>
      <td>    Frances A. Miller</td>
    </tr>
    <tr>
      <th>12 </th>
      <td>     Fred E. Finch</td>
      <td>  Deborah D. Helfrich</td>
    </tr>
    <tr>
      <th>13 </th>
      <td>     Fred E. Finch</td>
      <td>    Bobbie D. Mathews</td>
    </tr>
    <tr>
      <th>14 </th>
      <td>     Fred E. Finch</td>
      <td>     Arnold J. Fuller</td>
    </tr>
    <tr>
      <th>15 </th>
      <td>     Fred E. Finch</td>
      <td>    Ann W. McLaughlin</td>
    </tr>
    <tr>
      <th>16 </th>
      <td>     Fred E. Finch</td>
      <td>        Dominick Byrd</td>
    </tr>
    <tr>
      <th>17 </th>
      <td>      Ryan T. Luby</td>
      <td>       Darrell Aucoin</td>
    </tr>
    <tr>
      <th>18 </th>
      <td>      Ryan T. Luby</td>
      <td>        Fred E. Finch</td>
    </tr>
    <tr>
      <th>19 </th>
      <td>      Ryan T. Luby</td>
      <td>      Billy L. Hunter</td>
    </tr>
    <tr>
      <th>20 </th>
      <td>      Ryan T. Luby</td>
      <td>      John J. Oquendo</td>
    </tr>
    <tr>
      <th>21 </th>
      <td>      Ryan T. Luby</td>
      <td>   Robert B. Williams</td>
    </tr>
    <tr>
      <th>22 </th>
      <td>      Ryan T. Luby</td>
      <td>   Austin K. Gilliard</td>
    </tr>
    <tr>
      <th>23 </th>
      <td>      Ryan T. Luby</td>
      <td>     James M. Eddings</td>
    </tr>
    <tr>
      <th>24 </th>
      <td>      Ryan T. Luby</td>
      <td>        Elaine S. Ott</td>
    </tr>
    <tr>
      <th>25 </th>
      <td>      Ryan T. Luby</td>
      <td>        James A. Foxt</td>
    </tr>
    <tr>
      <th>26 </th>
      <td>      Ryan T. Luby</td>
      <td>      Daniel J. Moore</td>
    </tr>
    <tr>
      <th>27 </th>
      <td>      Ryan T. Luby</td>
      <td>    Kelly S. Ferguson</td>
    </tr>
    <tr>
      <th>28 </th>
      <td>      Ryan T. Luby</td>
      <td>       Joseph L. Wood</td>
    </tr>
    <tr>
      <th>29 </th>
      <td>      Ryan T. Luby</td>
      <td>    Frances A. Miller</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>531</th>
      <td>     Dominick Byrd</td>
      <td>      Daniel J. Moore</td>
    </tr>
    <tr>
      <th>532</th>
      <td>     Dominick Byrd</td>
      <td>  Deborah D. Helfrich</td>
    </tr>
    <tr>
      <th>533</th>
      <td>     Dominick Byrd</td>
      <td>    Bobbie D. Mathews</td>
    </tr>
    <tr>
      <th>534</th>
      <td>     Dominick Byrd</td>
      <td>     Arnold J. Fuller</td>
    </tr>
    <tr>
      <th>535</th>
      <td>     Dominick Byrd</td>
      <td>    Ann W. McLaughlin</td>
    </tr>
    <tr>
      <th>536</th>
      <td> Patrick Robertson</td>
      <td>       Darrell Aucoin</td>
    </tr>
    <tr>
      <th>537</th>
      <td> Patrick Robertson</td>
      <td>        Fred E. Finch</td>
    </tr>
    <tr>
      <th>538</th>
      <td> Patrick Robertson</td>
      <td>      Billy L. Hunter</td>
    </tr>
    <tr>
      <th>539</th>
      <td> Patrick Robertson</td>
      <td>      John J. Oquendo</td>
    </tr>
    <tr>
      <th>540</th>
      <td> Patrick Robertson</td>
      <td>   Austin K. Gilliard</td>
    </tr>
    <tr>
      <th>541</th>
      <td> Patrick Robertson</td>
      <td>     James M. Eddings</td>
    </tr>
    <tr>
      <th>542</th>
      <td> Patrick Robertson</td>
      <td>        Elaine S. Ott</td>
    </tr>
    <tr>
      <th>543</th>
      <td> Patrick Robertson</td>
      <td>        James A. Foxt</td>
    </tr>
    <tr>
      <th>544</th>
      <td> Patrick Robertson</td>
      <td>      Daniel J. Moore</td>
    </tr>
    <tr>
      <th>545</th>
      <td> Patrick Robertson</td>
      <td>    Kelly S. Ferguson</td>
    </tr>
    <tr>
      <th>546</th>
      <td> Patrick Robertson</td>
      <td>       Joseph L. Wood</td>
    </tr>
    <tr>
      <th>547</th>
      <td> Patrick Robertson</td>
      <td>    Frances A. Miller</td>
    </tr>
    <tr>
      <th>548</th>
      <td> Patrick Robertson</td>
      <td>     Mina W. Lawrence</td>
    </tr>
    <tr>
      <th>549</th>
      <td> Patrick Robertson</td>
      <td>       Jeff M. Wright</td>
    </tr>
    <tr>
      <th>550</th>
      <td> Patrick Robertson</td>
      <td>  Deborah D. Helfrich</td>
    </tr>
    <tr>
      <th>551</th>
      <td> Patrick Robertson</td>
      <td>     Nancy P. Jackson</td>
    </tr>
    <tr>
      <th>552</th>
      <td> Patrick Robertson</td>
      <td>    Bobbie D. Mathews</td>
    </tr>
    <tr>
      <th>553</th>
      <td> Patrick Robertson</td>
      <td>     Arnold J. Fuller</td>
    </tr>
    <tr>
      <th>554</th>
      <td> Patrick Robertson</td>
      <td>     Melvin O. Martin</td>
    </tr>
    <tr>
      <th>555</th>
      <td> Patrick Robertson</td>
      <td> Mildred F. Hottinger</td>
    </tr>
    <tr>
      <th>556</th>
      <td> Patrick Robertson</td>
      <td>  Melissa R. Anderson</td>
    </tr>
    <tr>
      <th>557</th>
      <td> Patrick Robertson</td>
      <td>     Janelle T. Smith</td>
    </tr>
    <tr>
      <th>558</th>
      <td> Patrick Robertson</td>
      <td>    Ann W. McLaughlin</td>
    </tr>
    <tr>
      <th>559</th>
      <td> Patrick Robertson</td>
      <td>    Judith B. Gibbons</td>
    </tr>
    <tr>
      <th>560</th>
      <td> Patrick Robertson</td>
      <td>        Dominick Byrd</td>
    </tr>
  </tbody>
</table>
<p>561 rows × 2 columns</p>
</div>



## INNER JOIN

__INNER JOIN__ Joins two tables where the join condition returns true. Discarded
when returning false or NULL.  

```sql
SELECT col1, col2, ...
FROM table1 INNER JOIN table2 ON condition;
```

### ON Clause

The __ON__ clause specifies the join condition:

- The ON clause can use a multiple set of conditions connected by AND, OR

- USING(<join col>) can also be used if both tables have the same column name
and type

- Some SQL implementations constructs the ON clause from the WHERE clause (DB2)
    - filtering by the WHERE clause gives the same result but in some
implementations will product an intermediate cross product of tables (making the
query slower)

__Example:__ How many events does each member attend?

- Note that this query does not include members who attended no events
    - Query is ordered by events_attended to show a comparison with a latter
query

```sql
SELECT m.name, COUNT(a.event) AS events_attended
FROM member AS m INNER JOIN attendance AS a ON m.quest_id = a.member
GROUP BY m.name
ORDER BY events_attended;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>events_attended</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0 </th>
      <td>       John J. Oquendo</td>
      <td> 1</td>
    </tr>
    <tr>
      <th>1 </th>
      <td>      James M. Eddings</td>
      <td> 2</td>
    </tr>
    <tr>
      <th>2 </th>
      <td>   Melissa R. Anderson</td>
      <td> 2</td>
    </tr>
    <tr>
      <th>3 </th>
      <td>      Melvin O. Martin</td>
      <td> 2</td>
    </tr>
    <tr>
      <th>4 </th>
      <td>      Mina W. Lawrence</td>
      <td> 2</td>
    </tr>
    <tr>
      <th>5 </th>
      <td>     Ann W. McLaughlin</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>6 </th>
      <td>     Bobbie D. Mathews</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>7 </th>
      <td>      Janelle T. Smith</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>8 </th>
      <td>  Mildred F. Hottinger</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>9 </th>
      <td> Phillip C. Mascarenas</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>10</th>
      <td>          Ryan T. Luby</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>11</th>
      <td>      Vivian R. Donley</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>12</th>
      <td>      Arnold J. Fuller</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>13</th>
      <td>    Austin K. Gilliard</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>14</th>
      <td>        Jeff M. Wright</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>15</th>
      <td>     Kelly S. Ferguson</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>16</th>
      <td>      Nancy P. Jackson</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>17</th>
      <td>      Ralph L. Waldrop</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>18</th>
      <td>            Ruben Lamb</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>19</th>
      <td>       Billy L. Hunter</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>20</th>
      <td>   Deborah D. Helfrich</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>21</th>
      <td>         Dominick Byrd</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>22</th>
      <td>     Frances A. Miller</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>23</th>
      <td>         Fred E. Finch</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>24</th>
      <td>        Joseph L. Wood</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>25</th>
      <td>     Judith B. Gibbons</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>26</th>
      <td>    Robert B. Williams</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>27</th>
      <td> Stephanie R. Matthews</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>28</th>
      <td>   Tameika M. McMaster</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>29</th>
      <td>         Elaine S. Ott</td>
      <td> 6</td>
    </tr>
    <tr>
      <th>30</th>
      <td>       Daniel J. Moore</td>
      <td> 7</td>
    </tr>
    <tr>
      <th>31</th>
      <td>     Patrick Robertson</td>
      <td> 7</td>
    </tr>
  </tbody>
</table>
</div>



## OUTER JOIN

__OUTER JOIN__ A join that returns all rows for 1 or 2 tables, even when there
is no corresponding value. In these cases, NULL values are entered for these
corresponding rows.

There are 3 types of OUTER JOINs:

1. __LEFT OUTER JOIN__: An OUTER JOIN returning all rows of the table first
mentioned.

2. __RIGHT OUTER JOIN__: An OUTER JOIN returning all rows of the table second
mentioned.

3. __FULL OUTER JOIN__: An OUTER JOIN returning all rows of both tables.


- Only LEFT OUTER JOIN is implemented in SQLite

__Example:__ What are the names of Stat Club members and how many events they
attended?

```sql
SELECT m.name, COUNT(a.event) AS events_attended
FROM member AS m LEFT OUTER JOIN attendance AS a ON m.quest_id = a.member
GROUP BY m.name
ORDER BY events_attended;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>events_attended</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0 </th>
      <td>        Darrell Aucoin</td>
      <td> 0</td>
    </tr>
    <tr>
      <th>1 </th>
      <td>         James A. Foxt</td>
      <td> 0</td>
    </tr>
    <tr>
      <th>2 </th>
      <td>       John J. Oquendo</td>
      <td> 1</td>
    </tr>
    <tr>
      <th>3 </th>
      <td>      James M. Eddings</td>
      <td> 2</td>
    </tr>
    <tr>
      <th>4 </th>
      <td>   Melissa R. Anderson</td>
      <td> 2</td>
    </tr>
    <tr>
      <th>5 </th>
      <td>      Melvin O. Martin</td>
      <td> 2</td>
    </tr>
    <tr>
      <th>6 </th>
      <td>      Mina W. Lawrence</td>
      <td> 2</td>
    </tr>
    <tr>
      <th>7 </th>
      <td>     Ann W. McLaughlin</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>8 </th>
      <td>     Bobbie D. Mathews</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>9 </th>
      <td>      Janelle T. Smith</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>10</th>
      <td>  Mildred F. Hottinger</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>11</th>
      <td> Phillip C. Mascarenas</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>12</th>
      <td>          Ryan T. Luby</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>13</th>
      <td>      Vivian R. Donley</td>
      <td> 3</td>
    </tr>
    <tr>
      <th>14</th>
      <td>      Arnold J. Fuller</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>15</th>
      <td>    Austin K. Gilliard</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>16</th>
      <td>        Jeff M. Wright</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>17</th>
      <td>     Kelly S. Ferguson</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>18</th>
      <td>      Nancy P. Jackson</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>19</th>
      <td>      Ralph L. Waldrop</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>20</th>
      <td>            Ruben Lamb</td>
      <td> 4</td>
    </tr>
    <tr>
      <th>21</th>
      <td>       Billy L. Hunter</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>22</th>
      <td>   Deborah D. Helfrich</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>23</th>
      <td>         Dominick Byrd</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>24</th>
      <td>     Frances A. Miller</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>25</th>
      <td>         Fred E. Finch</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>26</th>
      <td>        Joseph L. Wood</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>27</th>
      <td>     Judith B. Gibbons</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>28</th>
      <td>    Robert B. Williams</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>29</th>
      <td> Stephanie R. Matthews</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>30</th>
      <td>   Tameika M. McMaster</td>
      <td> 5</td>
    </tr>
    <tr>
      <th>31</th>
      <td>         Elaine S. Ott</td>
      <td> 6</td>
    </tr>
    <tr>
      <th>32</th>
      <td>       Daniel J. Moore</td>
      <td> 7</td>
    </tr>
    <tr>
      <th>33</th>
      <td>     Patrick Robertson</td>
      <td> 7</td>
    </tr>
  </tbody>
</table>
</div>



## Natural Join

__NATURAL JOIN__ A join condition that lets the server decide on the join
conditions based on the same column names and types across columns for the
tables.

__Example:__ What are the position and duties of each Stats Club exec?

```sql
SELECT  e.name, e.position, ep.duties
FROM exec AS e NATURAL JOIN exec_position AS ep;
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>position</th>
      <th>duties</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0 </th>
      <td>    Darrell Aucoin</td>
      <td>  President</td>
      <td> To be aware of MathSoc's Policies and Bylaws i...</td>
    </tr>
    <tr>
      <th>1 </th>
      <td>    Darrell Aucoin</td>
      <td>  President</td>
      <td>        To call and preside over general meetings.</td>
    </tr>
    <tr>
      <th>2 </th>
      <td>    Darrell Aucoin</td>
      <td>  President</td>
      <td> To manage the executive team and the strategic...</td>
    </tr>
    <tr>
      <th>3 </th>
      <td>    Darrell Aucoin</td>
      <td>  President</td>
      <td> To post announcements of all club meetings, an...</td>
    </tr>
    <tr>
      <th>4 </th>
      <td> Judith B. Gibbons</td>
      <td>     Events</td>
      <td> To assist the president and other vice-preside...</td>
    </tr>
    <tr>
      <th>5 </th>
      <td> Judith B. Gibbons</td>
      <td>     Events</td>
      <td> To chair the organization and promotion of lea...</td>
    </tr>
    <tr>
      <th>6 </th>
      <td>         Lamar Roy</td>
      <td>    Finance</td>
      <td> To ensure membership fees are collected and ma...</td>
    </tr>
    <tr>
      <th>7 </th>
      <td>         Lamar Roy</td>
      <td>    Finance</td>
      <td> To keep an up-to-date record of financial tran...</td>
    </tr>
    <tr>
      <th>8 </th>
      <td>         Lamar Roy</td>
      <td>    Finance</td>
      <td> To prepare a summary of the financial records ...</td>
    </tr>
    <tr>
      <th>9 </th>
      <td>         Lamar Roy</td>
      <td>    Finance</td>
      <td>   To prepare the budget at the beginning of term.</td>
    </tr>
    <tr>
      <th>10</th>
      <td>         Lamar Roy</td>
      <td>    Finance</td>
      <td> To volunteer as president in the absence of th...</td>
    </tr>
    <tr>
      <th>11</th>
      <td>    Gilberto Cross</td>
      <td>     Events</td>
      <td> To assist the president and other vice-preside...</td>
    </tr>
    <tr>
      <th>12</th>
      <td>    Gilberto Cross</td>
      <td>     Events</td>
      <td> To chair the organization and promotion of lea...</td>
    </tr>
    <tr>
      <th>13</th>
      <td>        Melba Lane</td>
      <td>  President</td>
      <td> To be aware of MathSoc's Policies and Bylaws i...</td>
    </tr>
    <tr>
      <th>14</th>
      <td>        Melba Lane</td>
      <td>  President</td>
      <td>        To call and preside over general meetings.</td>
    </tr>
    <tr>
      <th>15</th>
      <td>        Melba Lane</td>
      <td>  President</td>
      <td> To manage the executive team and the strategic...</td>
    </tr>
    <tr>
      <th>16</th>
      <td>        Melba Lane</td>
      <td>  President</td>
      <td> To post announcements of all club meetings, an...</td>
    </tr>
    <tr>
      <th>17</th>
      <td>        Ruben Lamb</td>
      <td> Technology</td>
      <td>             Maintain and update the club website.</td>
    </tr>
    <tr>
      <th>18</th>
      <td>        Ruben Lamb</td>
      <td> Technology</td>
      <td> Maintain any hardware, software, or technology...</td>
    </tr>
    <tr>
      <th>19</th>
      <td>        Ruben Lamb</td>
      <td> Technology</td>
      <td> Perform the duties of a Vice President - Event...</td>
    </tr>
    <tr>
      <th>20</th>
      <td> Patrick Robertson</td>
      <td>     Events</td>
      <td> To assist the president and other vice-preside...</td>
    </tr>
    <tr>
      <th>21</th>
      <td> Patrick Robertson</td>
      <td>     Events</td>
      <td> To chair the organization and promotion of lea...</td>
    </tr>
    <tr>
      <th>22</th>
      <td>     Dominick Byrd</td>
      <td>     Events</td>
      <td> To assist the president and other vice-preside...</td>
    </tr>
    <tr>
      <th>23</th>
      <td>     Dominick Byrd</td>
      <td>     Events</td>
      <td> To chair the organization and promotion of lea...</td>
    </tr>
  </tbody>
</table>
</div>



## Quiz: Joining Tables

__Q:__ What are the email addresses and phone numbers of stats club execs who
are in change or organizing at least one event?
<center>
![alt text](https://raw.githubusercontent.com/NormallySane/IntroSQL/master/Images/StatClubTables2.png)
</center>

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-joining-tables)  

## Subqueries

Subqueries are queries contained in queries. These subqueries are contained in
'(', ')'

There are two types of subqueries:

1. __Non-Correlated Subqueries:__ Can be run independently of the larger query.

2. __Correlated Subqueries:__ Must be run concurrently with the outer query.
They are dependent on the outer query.

## Non-Correlated Subqueries

__Non-Correlated Subquery:__ Any valid query within query that if executed by
itself will produce a result (including empty set). These are enclosed in '(',
')' in __FROM__, __WHERE__, or __HAVING__ clauses.

__Example:__ What Stats Club execs are in charge of making posters?

```sql
SELECT e.name, e.position
FROM exec AS e
WHERE e.questid IN (SELECT poster FROM event);
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>position</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>     Dominick Byrd</td>
      <td> Events</td>
    </tr>
    <tr>
      <th>1</th>
      <td>    Gilberto Cross</td>
      <td> Events</td>
    </tr>
    <tr>
      <th>2</th>
      <td> Judith B. Gibbons</td>
      <td> Events</td>
    </tr>
    <tr>
      <th>3</th>
      <td> Patrick Robertson</td>
      <td> Events</td>
    </tr>
  </tbody>
</table>
</div>



## Correlated Subqueries

__Correlated  Subquery__ makes references to it's containing query, executing it
for every candidate row referenced.
- Correlated subqueries can appear in the __SELECT__, __WHERE__, or __HAVING__
clauses.

__Example:__ What majors are the current Stats Club execs enrolled in?
- The member table has the information on majors but exec has the information on
execs

```sql
SELECT name, position,
(SELECT faculty FROM member AS m WHERE m.quest_id = e.questid) AS faulty,
(SELECT major FROM member AS m WHERE m.quest_id = e.questid) AS major
FROM exec AS e;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>position</th>
      <th>faulty</th>
      <th>major</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>    Darrell Aucoin</td>
      <td>     President</td>
      <td> Math</td>
      <td>     Stats</td>
    </tr>
    <tr>
      <th>1</th>
      <td> Judith B. Gibbons</td>
      <td>        Events</td>
      <td> Math</td>
      <td>   Act Sci</td>
    </tr>
    <tr>
      <th>2</th>
      <td>         Lamar Roy</td>
      <td>       Finance</td>
      <td> None</td>
      <td>      None</td>
    </tr>
    <tr>
      <th>3</th>
      <td>    Gilberto Cross</td>
      <td>        Events</td>
      <td> None</td>
      <td>      None</td>
    </tr>
    <tr>
      <th>4</th>
      <td>        Melba Lane</td>
      <td>     President</td>
      <td> None</td>
      <td>      None</td>
    </tr>
    <tr>
      <th>5</th>
      <td>        Ruben Lamb</td>
      <td>    Technology</td>
      <td> Math</td>
      <td>   Act Sci</td>
    </tr>
    <tr>
      <th>6</th>
      <td>      Hannah Mason</td>
      <td> SeniorAdvisor</td>
      <td> None</td>
      <td>      None</td>
    </tr>
    <tr>
      <th>7</th>
      <td> Patrick Robertson</td>
      <td>        Events</td>
      <td> Math</td>
      <td>     Stats</td>
    </tr>
    <tr>
      <th>8</th>
      <td>     Dominick Byrd</td>
      <td>        Events</td>
      <td> Math</td>
      <td> Pure Math</td>
    </tr>
  </tbody>
</table>
</div>



## Correlated vs Non-Correlated

1. Correlated subquery is __dependent__ on outer query, non-correlated is
__independent__.

2. Correlated subquery is executed __concurrently__ with outer query, non-
correlated is executed before.

3. In general, for speed of execution:  

<center>
Correlated subquery < Non-Correlated subquery < Joins
</center>

## Quiz: Subqueries

__Q:__ Where can a Non-Correlated subquery can be placed?

__Q:__ Where can a Correlated subquery can be placed?


__Q:__ Using a non-correlated subquery, what are the names, locations, and
descriptions of events that served pizza?
1. Break the problem into smaller pieces: What are the events that served pizza?
2. Only retrieve values from the table `event` that `event.name` matches those
values

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-subqueries)

## Set Operations

Set operations create a combination of rows from 2 tables into one result set.
- The tables (or the projection of those tables) have to have the same number of
columns and datatypes
    - if one column appears in a table but not in another, supply the value NULL
for the missing column

1. __UNION__: For tables A and B, combines the rows for A and B into one result
set.
2. __INTERSECT__: For tables A and B, returns the rows for A and B that they
have in common.
3. __Difference (EXCEPT)__: For tables A and B, return only the rows in A that
are not in common with B.

## UNION

__UNION operator:__ Addition of one result set to another result set with the
same number of attributes and types.  

```sql
SELECT ... FROM ...
UNION [ALL]
SELECT ... FROM ...
```

- Just __UNION__ removes duplicates, while __UNION ALL__ keeps all rows from
both result sets.

__Example:__ Suppose are you need to contact everyone involved in Stats Club:
members and execs.
What are the names, email addresses, and phone numbers (if you have them) of all
Stats Club members and execs?

```sql
SELECT name, email, NULL AS phone
FROM member
UNION
SELECT name, email, phone
FROM exec;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>email</th>
      <th>phone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0 </th>
      <td>     Ann W. McLaughlin</td>
      <td>         ann@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>1 </th>
      <td>      Arnold J. Fuller</td>
      <td>      arnold@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>2 </th>
      <td>    Austin K. Gilliard</td>
      <td>      austin@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>3 </th>
      <td>       Billy L. Hunter</td>
      <td>       billy@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>4 </th>
      <td>     Bobbie D. Mathews</td>
      <td>      bobbie@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>5 </th>
      <td>       Daniel J. Moore</td>
      <td>      daniel@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>6 </th>
      <td>        Darrell Aucoin</td>
      <td> darrell.aucoin@gmail.com</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>7 </th>
      <td>        Darrell Aucoin</td>
      <td> darrell.aucoin@gmail.com</td>
      <td> 519-555-1424</td>
    </tr>
    <tr>
      <th>8 </th>
      <td>   Deborah D. Helfrich</td>
      <td>     deborah@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>9 </th>
      <td>         Dominick Byrd</td>
      <td>    dominick@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>10</th>
      <td>         Dominick Byrd</td>
      <td>    dominick@uwaterloo.ca</td>
      <td> 519-555-2325</td>
    </tr>
    <tr>
      <th>11</th>
      <td>         Elaine S. Ott</td>
      <td>      elaine@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>12</th>
      <td>     Frances A. Miller</td>
      <td>     frances@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>13</th>
      <td>         Fred E. Finch</td>
      <td>        fred@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>14</th>
      <td>        Gilberto Cross</td>
      <td>    gilberto@uwaterloo.ca</td>
      <td> 519-555-3453</td>
    </tr>
    <tr>
      <th>15</th>
      <td>          Hannah Mason</td>
      <td>      hannah@uwaterloo.ca</td>
      <td> 519-555-2342</td>
    </tr>
    <tr>
      <th>16</th>
      <td>         James A. Foxt</td>
      <td>   james.fox@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>17</th>
      <td>      James M. Eddings</td>
      <td>       james@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>18</th>
      <td>      Janelle T. Smith</td>
      <td>     janelle@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>19</th>
      <td>        Jeff M. Wright</td>
      <td>        jeff@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>20</th>
      <td>       John J. Oquendo</td>
      <td>        john@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>21</th>
      <td>        Joseph L. Wood</td>
      <td>      joseph@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>22</th>
      <td>     Judith B. Gibbons</td>
      <td>      judith@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>23</th>
      <td>     Judith B. Gibbons</td>
      <td>      judith@uwaterloo.ca</td>
      <td> 519-555-2343</td>
    </tr>
    <tr>
      <th>24</th>
      <td>     Kelly S. Ferguson</td>
      <td>       kelly@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>25</th>
      <td>             Lamar Roy</td>
      <td>       lamar@uwaterloo.ca</td>
      <td> 519-555-3432</td>
    </tr>
    <tr>
      <th>26</th>
      <td>            Melba Lane</td>
      <td>       melba@uwaterloo.ca</td>
      <td> 519-555-2322</td>
    </tr>
    <tr>
      <th>27</th>
      <td>   Melissa R. Anderson</td>
      <td>     melissa@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>28</th>
      <td>      Melvin O. Martin</td>
      <td>      melvin@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>29</th>
      <td>  Mildred F. Hottinger</td>
      <td>     mildred@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>30</th>
      <td>      Mina W. Lawrence</td>
      <td>        mina@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>31</th>
      <td>      Nancy P. Jackson</td>
      <td>       nancy@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>32</th>
      <td>     Patrick Robertson</td>
      <td>     patrick@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>33</th>
      <td>     Patrick Robertson</td>
      <td>     patrick@uwaterloo.ca</td>
      <td> 519-555-2312</td>
    </tr>
    <tr>
      <th>34</th>
      <td> Phillip C. Mascarenas</td>
      <td>     phillip@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>35</th>
      <td>      Ralph L. Waldrop</td>
      <td>       ralph@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>36</th>
      <td>    Robert B. Williams</td>
      <td>      robert@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>37</th>
      <td>            Ruben Lamb</td>
      <td>       ruben@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>38</th>
      <td>            Ruben Lamb</td>
      <td>       ruben@uwaterloo.ca</td>
      <td> 519-555-5232</td>
    </tr>
    <tr>
      <th>39</th>
      <td>          Ryan T. Luby</td>
      <td>        ryan@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>40</th>
      <td> Stephanie R. Matthews</td>
      <td>        step@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>41</th>
      <td>   Tameika M. McMaster</td>
      <td>     tameika@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
    <tr>
      <th>42</th>
      <td>      Vivian R. Donley</td>
      <td>      vivian@uwaterloo.ca</td>
      <td>         None</td>
    </tr>
  </tbody>
</table>
</div>



## Intersection (INTERSECT Operator)

__INTERSECT operator:__ Returns only tuples that are in common between two
result sets. Result sets must be equal in number and type of attributes.  

```sql
SELECT ... FROM ...
INTERSECT
SELECT ... FROM ...;
```

__Example:__ What Stats Club execs have also signed up as Stats Club members?

```sql
SELECT name, quest_id
FROM member
INTERSECT
SELECT name, questid
FROM exec;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>quest_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>    Darrell Aucoin</td>
      <td>  darrell</td>
    </tr>
    <tr>
      <th>1</th>
      <td>     Dominick Byrd</td>
      <td> dominick</td>
    </tr>
    <tr>
      <th>2</th>
      <td> Judith B. Gibbons</td>
      <td>   judith</td>
    </tr>
    <tr>
      <th>3</th>
      <td> Patrick Robertson</td>
      <td>  patrick</td>
    </tr>
    <tr>
      <th>4</th>
      <td>        Ruben Lamb</td>
      <td>    ruben</td>
    </tr>
  </tbody>
</table>
</div>



## Difference (EXCEPT Operator)

__EXCEPT operator:__ Returns the first result set minus anything it has in
common with the second result set.  

```sql
SELECT ... FROM ...
EXCEPT [ALL]
SELECT ... FROM ...
```  

- Just EXCEPT uses set theory version of minus.

    - If B has a row in common with A then all rows matching that row is removed

- The optional ALL uses the bag semantics version.
    - If B has a row in common with A then only the number of common rows in B
rows matching that row is removed

__Example:__ What Stats Club members are not execs?

```sql
SELECT name, quest_id
FROM member
EXCEPT
SELECT name, questid
FROM exec;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>quest_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0 </th>
      <td>     Ann W. McLaughlin</td>
      <td>       ann</td>
    </tr>
    <tr>
      <th>1 </th>
      <td>      Arnold J. Fuller</td>
      <td>    arnold</td>
    </tr>
    <tr>
      <th>2 </th>
      <td>    Austin K. Gilliard</td>
      <td>    austin</td>
    </tr>
    <tr>
      <th>3 </th>
      <td>       Billy L. Hunter</td>
      <td>     billy</td>
    </tr>
    <tr>
      <th>4 </th>
      <td>     Bobbie D. Mathews</td>
      <td>    bobbie</td>
    </tr>
    <tr>
      <th>5 </th>
      <td>       Daniel J. Moore</td>
      <td>    daniel</td>
    </tr>
    <tr>
      <th>6 </th>
      <td>   Deborah D. Helfrich</td>
      <td>   deborah</td>
    </tr>
    <tr>
      <th>7 </th>
      <td>         Elaine S. Ott</td>
      <td>    elaine</td>
    </tr>
    <tr>
      <th>8 </th>
      <td>     Frances A. Miller</td>
      <td>   frances</td>
    </tr>
    <tr>
      <th>9 </th>
      <td>         Fred E. Finch</td>
      <td>      fred</td>
    </tr>
    <tr>
      <th>10</th>
      <td>         James A. Foxt</td>
      <td> james.fox</td>
    </tr>
    <tr>
      <th>11</th>
      <td>      James M. Eddings</td>
      <td>     james</td>
    </tr>
    <tr>
      <th>12</th>
      <td>      Janelle T. Smith</td>
      <td>   janelle</td>
    </tr>
    <tr>
      <th>13</th>
      <td>        Jeff M. Wright</td>
      <td>      jeff</td>
    </tr>
    <tr>
      <th>14</th>
      <td>       John J. Oquendo</td>
      <td>      john</td>
    </tr>
    <tr>
      <th>15</th>
      <td>        Joseph L. Wood</td>
      <td>    joseph</td>
    </tr>
    <tr>
      <th>16</th>
      <td>     Kelly S. Ferguson</td>
      <td>     kelly</td>
    </tr>
    <tr>
      <th>17</th>
      <td>   Melissa R. Anderson</td>
      <td>   melissa</td>
    </tr>
    <tr>
      <th>18</th>
      <td>      Melvin O. Martin</td>
      <td>    melvin</td>
    </tr>
    <tr>
      <th>19</th>
      <td>  Mildred F. Hottinger</td>
      <td>   mildred</td>
    </tr>
    <tr>
      <th>20</th>
      <td>      Mina W. Lawrence</td>
      <td>      mina</td>
    </tr>
    <tr>
      <th>21</th>
      <td>      Nancy P. Jackson</td>
      <td>     nancy</td>
    </tr>
    <tr>
      <th>22</th>
      <td> Phillip C. Mascarenas</td>
      <td>   phillip</td>
    </tr>
    <tr>
      <th>23</th>
      <td>      Ralph L. Waldrop</td>
      <td>     ralph</td>
    </tr>
    <tr>
      <th>24</th>
      <td>    Robert B. Williams</td>
      <td>    robert</td>
    </tr>
    <tr>
      <th>25</th>
      <td>          Ryan T. Luby</td>
      <td>      ryan</td>
    </tr>
    <tr>
      <th>26</th>
      <td> Stephanie R. Matthews</td>
      <td>      step</td>
    </tr>
    <tr>
      <th>27</th>
      <td>   Tameika M. McMaster</td>
      <td>   tameika</td>
    </tr>
    <tr>
      <th>28</th>
      <td>      Vivian R. Donley</td>
      <td>    vivian</td>
    </tr>
  </tbody>
</table>
</div>



## WITH Clause

__WITH clause:__ Makes a non-correlated subquery look like a table in the
executed statement:

- Increases readability of the query as well as ensure that if it is used in
several different places, it will only be executed once

```sql
WITH subquery_name [(colname1, ...)] AS
        (SELECT ...),
        subquery_name2 [(colname1, ...)] AS
        (SELECT ...)
SELECT ...
```

__Example:__ Suppose you are doing a report for MathSoc detailing Stats Club
events, budget, and expenses.

```sql
WITH cost (event, expenses) AS
    (SELECT event, SUM(price)
    FROM expenses
    GROUP BY event)
SELECT e.name, e.type, e.budget, cost.expenses
FROM event AS e INNER JOIN cost ON e.name = cost.event;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>budget</th>
      <th>expenses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>             BOT</td>
      <td>      social</td>
      <td>  90.0</td>
      <td>  58.57</td>
    </tr>
    <tr>
      <th>1</th>
      <td>             EOT</td>
      <td>      social</td>
      <td> 160.0</td>
      <td> 160.65</td>
    </tr>
    <tr>
      <th>2</th>
      <td> Intro to Hadoop</td>
      <td> educational</td>
      <td>  90.0</td>
      <td>  96.81</td>
    </tr>
    <tr>
      <th>3</th>
      <td>    Intro to SQL</td>
      <td> educational</td>
      <td>  90.0</td>
      <td> 102.77</td>
    </tr>
    <tr>
      <th>4</th>
      <td>  Intro to SQL 2</td>
      <td> educational</td>
      <td>   200</td>
      <td>  62.63</td>
    </tr>
    <tr>
      <th>5</th>
      <td>       Prof Talk</td>
      <td> educational</td>
      <td>  90.0</td>
      <td>  82.87</td>
    </tr>
    <tr>
      <th>6</th>
      <td>     Prof Talk 2</td>
      <td> educational</td>
      <td>  90.0</td>
      <td>  77.21</td>
    </tr>
    <tr>
      <th>7</th>
      <td>     Prof Talk 3</td>
      <td> educational</td>
      <td>  90.0</td>
      <td>  75.68</td>
    </tr>
  </tbody>
</table>
</div>



## Quiz: WITH Clause (HARD)

__Q:__ MathSoc only provides a maximum cap on social events based on the formula
below. What is the max cap for social expenses and is Stats Club over this
limit?
- Membership fee for Stats Club is 2 dollars

<center>
Social expenses = max{250, (MathSoc_Members) * (5 + (Member_fee))}  

Social expenses = max{250, (MathSoc_Members) * 7}
</center>

Break the problem into smaller problems:
- What are the total expenses for social events?
- What is the max budget for social events?

Smaller Problems:
- What are the total expenses for social events?
    - What events are social events?

- What is the max cap for social events?
    - What is the result of the formula  
    <center>
    (MathSoc  Members) * 7  
    <center>
        - What are the number of Stats Club members who are in the Math Faculty
(aka MathSoc members)?
    - How do we find the max value between this number and 250?

#### Think about how to solve this for 5 mins

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-with-clause-hard)  

## CASE Expressions

__CASE expressions:__ Similar to a series of if else statements executed for
every entry in a table. A new value is returned for every row in the table.

```sql
CASE [column]
        WHEN condition1 THEN result1
        WHEN condition2 THEN result2
        ...
        WHEN condition_n THEN result_n
        [ELSE result]
END
```

- The result can be of any datatype or the result of a correlated or non-
correlated subquery (if the result is a single value)

- CASE expressions are performed by themselves in the __SELECT__ clause or
within a function or aggregate function

    - CASE expressions within aggregate functions allow us to do counts, sums,
averages, etc. of particular occurrences

__Example:__ Suppose like before we are preparing a report for MathSoc, but now
we want to give a warning if the event is over budget or not.

```sql
WITH cost (event, expenses) AS
    (SELECT event, SUM(price)
    FROM expenses
    GROUP BY event)
SELECT e.name, e.type, e.budget, cost.expenses,
    CASE
    WHEN e.budget - cost.expenses < 0 THEN 'Over budget'
    ELSE NULL
END AS warning
FROM event AS e INNER JOIN cost ON e.name = cost.event;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>type</th>
      <th>budget</th>
      <th>expenses</th>
      <th>warning</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>             BOT</td>
      <td>      social</td>
      <td>  90</td>
      <td>  58.57</td>
      <td>        None</td>
    </tr>
    <tr>
      <th>1</th>
      <td>             EOT</td>
      <td>      social</td>
      <td> 160</td>
      <td> 160.65</td>
      <td> Over budget</td>
    </tr>
    <tr>
      <th>2</th>
      <td> Intro to Hadoop</td>
      <td> educational</td>
      <td>  90</td>
      <td>  96.81</td>
      <td> Over budget</td>
    </tr>
    <tr>
      <th>3</th>
      <td>    Intro to SQL</td>
      <td> educational</td>
      <td>  90</td>
      <td> 102.77</td>
      <td> Over budget</td>
    </tr>
    <tr>
      <th>4</th>
      <td>  Intro to SQL 2</td>
      <td> educational</td>
      <td> 200</td>
      <td>  62.63</td>
      <td>        None</td>
    </tr>
    <tr>
      <th>5</th>
      <td>       Prof Talk</td>
      <td> educational</td>
      <td>  90</td>
      <td>  82.87</td>
      <td>        None</td>
    </tr>
    <tr>
      <th>6</th>
      <td>     Prof Talk 2</td>
      <td> educational</td>
      <td>  90</td>
      <td>  77.21</td>
      <td>        None</td>
    </tr>
    <tr>
      <th>7</th>
      <td>     Prof Talk 3</td>
      <td> educational</td>
      <td>  90</td>
      <td>  75.68</td>
      <td>        None</td>
    </tr>
  </tbody>
</table>
</div>



## Quiz: CASE Expressions

__Q:__ Suppose we are interested in the healthiness of our food options at Stats
Club events. A score of various foods was given below. What is the average
'healthiness' of Stats Club events?


| Food | Score |
|------|-------|
| donuts | -2 |
| pop | -2 |
| fries | -2 |
| pizza | -1 |
| cookies | -1 |
| coffee | 0 |
| water | 2 |
| meals | 2 |
| veggie platter | 3 |

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-case-expressions)


## ORDER BY Clause

__ORDER BY Clause:__ Rearranges the rows of a result set according to a tuple of
columns.

```sql
SELECT column_list
FROM table_name
ORDER BY column1, column2, .. columnN [ASC | DESC];
```  

`ASC` is ascending (default)

`DESC` is descending

__Example:__ What is the membership list ordered by name?

```sql
SELECT name
FROM member
ORDER BY name;
```

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0 </th>
      <td>     Ann W. McLaughlin</td>
    </tr>
    <tr>
      <th>1 </th>
      <td>      Arnold J. Fuller</td>
    </tr>
    <tr>
      <th>2 </th>
      <td>    Austin K. Gilliard</td>
    </tr>
    <tr>
      <th>3 </th>
      <td>       Billy L. Hunter</td>
    </tr>
    <tr>
      <th>4 </th>
      <td>     Bobbie D. Mathews</td>
    </tr>
    <tr>
      <th>5 </th>
      <td>       Daniel J. Moore</td>
    </tr>
    <tr>
      <th>6 </th>
      <td>        Darrell Aucoin</td>
    </tr>
    <tr>
      <th>7 </th>
      <td>   Deborah D. Helfrich</td>
    </tr>
    <tr>
      <th>8 </th>
      <td>         Dominick Byrd</td>
    </tr>
    <tr>
      <th>9 </th>
      <td>         Elaine S. Ott</td>
    </tr>
    <tr>
      <th>10</th>
      <td>     Frances A. Miller</td>
    </tr>
    <tr>
      <th>11</th>
      <td>         Fred E. Finch</td>
    </tr>
    <tr>
      <th>12</th>
      <td>         James A. Foxt</td>
    </tr>
    <tr>
      <th>13</th>
      <td>      James M. Eddings</td>
    </tr>
    <tr>
      <th>14</th>
      <td>      Janelle T. Smith</td>
    </tr>
    <tr>
      <th>15</th>
      <td>        Jeff M. Wright</td>
    </tr>
    <tr>
      <th>16</th>
      <td>       John J. Oquendo</td>
    </tr>
    <tr>
      <th>17</th>
      <td>        Joseph L. Wood</td>
    </tr>
    <tr>
      <th>18</th>
      <td>     Judith B. Gibbons</td>
    </tr>
    <tr>
      <th>19</th>
      <td>     Kelly S. Ferguson</td>
    </tr>
    <tr>
      <th>20</th>
      <td>   Melissa R. Anderson</td>
    </tr>
    <tr>
      <th>21</th>
      <td>      Melvin O. Martin</td>
    </tr>
    <tr>
      <th>22</th>
      <td>  Mildred F. Hottinger</td>
    </tr>
    <tr>
      <th>23</th>
      <td>      Mina W. Lawrence</td>
    </tr>
    <tr>
      <th>24</th>
      <td>      Nancy P. Jackson</td>
    </tr>
    <tr>
      <th>25</th>
      <td>     Patrick Robertson</td>
    </tr>
    <tr>
      <th>26</th>
      <td> Phillip C. Mascarenas</td>
    </tr>
    <tr>
      <th>27</th>
      <td>      Ralph L. Waldrop</td>
    </tr>
    <tr>
      <th>28</th>
      <td>    Robert B. Williams</td>
    </tr>
    <tr>
      <th>29</th>
      <td>            Ruben Lamb</td>
    </tr>
    <tr>
      <th>30</th>
      <td>          Ryan T. Luby</td>
    </tr>
    <tr>
      <th>31</th>
      <td> Stephanie R. Matthews</td>
    </tr>
    <tr>
      <th>32</th>
      <td>   Tameika M. McMaster</td>
    </tr>
    <tr>
      <th>33</th>
      <td>      Vivian R. Donley</td>
    </tr>
  </tbody>
</table>
</div>



## LIMIT Clause

__LIMIT Clause:__ Restrict the result set to the first n of rows.

```sql
SELECT column1, column2, columnN
FROM table_name
LIMIT no_of_rows;
```  

- We can also offset where the restriction begins

```sql
SELECT column1, column2, columnN
FROM table_name
LIMIT no_of_rows OFFSET row_num;
```

__Example:__ What is the first 10 members ordered by name?

```sql
SELECT name
FROM member
ORDER BY name
LIMIT 10;
```


<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>   Ann W. McLaughlin</td>
    </tr>
    <tr>
      <th>1</th>
      <td>    Arnold J. Fuller</td>
    </tr>
    <tr>
      <th>2</th>
      <td>  Austin K. Gilliard</td>
    </tr>
    <tr>
      <th>3</th>
      <td>     Billy L. Hunter</td>
    </tr>
    <tr>
      <th>4</th>
      <td>   Bobbie D. Mathews</td>
    </tr>
    <tr>
      <th>5</th>
      <td>     Daniel J. Moore</td>
    </tr>
    <tr>
      <th>6</th>
      <td>      Darrell Aucoin</td>
    </tr>
    <tr>
      <th>7</th>
      <td> Deborah D. Helfrich</td>
    </tr>
    <tr>
      <th>8</th>
      <td>       Dominick Byrd</td>
    </tr>
    <tr>
      <th>9</th>
      <td>       Elaine S. Ott</td>
    </tr>
  </tbody>
</table>
</div>

## Quiz: ORDER BY and LIMIT Clause

__Q:__ What are the top 10 highest priced items in expenses?

Solutions are [here](https://github.com/NormallySane/IntroSQL/wiki/Quiz-Solutions#quiz-order-by-and-limit-clause)  

## Further Practice Questions?

## Quiz: Practice Questions

__Q:__ What events have dates specified?


__Q:__ What events don't have dates specified?


__Q:__ What Stats Club members are in Stats, Act Sci, or CS?
- Recall the `IN` predicate operator


__Q:__ What are the Stats Club exec positions?
- Avoid duplication of positions


__Q:__ How many different Stats Club exec positions are there?
- Note that we can use DISTINCT within aggregate functions


## Topics Not Covered
- How to create a database
    - Creating tables
    - Creating constraints
    - Window functions
    - Indices
    - Views
    - How to insert, delete, alter, drop, etc. data in a table
