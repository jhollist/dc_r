---
output: 
  html_document:
    css: style.css
---
# 00 Before
<http://www.datacarpentry.org/spreadsheet-ecology-lesson/>

1. Intro myself and helpers
2. Plea for flexibility 
3. Code of conduct and other stuff on workshop site
4. Twitter stuff 
5. Get Data
5. Check on spreadsheet installs

# 00 Spreadsheet Intro
<http://www.datacarpentry.org/spreadsheet-ecology-lesson/00-intro.html>

1. Our goals are:
    - Good data entry practices - formatting data tables in spreadsheets
    - How to avoid common formatting mistakes
    - Dates as data - beware!
    - Basic quality control and data manipulation in spreadsheets
    - Exporting data from spreadsheets
    - In short, 
        - good data organization and management foundation of research
        - We want computers (not people!) to make use of the data.
2. We won't be showing:
    - How to do statistics in a spreadsheet
    - How to do plotting in a spreadsheet
    - How to write code in spreadsheet programs
3. Our main focus is to focus on automation and reproducibility, these are very hard with GUI driven tools
4. Given this, why focus on spreasheets:
    - Some questions for students re: Spreadsheets
        - Who uses spreadsheets?
          - What type of tasks do you use them for?
        - Is it easy to automate tasks?
        - Ever had any problems?
          - What kind of problems?
    - Spreadsheets are ubiquitous and useful. 
5. Problems with Spreadsheets (and What are they good for)
    - Hopefully answers to questions above point out many of the problems.
    - But tables and figures are most one-off (i.e. repetitio/reproducibility not easy)
    - Not great for analysis b/c easy to move data unintentionally, grab wrong columns (e.g Reinhart-Rogoff).
    - But, they are good and useful for data entry
        - Most people know the basics (i.e. don't need a dbase guru just to enter data)
        - Can enforece quality control
        - Provide files for use in other programs
6. Key Point: Learn about some best pracices to our use of spreadsheets that will help out in the long run and provide a useful foundation for research projects.

# 01 Formatting Data Tables
<http://www.datacarpentry.org/spreadsheet-ecology-lesson/01-format-data.html>

1. Learn some best practices for structuring a dataset and for things to do when cleaning up a dataset.
2. Think about a spreadsheet like a computer would not like a human.
    - Notes, Colors, Merged Cells, empty columns or rows are great for humans to read but data analysis is now done by computers!
    - Neat, tidy, orderly, rows, columns are all good things
    - Be nice to yourself and keep structure clean; The you in 6 months when you actually have time to analyze the data will be grateful!
3. Best Practice 1: Keep Track of Your analysis:
    - 
3. Tidy Data Structure
    - Rows are observations (e.g. a sinlge sample, a patient, a plot)
    - Columns are Variables 
    - Values go in cells
    - Patient, date, hgt, weight, pulse, BP (prob)
    - Single data type in a column (don't mix text, numbers, dates,etc.)
    - leave raw data raw (edit data in a new file or new tab)
    - DOCUMENT EVERYTHING!
5. Exercise

# 02 Quick rewview of some of the problems
<http://www.datacarpentry.org/spreadsheet-ecology-lesson/02-common-mistakes.html>

# 03 Dates as data
<http://www.datacarpentry.org/spreadsheet-ecology-lesson/03-dates-as-data.html>

1. Goal is to recognize the problem with dates in spreadsheets
2. In short, dates may look nice in a spreadsheet, but unles you know exactly what is happening behind the scense, the data can very easily get corrupted.
3. Challenge
4. Preferred Date Format
5. "Helpful" Date formats in spreadsheets
6. Dates as integers
7. How to avoid ambiguity
    - Month, Day, Year columns
    - Year, Day of Year columns

# 04 Quality Assurance/Quality control
<http://www.datacarpentry.org/spreadsheet-ecology-lesson/04-quality-control.html>

1. Quality Assurance is for making sure data is entered according to a set of accepted values (e.g. pH between 0 and 14)
2. Quality Controol is checking existing data for problems (e.g that pH value of 72 is probably not that!)
3. Quality Assurance with Data Validation
4. Quality Control
    - Sorting
    - Conditional Formating
    
# 05 Exporting Data
<http://www.datacarpentry.org/spreadsheet-ecology-lesson/05-exporting-data.html>

1. Want to export data into non-proprietary formats.  
2. Allows for use in other software and not tied to a piece of software that might not exist in the future, and not always acceptable for data deposition.
3. Export to .csv (not perfect, but pretty good)

#06 Data Format Caveats
<http://www.datacarpentry.org/spreadsheet-ecology-lesson/06-data-formats-caveats.html>

1. commas in values for .csv (need "")