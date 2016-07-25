---
output: pdf_document
---
# 00 Before we get started
https://jwhollister.com/R-ecology-lesson/00-before-we-start.html

0. Learning Objectives:
    - Organize files and directories related to a particular set of analyses in an R Project within RStudio
    - Define the following (as they apply to R): Script, function, working directory, assign, object, variable
    - Describe the purpose of the RStudio script, console, environment, and plot windows
    - Assign values to variables
    -Call functions with zero or more named or unnamed arguments
    - Use the built-in RStudio help interface to search for more information on R functions
    -Ask for help from the R user community, providing sufficient information for the problem to be reproduced and troubleshooted
1. Working Directory
2. RStudio to manage WD
    - Open RStudio
    - Create Project data-carpentry
    - Create data/ and download data into it
    - Create data-carpentry-script.R
    - Show diagram
3. RStudio walk-through
    - Panes
    - Auto-complete
    - R Code
        - Code is instructions to computer: 2-ways
        - Console
            - prompt (> vs +)
            - ESC
        - Script to console (buttons and ctrl-enter)
4.  Basics of R
    - Free and Open Source
    - Better than commercial
        - First implementations
        - widely extensible (nrow(available.packages()))
    - 1000's of developers vs 10's-100's
    - huge and (mostly) friendly community
    - functional and OO
    - not just for stats, general purpose programming too.
    - http://jwhollister.com/R-ecology-lesson/motivation.html
5. R Syntax
    - https://jwhollister.com/R-ecology-lesson/00-before-we-start.html#the-r-syntax
    - comments
    - assignment operator
    - a function
    - `=` for args
    - `$`
    - quotes v not quotes
6. Using functions
    - `round`
    - `args(round)`
    - show multiple args
        - named (orderd, not ordered)
        - not-named
    - with base R: ~2400
    - Extend R with Packages:
        - `install.packages()`
        - CRAN
        - `library()`
        - `install.packages("dplyr")`
        - `library("dplyr")`
        - `dplyr::mutate()`
