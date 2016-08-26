---
output: 
  html_document:
    css: style.css
---

# 00 Introduction to SQL

1. Motivation
    - Seen how to clean up messy data
    - Databases offer a way store your now clean data that is robust and safe
    - Databases play well with lots of software (including R)

2. Dataset
    - Seen it a bit already, but we will continue using data from the Portal   
      Project.
    - This is data collected over ~40 years on small mammal communities in 
      southern Arizona.  
    - Has been used in many pubs.
    
3. Get the data, specifically download from figshare:
    - surveys.csv
    - species.csv
    - plots.csv
    - portal_mammals.sqlite
    
4. Let's look:
    - Say I wanted to look at changes in Dipodomys over time in the 2000s, or 
      I wanted get average weight of species per year.  
        - What data do we have on Dipodoyms?
        - Which files is this data in?
        - What sort of operations are needed to do this?
    - Look at each file quickly
    - Select subsets
    - Group data
    - Calculations
    - Combine across spreadsheets
    
6. Databases
    - Why use?
        - separate from analysis
        - no risk of changing data
        - fast
        - better QA on data entry
        - concepts translate really well to languages (r/python)
    - Many different types of Relational Database Managment Systems (RDMS)
        - Access
        - Oracle
        - SQL Server
        - Postgres
        - MySQL
        - Filemaker Pro
        - SQLite
        - Many commonalities across systems
    - We will use SQLite
        - FOSS
        - Widely used
        - No admin overhead
        - Has limits, but usually not a concern for research data

7. Relational Databases 
    - Let's look at portal_mammals.sqlite
        - should have already downloaded from figshare
        - Fire up SQLite Manger in Firefox
        - Open File with connect database
    - Tables on left hand side
        - can see columns
        - see table in browse and search
        - database is just a collection of tables
        - relational becuase the tables (should) relate to one another
    - Structure Tab
        - info about the table and data types of columns
    - Execute SQL tab
        - Where we will be inputing the SQL
    - Summary
        - RDBMS store data in tables with field (columns) and records (rows)
        - Data has types and all values in a field (column) must be of same type
        - Queries are what we use to interact (select, filter, summarize etc.)

8. Database Design
    - Like I mentioned in the summary and what we heard when Ryan was talking about
      clean/tidy spreadsheets:
        - One field per type of info
    - Row-column combinations can not be further subset (i.e. it contains a single 
      atomic value)
    - This is database specific (not necessarily required or always recomended
      for a clean spreadsheet),
          - no redundant info in tables
          - need an identifer (a key) to relate across tables
              - 2 types: primary and foreign
              - primary key is unique and each table must have its own primary 
                key
              - foreign key is used to relate to another tables primary key.
              - show in sqlite dbase surveys relates to plot.

9. Import data into the database
    - Let's create our own database from the three csv files
    - database: new database
    - database: import
    - select surveys and name appropriately
    - Does first row have columns headings?
    - Check the delimiter and quote options
    - leave trailing delim unchecked
    - OK
    - Modify table, OK
    - Set the data types 
        - text: species_id, genus, sex
        - int: day, month, year, weight, ...

## Challenge
    - stickies down:
    - repeat the import for plots and species

# 01 Basic Queries

Queries are how we interact with data.  They return a view of the database but don't (a SELECT query, that is) alter the underlying data.

1. First Query
    - Use the surveys table: data on individs captured included when, what plot, species, sex, and weight...
    - We will be using SELECT queries
    - Query to select year from surveys
        - Explain syntax and convention
    - Query to select year, month, day from surveys
    - Query to select all columns from surveys
    - Unique Values: 
        - select distinct species_id from surveys
        - select distinct year, species_id from surveys
    - Calculated Values:
        - select year, month, day, and weight/1000.0 (mention need for decimal)
        - use ROUND(weight/1000.0,2)
        
## Challenge
    - Write a query to return year, month, day, species_id, and weight in mg
    
