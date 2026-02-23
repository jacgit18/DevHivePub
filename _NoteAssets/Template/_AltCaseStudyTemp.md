---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
##### How does a bike-share navigate speedy success?

ASK  
  
Guiding Question:  
What is the primary business goal of Cyclistic's marketing team?  
  
What specific differences in usage patterns between annual members and casual riders are we trying to identify?  
  
What key metrics and performance indicators are relevant for this analysis?  
  
  
Key tasks:  
● Identify the business task  
● Consider key stakeholders  
● Define Scope like date range to focus on  
  
  
Deliverables - Business Task:  
  
Understand the differences in bike usage patterns between annual members and casual riders.  
  
Use these insights to create marketing strategies aimed at converting casual riders into annual members.  
  
  
Key stakeholders:  
  
Lily Moreno, Director of Marketing, oversees the development of marketing campaigns.  
  
The Cyclistic marketing analytics team collects, analyzes, and reports data to guide marketing strategies.  
  
The Cyclistic executive team will approve the recommended marketing program.  
  
  
  
PREPARE  
[https://www.coursera.org/lecture/data-preparation/what-is-bad-data-lHirM](https://www.coursera.org/lecture/data-preparation/what-is-bad-data-lHirM)  
  
Gather historical bike trip data, user demographics, and any other relevant data sources.  
  
  
Guiding Question:  
  
What data sources are available for this analysis?  
  
Is the data complete, accurate, and up-to-date?  
  
What additional data might be needed to gain deeper insights?  
  
[https://divvy-tripdata.s3.amazonaws.com/index.html](https://divvy-tripdata.s3.amazonaws.com/index.html)  
  
  
Key tasks:  
● Review data determine credibility  
● Download data and store it appropriately.  
● Identify how it’s organized.  
● Sort, and Filter data if it isn't already  
● Maybe pull in additional data if it makes sense  
  
  
Deliverables - Business Task:  
● list all data used  
  
  
PROCESS  
  
Have you ensured your data’s integrity?  
  
Key tasks:  
● Check the data for errors.  
● Choose your tools.  
● Transform the data so you can work with it effectively.  
● Clean and preprocess the data to handle missing values, remove duplicates, and format data consistently.  
  
Deliverables - Business Task:  
  
● Document all cleaning and manipulation steps to ensure reproducibility.  
  
  
  
Open your spreadsheet and create a column called ride_length. Calculate the length of each ride by subtracting the column started_at from the column ended_at (for example, =D2-C2) and format as HH:MM:SS using Format > Cells > Time > 37:30:55.  
  
Create a column called day_of_week, and calculate the day of the week that each ride started using the WEEKDAY command (for example, =WEEKDAY(C2,1)) in each file. Format as General or as a number with no decimals, noting that 1 = Sunday and 7 =  
Saturday.  
  
  
  
  
ANALYZE  
  
Guiding Question:  
  
How do trip durations compare between annual members and casual riders?  
At what times of day do annual members and casual riders typically use the bikes?  
Are there specific days of the week when casual riders are more active?  
Do annual members and casual riders prefer different types of bikes (e.g., traditional vs. assistive)?  
What routes or stations are most popular among annual members versus casual riders?  
How does weather or seasonality affect the usage patterns of each group?  
What factors seem to influence casual riders to convert to annual members?  
  
Key tasks:  
● Aggregate your data so it’s useful and accessible.  
● Organize and format your data.  
● Perform calculations.  
● Identify trends and relationships.  
  
Compare usage metrics such as trip duration, frequency, time of day, and days of the week between annual members and casual riders.  
  
  
Deliverables - Business Task:  
● A summary of your analysis  
  
  
1. Where relevant, make columns consistent and combine them into a single worksheet.  
2. Clean and transform your data to prepare for analysis.  
3. Conduct descriptive analysis.  
4. Run a few calculations in one file to get a better sense of the data layout. Options:  
● Calculate the mean of ride_length  
● Calculate the max ride_length  
● Calculate the mode of day_of_week  
  
  
5. Create a pivot table to quickly calculate and visualize the data. Options:  
● Calculate the average ride_length for members and casual riders. Try rows =  
member_casual; Values = Average of ride_length.  
● Calculate the average ride_length for users by day_of_week. Try columns =  
day_of_week; Rows = member_casual; Values = Average of ride_length.  
● Calculate the number of rides for users by day_of_week by adding Count of  
trip_id to Values.  
  
  
SHARE  
  
Guiding Question:  
What are the key findings and insights from the analysis?  
  
How can these insights be effectively communicated to the stakeholders  
?  
What visualizations will best illustrate the differences in usage patterns?  
  
Key tasks:  
● Determine the best way to share your findings.  
● Create effective data visualizations.  
● Present your findings.  
● Ensure your work is accessible.  
  
  
Deliverables - Business Task:  
  
● Supporting visualizations and key findings  
  
  
ACT present data and host findings somewhere like github or kaggle or viz  
  
What recommendations can be made based on the analysis?  
  
How can these recommendations be implemented in Cyclistic's marketing strategy?  
  
What potential impact will these recommendations have on converting casual riders into annual members?  
  
  
Based on the analysis, provide actionable recommendations for the marketing team to target casual riders.  
  
Consider strategies like targeted promotions, loyalty programs, and personalized communication to encourage casual riders to become annual members.