## Netflix data Analysis 
### Big-Data Analysis with Python

![plot](https://wallpapercave.com/wp/wp5063339.png)

# This is Exploratory Data analysis using python of “Netflix movies & tv shows” dataset. The purpose of this project is to find out The Major Key insights using project-  

### -how dataset looks like, type of data, size and overview of dataset. 

### -Cleaning dataset by various methods like removing nulls and duplicates. 

### -Filtering, sorting and getting meaningful insights from data.  


## First Step includes Understanding Data using basic syntax-
### Basic functions used to explore data are-
* head() - It shows the first N rows in the data (by default, N=5).
* tail () - It shows the last N rows in the data (by default, N=5).
* shape - It shows the total no. of rows and no. of columns of the dataframe.
* size - To show No. of total values(elements) in the dataset.
* columns - To show each Column Name.
* dtypes - To show the data-type of each column.
* info() - To show indexes, columns, data-types of each column, memory at once.
* value_counts - In a column, it shows all the unique values with their count. It can be applied on a single column only.
* unique() - It shows the all unique values of the series.
* nunique() - It shows the total no. of unique values in the series.

## Second Step Includes Data Cleaning. 
* duplicated( ) - To check row wise and detect the Duplicate rows.
* isnull( ) - To show where Null value is present.
* dropna( ) - It drops the rows that contains all missing values.
* isin( ) - To show all records including particular elements.
* str.contains( ) - To get all records that contains a given string.
* str.split( ) - It splits a column's string into different columns.

## Third Step includes Analyzing data.
* to_datetime( ) - Converts the data-type of Date-Time Column into datetime[ns] datatype.
* dt.year.value_counts( ) - It counts the occurrence of all individual years in Time column.
* groupby( ) - Groupby is used to split the data into groups based on some criteria.
* sns.countplot(df['Col_name']) - To show the count of all unique values of any column in the form of bar graph.
* max( ), min( ) - It shows the maximum/minimum value of the series.
* mean( ) - It shows the mean value of the series.

## This Project includes Creating New Columns & Dataframe, Filtering (Single Column & Multiple Columns), Filtering with And and OR Seaborn Library - Bar Graphs
