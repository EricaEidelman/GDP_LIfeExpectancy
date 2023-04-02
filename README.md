# GDP and Life Expectancy in Six Countries

## Overview
The purpose of this project is to look at the relationship between GDP and life expectancy in six countries - Chile, China, Germany, Mexico, the United States, and Zimbabwe - between the years of 2000 and 2015 with the goal of identifying any patterns or insights which can help to understand what drives an increase in the two measures. The data is relatively straighforward, showing the country, year, life expectancy, and GDP in USD for that year.

## Resources
Data Source: all_data.csv (from Codecademy)

Software: Python 3.7.6

## Initial Data Exploration
Data exploration started with checking the data types in the imported data frame as well as summarizing the data to understand the countries and years in scope, as per the below code snippet.

```
# Summarize countries and years in data
countries = census_df["Country"].tolist()
country = []
for item in countries:
    if item not in country:
        country.append(item)
        
years = census_df["Year"].tolist()
year = []
for item in years:
    if item not in year:
        year.append(item)
        
print(f"The dataset includes GDP and life expectancies on the following countries - {country} - for the years {year[0]} through {year[len(year)-1]}.")
```

This provided the following output: The dataset includes GDP and life expectancies on the following countries - ['Chile', 'China', 'Germany', 'Mexico', 'United States of America', 'Zimbabwe'] - for the years 2000 through 2015.

While the data was already relatively clean, the GDP column was initially in scientific notation, making it harder to understand the scale of the numbers. Further clean up included adding in another column showing GDP in trillions of USD.
