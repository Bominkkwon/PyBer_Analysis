# PyBer_Analysis



## Table of Contents
* [Project title](#project-title)
* [Technologies](#technologies)
* [Overview](#overview)
* [Analysis](#analysis)




## Project title
PyBer Analysis - Module 5 Challenge 

## Technologies
[Python](https://www.python.org/downloads/ "Download Python") 3.7.9.

## Overview 
PyBer, a ride-sharing app company valued at $2.3 billion, has assigned a project: analyze all the rideshare data ([PyBer ride data](https://github.com/Bominkkwon/PyBer_Analysis/blob/main/Resources/ride_data.csv), [City data](https://github.com/Bominkkwon/PyBer_Analysis/blob/main/Resources/city_data.csv), which consist of lists of cities, types of cities, dates, fares, ride ID, number of drivers from January to early May of 2019) and create a compelling visualization for the CEO. By creating visualizations of rideshare data for PyBer, the company would be able help improve access to ride-sharing services and determine affordability for underserved neighborhoods. One can also create a summary DataFrame of the ride-sharing data by city type and a multiple-line graph that shows the total weekly fares for each city type by using this script. This script is extremly helpful to summarize how the data differs by city type and how those differences can be used by decision-makers at PyBer.


(I have also noticed that when your Github Appearance setting (https://github.com/settings/appearance) is "Default Dark," some of the labels of these charts do not show on Readme.md-- Please switch to "Default Light" to resolve this issue)


## Results

In order to create visualizations, the script will merge the two datasets that were given and create the Rural, Suburban, and Urban DataFrames:
```Python
# Combine the data into a single dataset
pyber_data_df = pd.merge(ride_data_df, city_data_df, how="left", on=["city", "city"])

# Create the Urban, Suburban, Rural city DataFrames.
urban_cities_df = pyber_data_df[pyber_data_df["type"] == "Urban"]
suburban_cities_df = pyber_data_df[pyber_data_df["type"] == "Suburban"]
rural_cities_df = pyber_data_df[pyber_data_df["type"] == "Rural"]
```

![](analysis/Fig5.png) 

("% of Total Fares by City Type" (Fig 5))
```Python
sum_fares_by_type = pyber_data_df.groupby(["type"]).sum()["fare"]
total_fares = pyber_data_df["fare"].sum()
type_percents = 100 * sum_fares_by_type / total_fares
```
As the above pie chart is showing, more than half of total fares are charged in "Urban" areas and fares that were charged in "Rural" areas are less than 10% of fares charged in "Urban" areas.

![](analysis/Fig6.png)
![](analysis/Fig7.png)


