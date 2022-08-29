2208291230
	Status: #idea 
		Tags: [[SQL]]

# SQL Basics

# SQL Basics 


- Creating a Database is Simple , Simply Click on the main databases folder and at the top in SSMS click *NEW QUERY* in the pop-up field type the following code: 

` CREATE DATABASE DatabaseName; `

- Syntax for creating a Table is just as simple 

``` CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```

Example :

```
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);

```

Insert Statment

```
Insert into <table_name> (column_name)
(FirstName,LastName,[Age]) Values ('Joey','Blue',50)
``` 

Can specify column names as in this example by putting the column in brackets after the table_name


Select Statement

``` 
select <data>
from Database

//example
select FirstName,LastName, Age
from  Customer
//where clause (specifies where to pull from)
where FirstName ='mike'
and LastName= 'Schmidt%'  (% gives anything that starts with Schmidt and ends with anything else)
```

Update statment

```
update Customer
set Age= 20
where FirstName='Joey'
and LastName= 'Blue'
```

Delete statement

`DELETE <table_name>`

Add Where clause to specify what to delete other wise deletes whole table


Adding comments to SQL is denoted by --

` -- This is a comment for one line`
```
/*  This is a run-on comment 
that lasts until you terminate it with a
star and a slash
*/
```



Change table

Change columns
```
alter table <table_name>
add <column_name> datatype;

--example
alter table customer
add City varchar (50)
```
Add to new column

```
update Customer
set City = 'Bronx'
where FirstName = 'Marcus'
and LastName = 'Harrison'
```

Drop Table 
Dropping a table removes the table definition from the data dictionary. All rows of the table are no longer accessible. All indexes and triggers associated with a table are dropped.
`drop table <table_name>`

primary Keys

Primary keys must contain UNIQUE values, and cannot contain NULL values.

```
	create table Customer
(
	Id int NOT NULL Primary key identity (1,1),
	FirstName varchar (50)
	LastName varchar (50)
	Age int,
	City varchar (50)
)
```
The Identity constraint creates the ID for us, starts at 1 and incremented by 1 after every person.

The NOT NULL constraint enforces a column to not accept NULL values

The following SQL creates a PRIMARY KEY on the "ID" column when the customer table is created.



Create Order

```
Create table Orders
(	
	OrderId int primary key  identity (1,1),
	OrderDate DateTime,
	CustomerID int,
	ProductID int,
)
```

`select * from Orders`

\* is a wildcard to select all

in `values` you can use (GetDate()) to ge the current time


---
# Reference

[SQL in one hour](https://www.youtube.com/watch?v=9Pzj7Aj25lw&t=202s)
