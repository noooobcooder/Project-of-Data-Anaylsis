# Project-of-Data-Anaylsis

## Netflix Data Analysis 📊:  ##
This project performs an Exploratory Data Analysis (EDA) on Netflix data to gain insights into the movies and TV shows available on the platform.

## Key Objectives: ##
1)  Clean and prepare the raw data.

2)  Compare the number of movies vs. TV shows on Netflix.

3)  Identify the top content-producing countries.

4)  Understand the trend of content releases over the years.

5)  Analyze the distribution of title lengths.

## Key Findings: ##

1)  Missing data points were filled with "Unknown" to ensure data integrity.

2)  There are significantly more movies than TV shows on Netflix.

3)  The United States is the country that has produced the most content for the platform.

4)  The number of new releases has increased sharply in recent years, peaking around 2018.

## Visualizations (Graphs): ##

1)  The project includes several visualizations to make the data easy to understand:

2)   Movies vs. TV Shows: A bar chart comparing the total count of each content type.

3)  Release Trend: A line graph showing how content releases have changed over time.

4)  Top 10 Countries: A bar chart highlighting the top 10 countries with the most content.




## Netflix Data Analysis 📊 ##

## Importing Libraries ##
    import pandas as pd
This line imports the Pandas library and gives it a shorter name, pd. Pandas is an essential tool for working with structured data, like the kind found in a CSV file.

    import seaborn as sns
This imports the Seaborn library, which is great for creating beautiful and informative statistical graphs. We give it the shorter name sns.

    import matplotlib.pyplot as plt
This imports Matplotlib, another popular library for creating plots and charts. We use plt as its alias.

## Loading and Viewing Data ##
    df = pd.read_csv(...)
This command loads your CSV data file into a DataFrame, which is like a table or spreadsheet. We store this DataFrame in a variable named df.

    df.head(): 
This shows you the first 5 rows of your DataFrame. It's the quickest way to get a preview of your data and see what's inside.

    df.tail():
This does the opposite of head(), showing you the last 5 rows of the DataFrame.

    df.shape: 
This tells you the number of rows and columns in your DataFrame. For example, (8807, 12) means there are 8,807 rows and 12 columns.

    df.columns: 
This lists all the column names in your DataFrame. It's useful for checking the exact spelling of each column.

    df.info(): 
This gives you a summary of your DataFrame. It shows the data type of each column (like object for text or int64 for numbers) and tells you how many non-missing values are in each column. This is a very important step for data cleaning.

    df.describe():
This generates a statistical summary for only the numerical columns. It gives you information like the average (mean), minimum (min), and maximum (max) values.

## Data Cleaning and Preparation ##
    df.isnull().sum():
This is a powerful command that counts the number of missing values in each column. The output shows you exactly where the data is incomplete.

    df['director'].fillna("Unknown", inplace=True):
This command handles missing values. It finds all the empty spots (NaN) in the 'director' column and fills them with the word "Unknown". We use inplace=True to apply this change directly to the DataFrame. This same method is used for other columns like 'cast' and 'country'.

    df.to_csv("netflix_cleaned.csv", index=False): 
This saves your cleaned DataFrame into a new CSV file. The index=False part tells it not to save the row numbers as a new column in the file. This is a good practice so you don't have to repeat the cleaning steps.

## Data Exploration and Analysis ##
    df['title']: 
This is how you select a single column from your DataFrame.

    df[['title', 'type']]:  
You can also select multiple columns by putting their names in a list inside double brackets.

    df.iloc[0:5]:
This is a way to select data by its position. iloc means "integer location," and [0:5] selects the first five rows (from index 0 up to, but not including, 5).

    (df[df['type'] == 'Movie']): 
This is a filter. It selects all the rows where the value in the 'type' column is exactly 'Movie'.

     (df[df['release_year'] > 2018]):
Another filter that selects all content released in a year greater than 2018.

    df.sort_values(by='release_year', ascending=False):
This command sorts the entire DataFrame based on the 'release_year' column. ascending=False means it will sort from the newest year to the oldest.

     df['type'].unique(): 
This finds and lists all the unique values in the 'type' column. You can see that the only unique values are 'Movie' and 'TV Show'.

    df['type'].value_counts(): 
This counts how many times each unique value appears. It's a quick way to see the total number of movies and TV shows.

    df.groupby('release_year')['show_id'].count():
This command groups the data by release_year and then counts the number of show_ids in each group. It's used to find out how many titles were released in each year.

    df['title_length'] = df['title'].apply(len):
This creates a new column called title_length. The .apply(len) part goes through every title and counts the number of characters in it, then stores that number in the new column.

    df['release_year'].value_counts().sort_index().plot(kind='line', ...):
This code creates the line graph. It counts titles by year, sorts the years, and then plots the result as a line to show the trend.

     sns.barplot(x=..., y=..., palette=...): 
This uses Seaborn to create a bar chart. It takes the data for your x and y axes and a palette for colors to create the visualization.

    sns.histplot(df['title'].apply(len), ...): 
This creates a histogram, which is a type of bar chart that shows the distribution of numerical data. In this case, it shows how often different title lengths appear.


