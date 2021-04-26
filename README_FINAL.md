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


  
  

  
  

### Analysis of Outcomes Based on Goals

### Challenges and Difficulties Encountered

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
