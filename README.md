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

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/GDP%20Column.png)

Finally, the minimum, maximum, and average life expectancy and GDP was generated for the entire data set as well as each country (details in the ipynb file).

## Data Analysis
Once the data was prepared, line and scatter charts were made to help visualize any trends in the data. First, the life expectancies and GDPs of all six countries were plotted to see how they compared to one another. Below is the code for the GDP chart, with the life expectancy chart created in a similar manner, as well as the charts themselves.

```
# Plot comparison of GDP across the countries
plt.plot(chile["Year"], chile["GDP_USD_Trillions"])
plt.plot(china["Year"], china["GDP_USD_Trillions"])
plt.plot(germany["Year"], germany["GDP_USD_Trillions"])
plt.plot(mexico["Year"], mexico["GDP_USD_Trillions"])
plt.plot(usa["Year"], usa["GDP_USD_Trillions"])
plt.plot(zimbabwe["Year"], zimbabwe["GDP_USD_Trillions"])
plt.title("Country GDP (USD Trillions)")
plt.legend(["Chile", "China", "Germany", "Mexico", "USA", "Zimbabwe"], bbox_to_anchor = (1, 1), loc = "upper left")
plt.show()
```

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/GDP%20Comparison.png)

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/Life%20Expectancy%20Comparison.png)

The line charts show that in the years surveyed, the US has always had the highest GDP, while Mexico, Chile, and Zimbabwe had had the lowest. Germany had the second highest GDP until about 2007, when China's GDP massively surged and overtook it. Interestingly, these trends are not fully reflected in the life expectancy. Germany, Chile, the US, Mexico, and China all saw relatively small life expectancy gains from their initial expectancies in the 70-80 year range, while Zimbabwe saw about a 15 year increase in life expectancy, although by 2015 there was still approximately a 15 year difference in its life expectancy compared to those of the other surveyed countries.

After comparing trends across countries, scatter plots were made to check the relationship between GDP and life expectancy in each country. The code and plots follow below.

```
plt.scatter(chile["Life_Expectancy"], chile["GDP_USD_Trillions"])
plt.xlabel("Life Expectancy")
plt.ylabel("GDP (USD Trillions)")
plt.title("Life Expectancy vs. GDP (Chile)")
plt.show()
```

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/Chile%20Life%20Expectancy%20vs%20GDP.png)

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/China%20Life%20Expectancy%20vs%20GDP.png)

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/Germany%20Life%20Expectancy%20vs%20GDP.png)

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/Germany%20Life%20Expectancy%20vs%20GDP.png)

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/Germany%20Life%20Expectancy%20vs%20GDP.png)

![This is an image](https://github.com/EricaEidelman/GDP_LifeExpectancy/blob/main/Images/Zimbabwe%20Life%20Expectancy%20vs%20GDP.png)

There are a few interesting observations to be gleaned from these plots. As could be expected, for most of the countries life expectancy and GDP are positively linearly correlated; as one increases, so does the other. This makes sense, as a richer country will have more funds to invest in the health of its citizens. Zimbabwe is the one exception, with life expectancy increasing even as GDP remains flat (with only one data point seeing a drop in life expectancy). Although Zimbabwe's GDP does double, it stays flat at the increased level even as life expectancy increases again.
