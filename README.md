# Surf's Up
Report prepared for Module 9 challenge by Hannah Wikum - February 2022

## Resources
Data Source: hawaii.sqlite (provided)

Software: Jupyter Notebook, Visual Studio Code, Python 3.7 Anaconda Development Environment with numpy, pandas, sqlalchemy
___
## Overview
### Background
This analysis was completed for W. Avy to help inform if the proposed surf and ice cream shop in Oahu is sustainable year-round. I used the provided sqlite database with data from 1/1/2010 to 8/23/2017 to compare the statistics for observed temperatures over the years in the month of June versus December.

### Analysis
To complete the statistical analysis, I first had to filter the date column in the Measurements table of the database to isolate observations in either June or December. Since I needed to find temperatures in the same month across multiple years, I used the extract function from sqlalchemy to isolate for the 6th or 12th month of the year. Here is a sample of my code:

  _Code to filter for June temperatures_
  
  ![image](https://user-images.githubusercontent.com/93058069/153725977-2662eccd-4eaf-420d-81de-a219cb24b00c.png)
  
After isolating the data for a particular month, I added .all() to the end to convert the results to a list. I used the DataFrame feature of pandas to convert the list to a DataFrame with columns for date and temperature. Finally, I used df.describe() to get the summary statistics for the analysis.
___
## Results
After completing the analysis for each month as described above, I was able to see the output of summary statistics for both months to compare the key differences between weather in June versus December for Oahu. The image below shows the output of the summary statistics for both months:

  _June vs December Temperature Statistics_
  
  ![image](https://user-images.githubusercontent.com/93058069/153726303-e32345c5-7a3e-4788-becc-da7b2cc45240.png)

Here are a few of the key differences:

  * The mean temperature for December temperature observations are (predictably) colder than in June. The mean temperature is 3.9 degrees colder in December than in June.
  
  * The median temperature for December is also colder than in June. The median temperature for December was 71 degrees, which is 4 degrees cooler than June's 75 degrees.

  * The minimum temperature for June is a lot warmer than in December. For the records observed in the month of June, the coldest temperature was 64 degrees. For December, the coldest was 56 degrees. That is a full 8 degree difference in minimum temperatures. Beyond that, 25% of December observations are at 69 degrees or colder, which some might consider too cold to surf of eat ice cream, while the first quartile for June is 73 degrees.

  * You may also note that December has fewer recorded observations than June. This can be attributed to the 1/1/2010-8/23/2017 date range of the data, which means that we have eight years worth of observations for June, but only seven for December. The number of years and temperature observations for both months makes me feel confident using the statistics anyway, but wanted to note why the counts have such a difference.
___
## Summary
In summary, after conducting the multi-year temperature analysis for the months June and December in Oahu, the temperature statistics show that December is cooler than June. From mean to median, min to max, and every quartile in between, December statistics were all colder than what was observed in June.

To expand on the analysis, I ran two additional queries to help aid W. Avy in making a decision if the surf/ice cream shop is a viable year-round business.

_Precipitation_

Another data point I wanted to add to the analysis involved the number of observations with precipitation (assumed to be rain given the temperature statistics). I used a similar code shown in the Analysis section to filter out observations in the month of June or December, but this time on precipitation instead of observered temperature. Here is my code and the results:

  _Code to Determine % Observations with Rain in June_

  ![image](https://user-images.githubusercontent.com/93058069/153727152-698b2b4a-95c7-48b7-8668-5763e4fbaed6.png)
  
This section of code returend 54.5% for June and 59.0% for December. Not only is December colder, but precipitation occurs more often than in June. Customers would likely be less inclined to surf if there is precipitation.

_Temperature_

To round out the analysis, I added one final query on temperature to determine how consistent average temperatures are across the island in June and December by weather station. I built a query to take the average temperature for the month of June and grouped by station, before ordering the stations by highest to lowest average temperature for the month. I repeated for December by updating the month in the filter(extract()) part of the code to 12 instead of 6. Here is my code and the output:

  _Code to Determine Avg Temp by Station in June_
 
  ![image](https://user-images.githubusercontent.com/93058069/153730413-ae825267-7a1c-49e8-917e-10f4b024b4dd.png)

The results showed the highest average temperatures in June were recorded at station USC00519397 of 77.6 degrees. The lowest average was only 71.9 degrees, which is a difference of over 5 degrees. In December, the highest average temp recorded was 73.2 degrees, while the lowest was 69.3 degrees, which is a smaller variance in averages between stations than in June. Here is the code and results for December:

  _Code to Determine Avg Temp by Station in December_
  
  ![image](https://user-images.githubusercontent.com/93058069/153730649-bb925e65-99f9-4809-9130-d54aa8eba4b5.png)

  
 
 


   
   
