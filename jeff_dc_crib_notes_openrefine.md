---
output: 
  html_document:
    css: style.css
---

# 00 Setup and 01 Introduction
<http://www.datacarpentry.org/OpenRefine-ecology-lesson/setup>
<http://www.datacarpentry.org/OpenRefine-ecology-lesson/00-getting-started/>

1. Get the data
    - download and save to folder
    - I'm using data_carpentry_uri/data
2. Make sure we can get OpenRefine running.
3. Why use OpenRefine
    - Saves all steps to a file (kind of like automatically creating the "notes" we created in the Excel exercises)
    - Can undo easily and requires us to save work to a new file to keep hcnages
    - Allows us to apply some pretty high powered stuff easily (e.g. clustering algorithms)
4. Pretty active community - look at links 
5. Some basics of OpenRefine:
    - Open source
    - active community
    - good with biggish data (not too big though)
6. Now has a couple of R packages but we won't be showing those.  If you get comfy with R and like what you see here, try them out.
    - https://github.com/ChrisMuir/refinr
    - https://cran.r-project.org/web/packages/rrefine/index.html

# 02 Working with OpenRefine
<http://www.datacarpentry.org/OpenRefine-ecology-lesson/01-working-with-openrefine/>

1. Most of this will be live coding, but quickly we will learn how to:
    - create a project
    - get data from local computer
    - load the file
    - explore data with faceting
    - use clustering
    - split text
    - undo and redo
    - Clean up white spaces.

2. Go to Open Refine and got to the link with the materials we will be following these instructions.
  
    - Create Project
        - choose file
        - show what happens with wrong delim
        - create project
    - scientificName text facet
        - sort by count
        - edit (but don't keep)
    - cluster on scientificName
        - In text facet column on left, click cluster
        - key collision and metaphone3
        - Merge, merge selected and recluster
    - split scientific Name
        - from column, select Edit Column, split ...
        - space
        - uncheck remove
    - Undo/Redo 
        - get rid of split
    - Edit/transform/trim ...
    - Redo split
        - why only 2 columns now?
        
# 03 Filtering and Sorting with OpenRefine
<http://www.datacarpentry.org/OpenRefine-ecology-lesson/02-filter-exclude-sort/>

Show - no exercises

1. Filtering
  - scientific Name : Text Filter
  - Type in "bai" - 48 rows
  - Show 50 Rows
  - Challenge
2. Exclude Entries
    - In a text facet exclude one of these.
    - Don't keep this...
3. Sorting



# 04 Examining Numbers in OpenRefine
<http://www.datacarpentry.org/OpenRefine-ecology-lesson/03-numbers/>

Skip

# 05 Scripts from OpenRefine
<http://www.datacarpentry.org/OpenRefine-ecology-lesson/04-scripts/>

Show - no exercises

1. All of these steps are saved as a JSON file that open refine can use to re run.  
2. Follow along on website and redo on fresh copy of data

# 06 Exporting and Saving Data from OpenRefine
<http://www.datacarpentry.org/OpenRefine-ecology-lesson/05-save-export/>

Show - no exercises

# 07 Other Resources in OpenRefine
<http://www.datacarpentry.org/OpenRefine-ecology-lesson/06-resources/>