7. The most important skill in coding: HELP!
    - https://twitter.com/ThePracticalDev/status/716390583217029124
    - When you know the function
        - `?` or `help`
        - args
        - RStudio auto-complete
    - When you know the package
        - `help(package="dplyr")`
    - When you know a bit of the topic
        - `??smirnov`
        - `??histogram`
    - Google and Stackoverflow
        - Asking good questions (see https://jwhollister.com/R-ecology-lesson/00-before-we-start.html#asking-for-help)
    - Mailing Lists
    - Task Views
    
## 01 Intro to R
https://jwhollister.com/R-ecology-lesson/01-intro-to-R.html

0. Learning objectives:
    - Familiarize participants with R syntax
    - Understand the concepts of objects and assignment
    - Understand the concepts of vector and data types
    - Get exposed to a few functions
1. Creating Objects
    - Basic operators `+`, `-`, `*`, `/` 
    - can save result to an object with `<-` 
    - `weight_kg <- 55`
    - `(weight_kg <- 55)`
    - `weight_kg <- 55; weight_kg`
    - overwrite value
    - use math to change (*2.2 for lbs)
    - `weight_lbs <- 2.2 * weight_kg`
2. Challenge
    - work with person next to you
    - discuss what you think values would be
    - confirm using R
    - About 5 minutes
3. Vectors and data types
    - Vector
        - most basic structure
        - have length
        - have type (must be the same)
    - `weight_g <- c(50, 60, 65, 82)`
    - `weight_g`
    - `animals <- c("mouse", "rat", "dog")`
    - `animals`
    - `length(), class(), str()`
    - add to the vector (beginning and end)
        - `c(animals,"")`
    - types
        - numeric
        - character
        - logical/boolean
        - integer
        - raw
        - complex
    - Other data structures
        - list
        - matrix
        - factor
        - data.frame
4. Challenge
    - Work on together
    - We’ve seen that atomic vectors can be of type character, numeric, integer, and logical. But what happens if we try to mix these types in a single vector?
        - coercion
    - What class will these be?
    - `num_char <- c(1, 2, 3, 'a')`
    - `num_logical <- c(1, 2, 3, TRUE)`
    - `char_logical <- c('a', 'b', 'c', TRUE)`
    - `tricky <- c(1, 2, 3, '4')`
    - `c(3,"z",TRUE)`
    - so: 
      - Logical > Numeric
      - Logical > Character
      - Character > Numeric
      - Character > Numeric + Logical
5. Subsetting
    - `animals <- c("mouse", "rat", "dog", "cat")`
    - `animals[2]`
    - `animals[c(3,2)]`
    - `animals[c(1, 2, 3, 2, 1, 4)]`
    - `animals[-3]`
6. Conditional subsetting
    - `weight_g <- c(21, 34, 39, 54, 55)`
    - Subset based on logical
        - `weight_g[c(TRUE, FALSE, TRUE, TRUE, FALSE)]`
    - so we can use conditional statements such as
        - `weight_g > 50` 
        - `weight_g[weight_g > 50]`
        - or: `weight_g[weight_g < 30 | weight_g > 50]`
        - and: `weight_g[weight_g >= 30 & weight_g == 21]`
    - Works with both numeric and character
        - `animals[animals == "cat" | animals == "rat"]`
        - %in%: `animals %in% c("rat", "cat", "dog", "duck")`
        - `animals[animals %in% c("rat", "cat", "dog", "duck")]`
7. Challenge:
    - what does `"four" > "five"` return?
    - why?
8. Missing Data
    - Should have already discussed during spreadsheet, if not say a few words 
    - R's values is `NA`
    - for example: 
        - `planets <- c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune", NA)`
        - `heights <- c(2, 4, 4, NA, 6)`
        - `mean(heights)`
        - `max(heights)`
        - `mean(heights, na.rm = TRUE)`
        - `max(heights, na.rm = TRUE)`
    - `is.na()`
    - `na.omit()`
    - `complete.cases()`
9. Challenge
    - Try this: `sample <- c(2, 4, 4, "NA", 6); mean(sample, na.rm = TRUE)`
    - What happens and why?
    - Why does the error message say the argument is not numeric?
    
## 02 Starting with data
https://jwhollister.com/R-ecology-lesson/02-starting-with-data.html

0. Learning objectives: 
    - load external data (CSV files) in memory using the survey table (surveys.csv) as an example
    - explore the structure and the content of a data frame in R
    - understand what factors are and how to manipulate them
1. Introduce the survey.csv dataset
    - it is data on species captured across many years and plots

|Column|Description|
|------|-----------|
|record_id|	Unique id for the observation|
|month|	month of observation|
|day|	day of observation|
|year|	year of observation|
|plot_id|	ID of a particular plot|
|species_id|	2-letter code|
|sex|	sex of animal (“M”, “F”)|
|hindfoot_length|	length of the hindfoot in mm|
|weight|	weight of the animal in grams|
|genus|	genus of animal|
|species|	species of animal|
|taxa|	e.g. Rodent, Reptile, Bird, Rabbit|
|plot_type|	type of plot|

2. Download the data, store in data folder, and read in
    - `download.file("https://ndownloader.figshare.com/files/2292169", "data/portal_data_joined.csv")`
    - `surveys <- read.csv('data/portal_data_joined.csv')`
    - `head(surveys)`: describe the result
    - `str(surveys)`: do challenge
3. Challenge:
    - If not already done, download data
    - read into surveys
    - get result of str(): green sticky when you get there
    - Answer these:
        - What is the class of the object surveys?
        - How many rows and how many columns are in this object?
        - How many species have been recorded during these surveys?
    - Point out factors.  Useful structure, but unique and need to be discussed before we dig more into data frames.
4. Factors
    - For categorical data
    - stored as integers(i.e. levels) with labels
    - pre-detemined number of levels
        - may have A, B, C levels but only A and C in your data
        - `sex <- factor(c("male", "female", "female", "male"))`
        - `levels(sex)`
        - `nlevels(sex)`
    - These don't have order, but you might
        - `food <- factor(c("low", "high", "medium", "high", "low", "medium", "high"))`
        - `levels(food)`
        - `food <- factor(food, levels=c("low", "medium", "high"))`
        - `levels(food)`
        - `min(food) ## doesn't work`
    - To add the ordering:
        - `food <- factor(food, levels=c("low", "medium", "high"), ordered=TRUE)`
        - `levels(food)`
        - `min(food) ## works!`
    - Converting Factors
        - `as.character()`
        - `as.numeric()` be careful
        - Examples
              - `f <- factor(c(1, 5, 10, 2))`
              - `as.numeric(f) ## wrong! and there is no warning...`
              - `as.numeric(as.character(f)) ## works...`
              - `as.numeric(levels(f))[f]  ## The recommended way.`
                  - Recomended becasue slightly more effecient than as.character, but not by much.
5. Challenge
    - In which order are the treatments listed?
    - How can you recreate this plot with "control" listed last instead of first?
    - `exprmt <- factor(c("treat1", "treat2", "treat1", "treat3", "treat1", "control","treat1", "treat2", "treat3"))`
    - `table(exprmt)`
    - `barplot(table(exprmt))`
    - Work on this on your own.
    - ~10 minutes to work  on this.
    
## 03 Data Frames
https://jwhollister.com/R-ecology-lesson/03-data-frames.html

0. Learning objectives
    - understand the concept of a data.frame
    - use sequences
    - know how to access any element of a data.frame
1. What are data frames?
    - de facto standard for data in R
    - tabular/rectangular data
    - has rows and columns, spreadsheet like but with rules
        - collection of vectors as columns
    - can see basics structure with `str()`
    - either built or imported
        - `data.frame()`
        - `read.csv()`
        - `read.table()`
        - packages rio, readr, readxl ...
        - defualt on import is to convert strings to factors... ugh!
    - import:
        - `some_data <- read.csv("data/some_file.csv", stringsAsFactors = FALSE)`
    - build:
        - Compare the output of these examples
        - vs`character` and `factor`.
        - factor: 
            - `example_data <- data.frame(animal=c("dog", "cat", "sea cucumber", "sea urchin"),feel=c("furry", "furry", "squishy", "spiny"), weight=c(45, 8, 1.1, 0.8)); str(example_data)`
        - character:
            - `example_data <- data.frame(animal=c("dog", "cat", "sea cucumber", "sea urchin"),feel=c("furry", "furry", "squishy", "spiny"), weight=c(45, 8, 1.1, 0.8),stringsAsFactors = FALSE); str(example_data)`
2. Challenge
    - Let's do these one at a time, then discuss.  5 minutes for each.
    - Find the mistakes and experiment!!
        - `author_book <- data.frame(author_first=c("Charles", "Ernst", "Theodosius"), author_last=c(Darwin, Mayr, Dobzhansky),year=c(1942, 1970))`
    - Predict class for each column, we will check together using `str()`
        - Did you guess right? Why? Why not?
        - What would stringAsFactors = FALSE have done?
        - What needs to change to get everything as you'd expect?
        - `country_climate <- data.frame(country=c("Canada", "Panama", "South Africa", "Australia"),climate=c("cold", "hot", "temperate", "hot/temperate"), temperature=c(10, 30, 18, "15"), northern_hemisphere=c(TRUE, TRUE, FALSE, "FALSE"),has_kangaroo=c(FALSE, FALSE, FALSE, 1))`
    - We've talked about `data.frame()` and `read.csv()`, but you can also bind existing vectors together as columns with `cbind()` or as rows with `rbind()`.  Try this and the check with `class()`.
        - `colors <- c("red", "green", "blue", "yellow")`
        - `counts <- c(50, 60, 65, 82)`
        - `new_dataframe <- as.data.frame(cbind(colors, weights))`
        - `class(new_dataframe)`
    - Gist of this is that type conversions is both a good and bad thing.  Just make sure you check your data when it is read in to be sure it is as you expect.
3. Inspecting `data.frame` objects
    - in addition to `head()` and `str()` we can check
    - Size
        - `dim()`
        - `nrow()`
        - `ncol()`
    - Content
        - `head()`
        - `tail()`
    - Names
        - `names()`
        - `rownames()`
    - Summary
        - `str()`
        - `summary()`
4. Indexing, Sequences, and Subsetting
    - Sequences
        - `:`, `2:8`
        - `seq(1, 10, by=2)`
        - `seq(5, 10, length.out=3)`
        - `seq(50, by=5, length.out=10)`
        - `seq(1, 8, by=3) # sequence stops to stay below upper limit`
    - Indexing
        - vector
            - `a_vector <- 20:10; a_vector[3]`
        - data.frame
            - `surveys[1]`
            - `surveys[,1]`
            - `surveys[1,1]`
            - `surveys[1,6]`
            - `surveys[1:3,7]`
            - `surveys[3,]`
            - `head_surveys <- surveys[1:6,]`
        - by column name
            - `surveys[,"species_id"]`
            - `surveys[["species_id"]]`
            - `surveys$species_id`
            - `surveys$d` #word on partial matching, don't do it`
    - Subsetting
        - dm <- surveys[surveys$species_id == "DM", ]
        
5. Challenge
    - The function nrow() on a data.frame returns the number of rows. Use it, in conjuction with seq() to create a new data.frame called surveys_by_10 that includes every 10th row of the survey data frame starting at row 10 (10, 20, 30, …)
    - Create a data.frame containing only the observations from 1999 of the surveys dataset.

## 04 Aggregating and analyzing data with dplyr
https://jwhollister.com/R-ecology-lesson/04-dplyr.html

0. Learning Objective
    - Learn basic utilities of the `dplyr` package
    - Select and filter data
    - Be able to use `magrittr` pipes
    - Create new columns with `mutate()`
    - Use the split-apply-combine paradigm to summarize data 
    - Export data with `write.csv()`
    
1. What is `dplyr`? 
2. Selecting and Filtering
    - Selecting columns
        - `select(surveys, plot_id, species_id, weight)`
    - Filtering rows
        - `filter(surveys, year == 1995)` 
        - note: `==` if not already covered
3. Pipes
    - What if we want to both select and filter?
        - intermediate, nested, or pipes
        - Let little bunny foo-foo explain:
            - http://r4ds.had.co.nz/pipes.html
        - from `magrittr`, a `dplyr` dependency
    - `output %>% input #first arg by default`
    - Examples: 
        - `surveys %>% filter(weight < 5) %>% select(species_id, sex, weight)`
        - `surveys_sml <- surveys %>% filter(weight < 5) %>% select(species_id, sex, weight);surveys_sml`
4. Challenge
    - Using pipes, subset the data to include individuals collected before 1995, and retain the columns year, sex, and weight.
    - Stickies when done
    - I'll show mine (or ask if anyone wants to show)
5. Mutate
    - Create new columns
    - examples (show line breaks in source):
        - `surveys %>% mutate(weight_kg = weight / 1000)`
        - `surveys %>% mutate(weight_kg = weight / 1000) %>% head`
        - `surveys %>% filter(!is.na(weight)) %>% mutate(weight_kg = weight / 1000) %>% head`
            - describe `!is.na()`
6. Challenge
    - Create a new dataframe from the survey data that meets the following criteria: contains only the species_id column and a column that contains values that are half the hindfoot_length values (e.g. a new column hindfoot_half). In this hindfoot_half column, there are no NA values and all values are < 30.
7. Split-apply-combine and `summarize()`
    - Split into groups
    - Apply analyis to each
    - Combine results
    - See https://www.jstatsoft.org/article/view/v040i01
    - `group_by()` and `summarize()`
    - Examples:
        - `surveys %>% group_by(sex) %>% summarize(mean_weight = mean(weight, na.rm = TRUE))`
        - two columns: `surveys %>% group_by(sex, species_id) %>% summarize(mean_weight = mean(weight, na.rm = TRUE))`
        - remove missing values up front: `surveys %>% filter(!is.na(weight)) %>% group_by(sex, species_id) %>% summarize(mean_weight = mean(weight))`
        - explain `tbl_df`
        - `surveys %>% filter(!is.na(weight)) %>% group_by(sex, species_id) %>% summarize(mean_weight = mean(weight)) %>% print(n=15)`
        - Summarize multiple values: `surveys %>%filter(!is.na(weight)) %>% group_by(sex, species_id) %>% summarize(mean_weight = mean(weight), min_weight = min(weight))`
    - Tally
        - as part of summarize with: `surveys %>% group_by(sex) %>% summarize(mean_weight = mean(weight, na.rm = TRUE),samp = n())`
        - with `tally()`: `surveys %>% group_by(sex) %>% tally()`
8. Challenge
    - How many individuals were caught in each plot_type surveyed?
    - Use group_by() and summarize() to find the mean, min, and max hindfoot length for each species (using species _id).
    - What was the heaviest animal measured in each year? Return the columns year, genus, species_id, and weight.
9. Exporting data
    - After a lot of data munging, useful to store to external file for sharing, archiving, etc.
    - Do with `write.csv()`
    - Let's prep our dataset for next lesson on plotting and write out to a new .csv
```
surveys_complete <- surveys %>%
  filter(species_id != "",  # remove missing species_id
  !is.na(weight),           # remove missing weight
  !is.na(hindfoot_length),  # remove missing hindfoot_length
  sex != "")                # remove missing sex

#Most common: 
species_counts <- surveys_complete %>%
                    group_by(species_id) %>%
                    tally %>%
                    filter(n >= 50) %>%
                    select(species_id)
#Now filter on these: 
surveys_complete <- surveys_complete %>%
                      filter(species_id %in% species_counts$species_id)
```
    - `dim(surveys_complete)` #Should be 30463 by 13
    - Finally: `write.csv(surveys_complete, file="data_output/surveys_complete.csv", row.names=FALSE)`
    
## 05 Data Visualization with ggplot2
http://jwhollister.com/R-ecology-lesson/05-visualization-ggplot2.html

0. Learning objectives
    - Visualize mammals data from surveys_complete.csv
    - Understand how to plot data using `ggplot2`
    - Build step-by-step, complex plots
1. Get and Load packages
    - `install.packages("ggplot2")`
    - `library(ggplot2)`
    - `library(dplyr)`
2. What is `ggplot2`
    - plotting package for all things static viz
    - data.frame is basis for plots
    - basic recipe:
        - create ggplot object
        - add geom
        - bind together with `+`
        - call object to plot
    - interactive example:

```
#minimum required
ggplot(data = surveys_complete) 
#now has x and y mapped via aes()
ggplot(data = surveys_complete, aes(x = weight, y = hindfoot_length)) 
#Add the geometry to plot
ggplot(data = surveys_complete, aes(x = weight, y = hindfoot_length)) + geom_point

```

-dadshfalhflajkshf


```
surveys_plot <- ggplot(data = surveys_complete, aes(x = weight, y = hindfoot_length)) + geom_point
surveys_plot
```

    - think of stuff in `ggplot()` as universal (available to all geoms) and stuff added to geom as only for that geom.
    
    


