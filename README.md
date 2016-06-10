## RTI CDS Backend Developer Exercise 01

Welcome to Exercise 01. This exercise provides a small SQLite database with some data derived from the 1996 US Census and a few questions related to working with SQL and open source analysis packages.

----

### Some guidance

1. Use open source languages and tools, such as Python, R, Ruby, or Java.
2. Clone this repository to your computer. Work in your clone of it, and when you're done, send us a tarball, zip file, or link to your repo online.
3. Use the Internet as a resource to help you complete your work. We do it all the time.
4. Comment your code so that when you look back at it in a year, you'll remember what you were doing.
5. There are many ways to approach and solve the problems presented in this exercise.
6. Have fun!
7. Don't spend more than about 2 hours max on this. You don't need to complete all the tasks listed below: they are just some examples to help you out.

Google will point you to popular libraries for connecting to SQLite databases from Python, R, etc.

----

### The Task

There are many things you can do with this dataset. Here are a few structured tasks to attempt:

0. Read the section below about **The Data**.
1. Write a SQL query that creates a consolidated dataset from the normalized tables in the database. In other words, write a SQL query that "flattens" the database to a single table.
2. Export the "flattened" table to a CSV file.
3. Import the "flattened" table (or CSV file) into your programming language of choice (R, Python, Java, etc.) and put it into a data structure for analysis.
4. Perform some simple exploratory analysis and generate summary statistics to get a sense of what is in the data.
5. Create a simple web application that shows your analysis.
6. Create a paginated view of the data in your web application.
7. Generate one or more charts that you feel convey important relationships in the data.

----

### The Data

This repository contains a file called `exercise01.sqlite`. It is a normalized relational [SQLite database](http://www.sqlite.org). 

It contains a table, named `records`, that has 48842 US Census records with the following fields:

- `id`: a unique id number for each record
- `age`: a continuous variable representing an individual's age
- `workclass_id`: foreign key to the `workclasses` table, representing the broad class of occupation of an individual
- `education_level_id`: foreign key to the `education_levels` table, representing the highest level of education an individual received
- `education_num`: a continuous variable representing an individual's current education level
- `marital_status_id`: foreign key to the `marital_statuses` table, representing an individual's marital status
- `occupation_id`: foreign key to the `occupations` table, representing an individual's occupation
- `race_id`: foreign key to the `races` table, representing an individual's race
- `sex_id`: foreign key to the `sexes` table, representing an individual's sex
- `capital_gain`: a continuous variable representing post-social insurance income, in the form of capital gains.
- `capital_loss`: a continuous variable representing post-social insurance losses, in the form of capital losses.
- `hours_week`: a continuous variable representing the number of hours per week an individual worked.
- `country_id`: foreign key to the `countries` table, representing an individual's native country
- `over_50k`: a boolean variable representing whether the individual makes over $50,000/year. A value of 1 means that the person makes greater than $50,000/year and a value of 0 means that the person makes less than or equal to $50,000/year.

Inspection of the database will reveal the reference tables and the values that they contain, referenced by the foreign keys in the categorical fields of the `records` table. Basically, anywhere you see a field name above that ends with `_id`, there is a corresponding table in the database that contains the values associated with that categorical variable. Fields that contain continuous values, such as `age`, do not join to other tables.

Some of the reference tables have an entry for a question mark `?` that represents missing data in `records`.
