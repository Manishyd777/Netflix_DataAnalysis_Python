## Netflix Dataset
### Big-Data Analysis with Python
![1.png](attachment:1.png)
This Netflix Dataset has information about the TV Shows and Movies available on Netflix till 2021.

This dataset is collected from Flixable which is a third-party Netflix search engine, and available on Kaggle website for free.
-------
# Importing the dataset
import pandas as pd
data = pd.read_csv(r"C:\Users\ROHIT GREWAL\Desktop\DSL\Videos\Data-Sets\8. Netflix Dataset.csv")                     # to import pandas library
data

#### Getting some basic information about the dataset
### 1. head()
data.head()                                     # to show top-5 records of the dataset
### 2. tail()

data.tail()                                      # to show bottom-5 records of dataset
### 3. shape
data.shape                                      # to show the No. of Rows and Columns
### 4. size
data.size                                      # to show No. of total values(elements) in the dataset
### 5. columns
data.columns                                   # to show each Column Name
### 7. dtypes
data.dtypes                                    # to show the data-type of each column
### 8. info()
data.info()                                   # To show indexes, columns, data-types of each column, memory at once
----
### Task.1. Is there any Duplicate Record in this dataset ? If yes, then remove the duplicate records.
### duplicate()
data.head()
data.shape
data[data.duplicated()]                                         # To check row wise and detect the Duplicate rows  
data.drop_duplicates(inplace = True)                                # To Remove the Duplicate rows permanently
data[data.duplicated()]
data.shape
----
### Task.2. Is there any Null Value present in any column ? Show with Heat-map.
### isnull()
data.head()
data.isnull()                                               # To show where Null value is present
data.isnull().sum()                                               # To show the count of Null values in each column
### seaborn library (heat-map)
import seaborn as sns                                               # To import Seaborn library
sns.heatmap(data.isnull())                                               # Using heat-map to show null values count
----
----
### Q.1. For 'House of Cards', what is the Show Id and Who is the Director of this show ?
### isin()
data.head()
data[data['Title'].isin(['House of Cards'])]       #  To show all records of a particular item in any column
### str.contains()
data[data['Title'].str.contains('House of Cards')]          #  To show all records of a particular string in any column
----
### Q.2. In which year highest number of the TV Shows & Movies were released ? Show with Bar Graph.
### dtypes
data.dtypes
### to_datetime
data['Date_N'] = pd.to_datetime(data['Release_Date'])
data.head()
data.dtypes

### dt.year.value_counts()
data['Date_N'].dt.year.value_counts()                # It counts the occurrence of all individual Years in Date column.
### Bar Graph
data['Date_N'].dt.year.value_counts().plot(kind='bar')
----
### Q.3. How many Movies & TV Shows are in the dataset ? Show with Bar Graph.
### groupby()
data.head(2)
data.groupby('Category').Category.count()                 # To group all unique items of a column and show their count
### countplot()
sns.countplot(data['Category'])        # To show the count of all unique values of any column in the form of bar graph
----
### Q.4. Show all the Movies that were released in year 2000.
### Creating new column
# data.head()
data.head(2)
# data['Year'] = data['Date_N'].dt.year           # to create new Year column ; it will consider only year

data['Year'] = data['Date_N'].dt.year
# data.head(2)

data.head(2)
### Filtering
# data[ (data['Category']=='Movie') & (data['Year']==2020) ]

data[ (data['Category'] == 'Movie') & (data['Year']==2000) ]
data[ (data['Category'] == 'Movie') & (data['Year']==2020) ]
----
### Q.5. Show only the Titles of all TV Shows that were released in India only.
### Filtering
# data.head(2)

data.head(2)
# data [ (data['Category'] == 'TV Show') & (data['Country'] == 'India') ] ['Title']

data[ (data['Category']=='TV Show') & (data['Country']=='India') ] ['Title']
----
### Q.6. Show Top 10 Directors, who gave the highest number of TV Shows & Movies to Netflix ?
### value_counts()
# data['Director'].value_counts().head(10)

data.head(2)
data['Director'].value_counts().head(10)
----
#### Q.7. Show all the Records, where "Category is Movie and Type is Comedies" or "Country is United Kingdom".
### Filtering ( And, Or Operators )
# data[(data['Category']=='Movie') & (data['Type']=='Comedies') ]

data.head(2)
data[ (data['Category']=='Movie') & (data['Type']=='Comedies') ]
# data[(data['Category']=='Movie') & (data['Type']=='Comedies') | (data['Country']=='United Kingdom')]

