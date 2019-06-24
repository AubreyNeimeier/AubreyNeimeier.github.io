---
layout: post
title:      "The Basics of Table Relations in SQL "
date:       2019-06-24 01:10:39 +0000
permalink:  the_basics_of_table_relations_in_sql
---

Let’s start with some basic definitions of keywords. 
## Relational database - a database structured to recognize relations among stored items of information.

In plain english - data that can tell a story by relating various sets of data together. Instead of a list of shoppers and then a list of products, for example, we can relate certain shoppers to certain products. Who bought which products? What are the other attributes of the shopper and their products? These databases tell a more complete story instead of having different databases existing detached and separated. 

These pieces of data are related with a two part strategy. First, each record, with have a 
## Primary Key - A primary key is an integer, for a specific row in a table, which is used as the unique identifier, just like a row in excel has a row number. Primary keys are unique and autoincrementing. 

Ex. Students (ID (THIS IS THE PRIMARY KEY), student name, gender, intended college) 
1 | Jane Doe | female | Ohio State
2 | Jacob Doe | male | Penn State
3 | Sarah Doe | female | Ohio State

Ex. Colleges (ID (THIS IS THE PRIMARY KEY), school name, number of students, state) 
1| Ohio State | 50,000 | Ohio
2 | Penn State | 20,000 | Pennsylvania
3|  Alfred | 2,300 |  New York


Now imagine we wanted a table that explained which students went to which school. A table that RELATED students and colleges… it might seem like we should just add a list of students as a column type, however an ARRAY is not an acceptable data type in SQL. So something like the following WOULD NOT BE POSSIBLE. Also, it would be challenging to work with. Who wants an array of 50,000 students in one cell of a table? 

 
Ex. Colleges (ID (THIS IS THE PRIMARY KEY), school name, number of students, state, students that attend) 

1| Ohio State | 50,000 | Ohio | [Jane Doe, Sarah Doe, Mike Jones, Scott Mescudi etc etc --this list would be 50,000 items long!!!!!!!!!!!!!!]
2| Penn State | 20,000 | Pennsylvania | [ list of 20,000 students ] 
3|  Alfred | 2,300 |  New York [ list of 2300 students ] 

## So instead, we insert a Foreign Key. One of the tables that we are trying to relate, will have a new column added, which is an integer, corresponding to the primary key of the second table. It’s a wordy definition but take a look at the example below. 

We will modify the students table to have a foreign key, indicating the college id (primary id from the college table). 

Ex. Students (ID (THIS IS THE PRIMARY KEY), student name, gender, intended college, college_id (THIS IS THE FOREIGN KEY) 
1 | Jane Doe | female | Ohio State | 1 
2 | Jacob Doe | male | Penn State | 2
3 | Sarah Doe | female | Ohio State | 1 

So in row 1, the foreign key is pointing the PRIMARY ID of the college, from the college table. 

In determining which table will get the foregin key, ask yourself who belongs to who? 
The item which belongs to the other, will have the foreign key. 
In our example, a student belongs to a college, thus the student table will have the foreign key added.


