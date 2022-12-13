# IS426-final-project (Documentation of code)
*Note: All csv files will need to be moved to a folder labeled "data", but I saw no option to do that in the repo*

This code was designed to rip data from csv files, read them into a MySQL database, manipulate the data in SQL to create the target comparison, then showcase multiple ways of executing Python code to find certain targets.

## The Data
The datasets were various economic indicators from the City of Boston (such as passengers through Logan Airport, the unemployment rate, etc), as well as the crime incident reports from 2015 up to 2019, which matches up with the indicators timeframe. Done in a Jupyter notebook, I have documented this code cell by cell.

## Code Cell 1: Loading the Data
In this cell, I use the pymysql package to establish a connection to the MySQL database, and reset the target tables (deleting and re-creating them). I then iterated through the files, loading them into lists of dictionaries, then executing a SQL command to insert each record into the database. This took over half an hour, so I would highly advise against running the code again.

## Code Cell 2: Aggregating the Data
Now that we have all of our data, we just need to retrieve it in the format we want, with the granularity lined up, grouped by offense code, month, and year. To do this, we first needed to select our key columns, and then join the tables to avoid a cartesian product. Lining up the months, years, and codes ensures that the aggregated data is in fact correct (I tested this by aggregating ALL occurences of each offense code, then iterating through them, tallying them up, and comparing the values, which is actually demonstrated in the next cell). Since Jupyter decided not to return the aggregated table, I just ran it in the SQL interface, which worked perfectly, albeit taking way too long. Given this, I just exported the results as a csv and imported that back into Jupyter.

## Code Cell 3: Manipulating the Data
### The only cell I would advise running
This was where I showcased multiple ways of finding certain key data values, showing trends over time, and picking out corresponding values from other notable information in the aggregated dataset. The first part of the program demonstrates selecting the maximum and minimum number of crime incidents in a month, catching the count, timestamp, and offense code of both the maximum and minimum number of occurences found in the data. The second part demostrated an iterative loop on a certain offense code, catching the timestamp, and the amount of incidents for only that code, and returning the total number of occurences in the entire set. The third part of the code demonstrates comparing values of economic indicators and finding the corresponding incident data point for a certain code (yes I could have done a list and iterated through the list to find the corresponding codes but this project took long enough to run in its present state).

## Cut For Time
Originally, I also wanted to include matplotlib diagrams on indicators vs incidents, as well as manipulation and plots in RStudio. However, given the concepts already demonstrated in the project, as well as the looming deadline, that will just have to wait.