data[ (data['Category']=='Movie') & (data['Type']=='Comedies') | (data['Country']=='United Kingdom')]
----
### Q.8. In how many movies/shows, Tom Cruise was cast ?
# data.head()

data.head(2)
### filtering
# data[data['Cast']=='Tom Cruise']

data[data['Cast'] == 'Tom Cruise']
### str.contains()
# data[data['Cast'].str.contains('Tom Cruise')]

data[data['Cast'].str.contains('Tom Cruise')]
### Creating new data-frame
# data_new = data.dropna()                       # It drops the rows that contains all or any missing values.

data_new = data.dropna()
# data_new.head(2)

data_new.head(2)
# data_new[data_new['Cast'].str.contains('Tom Cruise')]

data_new[data_new['Cast'].str.contains('Tom Cruise')]
----
### Q.9. What are the different Ratings defined by Netflix ?
### nunique()
# data.Rating.nunique()

data.head(2)
data['Rating'].nunique()
### unique()
# data.Rating.unique()

data['Rating'].unique()
#### Q.9.1. How many Movies got the 'TV-14' rating, in Canada ?
data.head(2)
# data[(data['Category']=='Movie') & (data['Rating'] == 'TV-14')].shape

data[(data['Category']=='Movie') & (data['Rating']=='TV-14')].shape
# data[(data['Category']=='Movie') & (data['Rating'] == 'TV-14') & (data['Country']=='Canada')].shape

data[(data['Category']=='Movie') & (data['Rating']=='TV-14') & (data['Country']=='Canada')].shape
#### Q.9.2. How many TV Show got the 'R' rating, after year 2018 ?
# data[(data['Category']=='TV Show') & (data['Rating'] == 'R')]

data.head(2)
data[(data['Category']=='TV Show') & (data['Rating']=='R')]
# data[(data['Category']=='TV Show') & (data['Rating'] == 'R') & (data['Year'] > 2018)]

data[(data['Category']=='TV Show') & (data['Rating']=='R') & (data['Year'] > 2018)]
----
### Q.10. What is the maximum duration of a Movie/Show on Netflix ?
# data.head(2)

data.head(2)
# data['Duration'].unique()

data.Duration.unique()
# data.Duration.dtypes

data.Duration.dtypes
### str.split()
data.head(2)
# data[['Minutes','Unit']] = data['Duration'].str.split(' ', expand=True)

data[['Minutes', 'Unit']] = data['Duration'].str.split(' ', expand = True)
# data.head(2)

data.head(2)
### max()
# data.Minutes.max()

data['Minutes'].max()
data['Minutes'].min()
data['Minutes'].mean()
data.dtypes
----
### Q.11. Which individual country has the Highest No. of TV Shows ?
# data.head(2)

data.head(2)
# data_tvshow = data[data['Category'] == 'TV Show']

data_tvshow = data[data['Category'] == 'TV Show']
# data_tvshow.head(2)

data_tvshow.head(2)
# data_tvshow.Country.value_counts()

data_tvshow.Country.value_counts()
# data_tvshow.Country.value_counts().head(1)

data_tvshow.Country.value_counts().head(1)
----
### Q.12. How can we sort the dataset by Year ?
# data.head(2)

data.head(2)
# data.sort_values(by='Year').head(2)

data.sort_values(by = 'Year')
# data.sort_values(by='Year', ascending=False).head(2)

data.sort_values(by = 'Year', ascending = False).head(10)
----
### Q.13. Find all the instances where : 
### Category is 'Movie' and Type is 'Dramas'
### or
###  Category is 'TV Show' & Type is 'Kids' TV'
data.head(2)
# data [(data['Category']=='Movie') & (data['Type']=='Dramas')].head(2)

data [ (data['Category']=='Movie') & (data['Type']=='Dramas') ].head(2)
# data[(data['Category']=='TV Show') & (data['Type']=="Kids' TV")].head(2)

data [ (data['Category']=='TV Show') & (data['Type']== "Kids' TV") ]
# data [(data['Category']=='Movie') & (data['Type']=='Dramas') | (data['Category']=='TV Show') & (data['Type']=="Kids' TV")].head(1)

data [ (data['Category']=='Movie') & (data['Type']=='Dramas') | (data['Category']=='TV Show') & (data['Type']== "Kids' TV") ]
----
----
----
----- ***** -----
By-
Rohit Grewal (Data Analyst)
