---
layout: post
title:      "SQL Joins (Queries and Tables)"
date:       2019-07-01 02:04:12 +0000
permalink:  sql_joins_queries_and_tables
---

Today we will be talking about SQL joins, a powerful way to relate and aggregate data across many tables. First, lets start with definitions of each. 
## An Important Difference
A SQL join clause is a way to combine ROWS from two or more tables, based on a common column between them. After a join CLAUSE, or join QUERY is preformed, we have essentially search RESULTS. The data may be coming from multiple tables, and we may rename columns, but the final product is simply a search result. There is no manipulation of tables in the database, only extractions. 

A SQL join table is a new table we form in the database. Like join queries, they may pull data from multiple tables, however the final product is a new, permanent, table in the database. From here, the join TABLE, may be used in future QUERIES. 

Now that we have defined and differentiated the two, let’s review our options for building these tables and queries. There are four types of joins, which we can use to build queries/clauses AND join tables. I have summarized below. For visual learners, such as myself, the graphic below may be more meaningful. 

TYPE | DESCRIPTION
Inner join | returns all rows where there is a match in BOTH 
Left join | ALL left (first table) rows AND right table rows if there is a match
Right join | ALL right (second table) rows AND left table rows if there is a match 
Full join | ALL rows where there is a match in ONE of the tables. Essentially all rows from both tables. 

## SQL Join Queries
Imagine a school has a list containing the name of every student along with their student ID, their grade, and lunch period. Now imagine, the school also has a list of student ID’s, and their corresponding food allergies. Now for the lunch ladies preparing the food for each period, they must cross reference information between two tables to prepare each student’s food properly, for the correct period. Here, a SQL join clause could become a hybrid of both tables. By joining the tables based on the common COLUMN in each (student ID), we eliminate the need for the lunch ladies to cross reference information across two tables. 

### Boiler Plate code for a SQL QUERY
SELECT column(s)
AS new_column_name(s)_from_table_2
FROM table_1_name
TYPE_OF_JOIN table_2_name
ON table_1_column = table_2_column

For example, to query cats with owners (and only cats that HAVE owners) we our query would be:

SELECT Cats.name, Cats.breed, Owners.name 
AS “owner_name” 
FROM cats
INNER JOIN owners
ON Cats.owner_id = Owners.id 

NOTE the final, true expression on which the join is based. Since we have two tables, one with a cats.owners_id and the second with the Owners ID, that is how they are linked. The expression must be true! We must have this ‘link of equality’ in order to make a join query. Most often, these ‘links of equality’ are formed with a primary key of one table, and another ID column in the other. 

The returned result looks like the following:

name | breed | owner_name
Maru | Scottish | Bob
Hana | Tabby | Bob
Nona | Tortioseshell | Sophie
-	Remember column names are always lowercased and snaked. 
## SQL Join Tables
Now we will review how to create a join table. This will be a new table we permanently add to the database, and it will specifically link data in a MANY to MANY relationship. A join table contains common fields from 2 or more tables, to create a many to many relationship. The columns are typically primary keys and foreigns keys from the two tables, similar to the columns involved in the ‘links of equality’ from above. 
Lets use the same cats and owners example from before. Cats may have many owners, and owners may have many cats. Thus, an inner join table, representing a many to many relationship is appropriate. The boiler plate syntax would look like the following: 
CREATE TABLE cats_owners(
cat_id  INTEGER
owner_id INTEGER) ;

The resulting table would look like the following
cat_id | owner_id 
3 | 2 
3 | 3
1 | 2 


This table by itself isn’t super meaningful to the naked eye. However it is a powerful table to incorporate into future search queries. We can select additional information by performing a join statement on one of the original tables, with the newly formed join table. 

### Boiler Plate code for a SQL JOIN TABLE

The boilerplate syntax for that type of query is very similar to a normal sql query, however one of the tables is a join table now; 

SELECT column(s)
FROM table_1
INNER JOIN table_2
ON table_1.column_name = table_2.column_name
WHERE table_2.column_name = condition

Or with our example, to select all owners of the cat with id = 3 we would use the following query:

SELECT owners.name
FROM owners
INNER JOIN cats_owner
ON owners.id = cats_owners.owner_id
WHERE cats_owner.cat_id = 3