2. Filtering
    - May also want to return rows that match some critera
    - Can use the WHERE clause for this.
    - Select all from surveys where species_id = 'DM'
    - where year >= 2000
    - where both are true with AND (use parens around logicals for readability)
    - where species_id = DM or DO or DS

## Challenge
    - return day, month, year, species_id, weight (in kg) for plot 1 and more than 75 grams.
    
3. Complex Queries
    - Combine the above 
    - select all from surveys where year >= 2000 and species_id IN ('DM','DO','DS'));
    - strategy on complex queries, start simple and add
    - if large data, useful to work on smaller dataset to test query
    - very complex and comments are useful
    - SQL comment is '--'
    - show example on website
    
4. Sorting
    - We can use ORDER BY to sort
    - SELECT * FROM species ORDER BY taxa ASC;
    - SELECT * FROM species ORDER BY taxa DESC;
    - SELECT * FROM species ORDER BY genus ASC, species ASC;
    
## Challenge
    - query that returns year, species_id, and weight(kg) from surveys with largest weights on top.
    
5. Order of execution
    - SQL has a fairly specific order of operations and it isn't determined by the order in which we type the query. 
    - But we can filter or order on things that aren't necessarily selected, but this isn't always determined by order of operations
    - in short, if it fails, look at the order as that may be the cause!
    - SELECT genus, species FROM species WHERE taxa = 'Bird' ORDER BY species_id ASC;
    
## Challenge
    - Let’s try to combine what we’ve learned so far in a single query. Using the surveys table write a query to display the three date fields, species_id, and weight in kilograms (rounded to two decimal places), for individuals captured in 1999, ordered alphabetically by the species_id. Write the query as a single line, then put each clause on its own line, and see how more legible the query becomes!
    
# 02 Aggregation
Aggregation allows us to combine results

1. COUNT and GROUP BY
    - We can use COUNT, with the start returns all rows
    - SELECT COUNT(*) FROM surveys;
    - SELECT COUNT(*), SUM(weight) FROM surveys;
    - SELECT ROUND(SUM(weight)/1000.0, 3) FROM surveys;
    - Mention MAX, MIN, AVG
    
## Challenge
    - stickies down
    - Write a query that returns: total weight, average weight, and the min and max weights for all animals caught over the duration of the survey. Can you modify it so that it outputs these values only for weights between 5 and 10?
    
    - Now lets do this same thing, but by species_id
    - SELECT COUNT(*) FROM surveys GROUP BY species_id;
    - GROUP BY can be used with multiple comma separate fields

## Challenge
    - stickies down
    - Write queries that return:
        - How many individuals were counted in each year. a) in total; b) per each species.
        - Average weight of each species in each year. 
        - Can you modify the above queries combining them into one?
        
2. HAVING keyword
    - HAVING is like where but for aggregate results
    - SELECT species_id, COUNT(species_id) FROM surveys GROUP BY species_id HAVING COUNT(species_id) > 10;
    - AS lets you add a column to view and use that later in the query
    - SELECT species_id, COUNT(species_id) AS occurrences FROM surveys GROUP BY species_id HAVING occurrences > 10;
    - Notice order of operations.  In this case HAVING must come after the group_by
    
## Challenge
    - Write a query that returns, from the species table, the number of genus in each taxa, only for the taxa with more than 10 genus.
    
3. Ordering aggregated results
    - We can also order aggregated results similar to how we use HAVING
    - ORDER BY COUNT(species_id);
    
4. Saving queries
    - Often we want to re-use a query, we can do this by saving it as a view:
    - CREATE VIEW species_count AS SELECT species_id, COUNT(*) FROM surveys GROUP BY species_id;
    - to re-use: SELECT * FROM species_count;
    - to drop: DROP VIEW species_count;

## Challenge
    - Write a query that returns the number of each species caught in each year sorted from most often caught species to the least occurring ones within each year starting from the most recent records. Save this query as a VIEW.

# 03 Joins and Aliases

1. Joins
2. Functions
3. Aliases


