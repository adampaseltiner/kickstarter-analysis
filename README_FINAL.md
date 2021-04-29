# Kickstarting with Excel

## Overview of Project

### Purpose
  In this project I wanted to help Louise, a playright, best determine how to get her new play *Fever* crowdfunded on Kickstarter. To do so, I analyzed various data sets about crowdfunding campaigns to help illuminate what specific factors can help make a crowdfunding project successful. 

## Analysis and Challenges
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

  Calculating the standard deviation `=STDEV.P('Successful US Kickstarters'!D:D)`, upper and lower quartiles `=QUARTILE.EXC('Successful US Kickstarters'!D:D, 3)` and IQR of the pledged amounts shows us the measure of spread for the campaigns: since the mean pledged amount is close to the upper quartile of the pledged amount, that indicates a majority of campaigns are relatively similar in value. It also indicates that there are some outliers in the data set, meaning that some Kickstarter campaigns had incredibly high goals that ultimately failed.
  
  Since Louise is intruiged about launching her play in Great Britain, I decided to use the variance data to construct a `Box and Whisker` plot to finally help guide her in setting a goal amount, since visualizing it this way best shows the distribution of the data:
  
  ![Goals vs Pledged](https://user-images.githubusercontent.com/82347825/116341991-db94a780-a7af-11eb-9af1-dc2b63a1bf38.png)

  The main take away from the above chart is this: the mean campaign goal (as indicated by the 'x') shows that the average goal is around $4000, however, that is higher than the outliers for the amounts pledged. Additionally, half of the campaign goals are $2000 or less, which falls in (or near) the 3rd quartile of amounts pledged, which would indicate a high degree of success in that range.
  
  ### Challenges and Difficulties Encountered
Overall, the steps taken above was a rather familiar data analysis process for me, since I work with Excel often and am rather familiar with the formulas, charts and tables that we used. However, what was challenging for me at times was remembering that several of the open tabs had formulas and/or filtered data that affected other tables or charts, and needing to go back and clear them/alter them in order for my results to come back accurately.

  ---
  
## Results

### Analysis of Outcomes Based on Launch Date
  1. It is quite clear that the summer months of May-Jul (with May being the most succesful) is the best time of year to launch a successful Kickstarter campaign.
  2. The data for failed campaigns does not seem to vary much according to the time of year, indicating that the problems with those campaigns are most likely related to their goal amounts. 

### Analysis of Outcomes Based on Goals
  1. This graph is deceptive, since it does not take the variance data into account: if one were to look at the graph alone and not consider the total number of projects related to each goal range, one would think that campaigns with goals between $35-45k were just as likely to be funded as those with goals of $5000 and under. Relying solely upon this graph would be misleading and not as resourceful for Louise as a `Box and Whisker` plot.

### What are some limitations of this dataset?
  Considering the Kickstarter is a company where backers are given incentives based on the amount of dollars pledged, I think it would be helpful to  see what the reward ranges were for each campaign, and also what the rewards were. Lousie would definitely benefit from being able to get an idea of the types of rewards people were given for the price they were pledging.
  
- What are some other possible tables and/or graphs that we could create?
  I think it would be helpful to chart the success rate of Kickstarter campaigns based on the length of the campaign: does the campaign go only for a few weeks? A few months? Is there a certain campaign length that indicates the highest rate of success? Being able to definitively tell Louise that a one month long campaign yields the highest rate of success would certainly be beneficial to her planning.
