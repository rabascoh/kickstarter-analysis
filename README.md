# Kickstarter Campaign Analysis

## Overview of Project
The purpose of this project is to gain insight into the success of various Kickstarter campaigns following Louise's Kickstarter campaign for her play *Fever*. The primary objective is to better understand how campaigns fared in her category, Theater, and determine which launch dates and funding goals were most successful. 

## Analysis and Challenges
### Outcomes Based on Launch Date
#### Analysis
To determine the outcomes by launch date, the sucessful, failed and canceled campaigns were grouped by the month the campaign was created. The campaigns were then filtered to only display the Theater parent category. The line chart below illustrates the Theater Outcomes based on Launch Date. 

![Outcomes Based on Launch Date](https://github.com/rabascoh/kickstarter-analysis/blob/main/Resources/Theater_Outcomes_vs_Launch.png)

#### Challenges
No challenges were encounted during analysis due to the datafile including outcomes and date created data for all Theater campaigns. Potential challenges could arise if there were missing data (e.g., missing start dates for some campaigns) or if the start date data were not previously converted to standard date format. If there were missing data, the campaigns would need to be filtered out and the updated base size/missing data exclusion would need to be noted. If the date data were still in UTC format, the following formula would need to be applied: =(((UTC_DATE/60)/60)/24)+DATE(1970,1,1). 

### Outcomes Based on Goals
#### Analysis
To determine the outcomes based on the campaign goals, a new table was created to pull in the number of successful, failed and canceled campaigns, total projects, and the percentage of successful, failed and canceled campaigns in the Plays subcategory across 12 bucketed goal ranges. The line chart below displays percentage of successful, failed and canceled campaigns for each goal range. 

![Outcomes Based on Goal](https://github.com/rabascoh/kickstarter-analysis/blob/main/Resources/Outcomes_vs_Goals.png)

#### Challenges
I encountered a challenge when creating the new Outcomes Based on Goals table. When calculating the Number of Successful, Failed and Canceled campaigns, the goal range calculations needed to include the lower and upper bounds of the range. Initially I had only included the upper bounds so the table was capturing all data up until the upper bounds. 
Example Error Formula: =COUNTIFS(Kickstarter!$F:$F,"successful", Kickstarter!$D:$D, "<=4999", Kickstarter!$O:$O,"plays")
To resolve this error, I added an additional field to the COUNTIFS statement for the lower bounds of the ranges. 
Example Corrected Formula: =COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D, ">=1000", Kickstarter!$D:$D, "<=4999", Kickstarter!$O:$O,"plays")

## Results
### Outcomes Based on Launch Date
The following two conclusions can be drawn from the analysis:
1. May is the best month to launch a Kickstarter campaign for Theater with the highest number of successful campaigns (*n*=111). 
2. December is the worst month to launch a Kickstarter campaign for Theater with the lowest number of successful campaings (*n*=37). There are almost as many failed campaigns (*n*=35) in December as successful campaigns. 

### Outcomes Based on Goals
The following conclusion can be drawn for the analysis: 
* The most successful Kickstarter campaigns for Plays are campaigns with goals below $15,000. The campaigns with the highest Percentage Successful (73%) are those with goals between $1,000 to $4,999. 

### Limitations
The dataset had the following limitations. 
* **Data Freshness** | The most recent data captured in this dataset is from 2017. Kickstarter campaign success factors have likely changed in the past four years. I would expect campaigns after March 2020 to behave differently than previous years due to the impace of COVID-19. 
* **Currency** | The dataset includes several currencies (e.g., USD, EUR, GPB), however the currency exchange rates were not factored into the analysis. In particular, for the Outcomes Based on Goals analysis, the dollar values were considered as though they were weighted equally. For future analyses, the dollar values should be converted to one currency prior to analysis to ensure the values are consistent across campaigns and regions. 

### Additional Tables / Graphs Recommendations

### Outcomes Based on Launch Date
For Outcomes Based on Launch Date, I recommend filtering to the 'play' subcategory rather than looking at the 'theater' parent category for this analysis to better understand how campaigns similar to Louise's performed. 

![Alt Outcomes Based on Launch Date](https://github.com/rabascoh/kickstarter-analysis/blob/main/Resources/Alt_Theater_Outcomes_vs_Launch.png)

### Outcomes Based on Goals
For Outcomes Based on Goals, I recommend using a bar or column chart to display the data rather than a line chart due to the x-axis capturing categorical data. A column chart, as pictured below, allows the reader to quickly determine the percentage of successful, failed and canceled campaigns for each goal range. 

![Alt Outcomes Based on Goals](https://github.com/rabascoh/kickstarter-analysis/blob/main/Resources/Alt_Outcomes_vs_Goals.png)




