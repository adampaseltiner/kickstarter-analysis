# Kickstarting with Excel

## Overview of Project

### Purpose
  In this project I wanted to help Louise, a playright, best determine how to get her new play *Fever* crowdfunded on Kickstarter. To do so, I analyzed various data sets about crowdfunding campaigns to help illuminate what specific factors can help make a crowdfunding project successful. 

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
  To begin, I started by looking at Kickstarter campaigns that nearly missed their fundraising goals. To do so, I used the `ROUND` formula to analyze the amount pledged vs. the campaigns goal. For example: `=ROUND(E2/D2*100,0)`  
  
  Next, I wanted to see the average donations that backers contributed to a campaign, so I used a similar `ROUND` formula, however, I wanted to be sure to protect the formula from errors in case the campaign had zero backers behind it (since you can't divide by zero). Therefore, using the formula `=IFERROR(ROUND(E2/L2,2),0)` accurately gave me the average donations per backer.
  
  Now that I had added the above data to the spreadsheet, I decided to create a pivot table and pivot chart based on the outcomes of each of the parent campaign categories:
  
 ![Parent Category Outcomes](https://user-images.githubusercontent.com/82347825/116015908-fc6ec880-a608-11eb-84ee-ae965269ff4f.png)
  
  However, since Louise is most interested in theater (the parent category) and plays (the subcategory), I decided to filter out the extraneous parent and subcategories and focus solely on her main interests. Doing so resulted in this chart: 
 
 ![Count of Outcomes_Plays](https://user-images.githubusercontent.com/82347825/116016335-515f0e80-a60a-11eb-963d-64783d1597f0.png)
 
  After finding the specifics about the successes and failures by category, I decided it was important to then look at the timing of Kickstarter campaigns and whether or not (1) how long they last and (2) what time of year they are launched effect the campaign's outcome. Since the data provided to us was in Unix timestamp format, I needed to convert it to `DD/MM/YYYY` by using the formula `=(((J2/60)/60)/24)+DATE(1970,1,1)`. Using the converted data results for date and creating a new pivot chart to show the outcomes of Kickstarter campaign based on launch date yields the following chart, which clearly shows that a launch date in the month of May yields the largest number of successful campaigns: 
  
  ![Outcomes Based On Launch Date](https://user-images.githubusercontent.com/82347825/116021198-bb30e580-a615-11eb-90dd-f09c891e35cc.png)

  While in Edinburgh for a film festival, Lousie saw several plays and was curious about the details on how they got funded. To pull some of those numbers, we ran a `VLOOKUP` formula to pull the goals, pledged amounts, average donations and total number of backers. For example: `=VLOOKUP(A2,Kickstarter!B:D,3,FALSE)` yielded the goal amount for the play *Be Prepared*.
  
  Although the aforementioned data provided insight into the fundraising trends for Kickstarter campaigns, it was prudent to delve further into the statistical components of the data set to determine our conclusions rather than reading things at face value. Therefore, I chose to analyze the central tendencies to show the averages (`=MEAN` and `=MEDIAN` formulas) of the pledged goals:
  
 ![Descriptive Statistics 1](https://user-images.githubusercontent.com/82347825/116336580-d121e000-a7a6-11eb-8614-965bad5f116d.PNG)

  This table shows us that the average fundraising goal of a successful Kickstarter campaign is much lower (nearly half!) of that of a failed one. Looking at the averages, however, does not tell the entire story of the data, and therefore I decided to look at the measures of spread:
  
  ![Descriptive Statistics 2](https://user-images.githubusercontent.com/82347825/116336790-2827b500-a7a7-11eb-9d44-fe5505d2ce99.PNG)

  Calculating the standard deviation `=STDEV.P('Successful US Kickstarters'!D:D)`, upper and lower quartiles `=QUARTILE.EXC('Successful US Kickstarters'!D:D, 3)` and IQR of the pledged amount shows us the measure of spread for the campaigns: since the mean pledged amount is close to the upper quartile of the pledged amount, that indicates a majority of campaigns are relatively similar in value. It also indicates that there are some outliers in the data set, meaning that some Kickstarter campaigns had incredibly high goals that ultimately failed.
  
  Since Louise is intruiged about launching her play in Great Britain, I decided to use the variance data to construct a `Box and Whisker` plot to finally help guide her in setting a goal amount:
  
  ![Goals vs Pledged](https://user-images.githubusercontent.com/82347825/116341991-db94a780-a7af-11eb-9af1-dc2b63a1bf38.png)

  This type of chart can help display 
  
 
  

  
  

### Analysis of Outcomes Based on Goals

### Challenges and Difficulties Encountered

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
