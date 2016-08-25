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
    
3. Get the data, specifically:
    - surveys.csv
    - species.csv
    - plots.csv
    
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
        - download from figshare
        - Fire up SQLite Manger in Firefox
        - Open File
    - 


# 01 Basic Queries
# 02 Aggregation
# 03 Joins and Aliases

