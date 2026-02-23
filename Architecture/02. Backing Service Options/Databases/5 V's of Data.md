---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Break this up.
Purpose: This documentation discusses
Status: Refinement
Started: 2024-04-29
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Stages of Data 
#todo/BAU/noteRefine 
- [ ] clean up

Plan: Decide what kind of data is needed, how it will be managed, and who will be responsible for it.  
  
Capture: Collect or bring in data from a variety of different sources.  
  
Manage: Care for and maintain the data. This includes determining how and where it is stored and the tools used to do so.  
  
Analyze: Use the data to solve problems, make decisions, and support business goals.  
  
Archive: Keep relevant data stored for long-term and future reference.  
  
Destroy: Remove data from storage and delete any shared copies of the data.

keep [[Data Visualization Choices.pdf]] in mind


![[5 V.png]]


The 5 V's of data refer to five characteristics or dimensions that are used to describe and evaluate data:

1. **Volume**: Volume refers to the amount of data being generated, collected, stored, and processed. It can range from small amounts of data to massive volumes, often measured in terabytes, petabytes, or even exabytes. With the advent of big data technologies, organizations are dealing with increasingly large volumes of data, necessitating scalable storage and processing solutions.

2. **Velocity**: Velocity refers to the speed at which data is generated, collected, and processed. It encompasses both the rate of data ingestion and the frequency of data updates or changes. In today's fast-paced digital world, data is generated at unprecedented speeds from various sources such as sensors, social media, and transactional systems. Real-time or near-real-time processing is often required to derive timely insights and make informed decisions.

3. **Variety**: Variety refers to the diversity of data types and sources. Data comes in various formats, including structured, semi-structured, and unstructured data. It can originate from databases, files, streams, social media, sensors, and more. Managing and analyzing diverse data types require flexible data processing techniques and tools, such as schema-on-read approaches and NoSQL databases.

4. **Veracity**: Veracity refers to the quality, accuracy, and reliability of data. It encompasses factors such as data consistency, completeness, and trustworthiness. Inaccurate or inconsistent data can lead to erroneous insights and decisions, emphasizing the importance of data quality assurance processes, data governance frameworks, and data cleansing techniques.

5. **Value**: Value refers to the usefulness or relevance of data in achieving business objectives and deriving actionable insights. It's essential to extract meaningful insights and value from data to drive informed decision-making, optimize processes, improve customer experiences, and gain competitive advantages. Data analytics, machine learning, and data visualization techniques are employed to uncover insights and extract value from data.

By considering these five dimensions of data—volume, velocity, variety, veracity, and value—organizations can better understand, manage, and leverage their data assets to drive business success and innovation.

## Quantitative & Qualitative Data

![[Pasted image 20240429083438.png]]


Qualitative data:  
  
Is also called categorical data  
Represents the characteristics, attributes, properties, and qualities of things  
Describes data using language (rather than numbers), such as smell, location, color, texture, marital status, and so on


# Data analytics answers questions


In a constantly changing business environment, it can be hard to predict the next move. That’s where data analytics comes in. A successful data analytics initiative can provide a clear picture of where you are, where you have been, and where you should go.

The information technology (IT) industry typically recognizes four types of data analytics:

- Descriptive analytics
- Diagnostic analytics
- Predictive analytics
- Prescriptive analytics 

Each type of data analytics has a different goal and a different place in the data analysis process, and answers a specific question. Take a moment to view the following diagram, which clarifies the degree of complexity and added-value contribution for each of the four data analytics types.


![[2024-04-29 08.48.38 ole03.yourlearning.ibm.com 56db9bc4e512.png]]
### Descriptive analytics: What is happening?

Descriptive analytics is the simplest and most common type of data analytics.

Descriptive analytics answers the question, “What is happening?”. It provides a snapshot of business trends and patterns and uses historical and current data.

Descriptive analytics manipulates raw data from multiple sources to give a data analyst valuable insights into the past and a view of key metrics within a business. 

These findings might signal that something is right or wrong but not explain why. However, the findings can help to determine what the biggest issues are and where to start investigating!

  

Here are some examples of data used for descriptive analytics:

- The number of subscribers for a service
- Customer satisfaction survey data
- Monthly revenue reports
- Daily stock reports
- Demographic data about a business’ customer population, for instance, data that indicates that 30% of customers are self-employed

### Diagnostic analytics: Why is it happening?

After asking the question, “What is happening?”, the next step is to dive deeper and ask “why?”, such as,  “Why are trends and patterns happening?” This is where diagnostic analytics comes in.

Diagnostic analytics takes the insights found from descriptive analytics and drills down to find the causes of specific problems.

Businesses use of diagnostic analytics because it creates more connections between data and identifies patterns of behavior.

  

Here are some examples of diagnostic analytics:

- A freight company investigates the cause of slow shipments in a certain region.
- A healthcare company examines diagnoses and prescribed medications to identify the influence of medications.
- An IT company analyzes server ticket data to identify a small number of servers causing the bulk of an organization’s service outages.

### Predictive analytics: What is likely to happen in the future?

Predictive analytics is about forecasting. This type of analytics uses historical data to make predictions about the future. Whether it’s the likelihood of a future event, forecasting a quantifiable amount, or estimating a point in time at which something might happen – these are all done through predictive models.

In a world of great uncertainty, being able to predict allows businesses to make better decisions.

This type of analytics is more advanced and can often depend on machine learning and deep learning.

  

Here are some examples of diagnostic analytics:

- A software company uses customer segmentation to determine sales leads.
- An automotive manufacturer forecasts the failure rate of a specific vehicle part to determine recommended service actions.
- A weather forecaster analyzes current weather conditions in one part of the world to determine future weather conditions in other parts of the world.

### Prescriptive analytics: What should happen?

Prescriptive analytics combines the insight from all previous data analyses to determine a course of action to take to address a problem or make a decision.

The purpose of prescriptive analytics is to prescribe what action to take to eliminate a future problem or take full advantage of a promising trend.

Prescriptive analytics is typically used for a host of actions, versus an individual action. This requires a major commitment from businesses to put forth the strategy, effort, and resources. As technology continues to improve and more professionals are educated in data, more companies will enter this data-driven realm.

Prescriptive analytics uses advanced tools and technologies, like machine learning, business rules, and algorithms. This makes prescriptive analytics sophisticated to implement and manage.

  

Here are some examples of prescriptive analytics:

- A traffic application that helps people choose the best route home and considers the distance of each route, the speed at which one can travel on each road and, crucially, the current traffic constraints
- An exam timetable that checks if students have conflicting schedules
- Artificial intelligence (AI) systems from data-driven companies like Facebook, TikTok, and Netflix


**Wide data(A lot of columns) is preferred when**
  
Creating tables and charts with a few variables about each subject  
  
Comparing straightforward line graphs  
  
  
  
**Long data is preferred when**
  
Storing a lot of variables about each subject. For example, 60 years worth of interest rates for each bank  
  
Performing advanced statistical analysis or graphing



# Types of visualizations

![[unnamed.png]]

Data analysts use specific charts to visualize quantitative and qualitative data. The following image contains common charts for visualizing these two types of data. Conceptual charts can show either quantitative or qualitative data. Take a moment to study them.

![[2024-04-29 09.19.37 ole03.yourlearning.ibm.com 3498cf71ef62.png]]


![[2024-04-29 09.20.51 ole03.yourlearning.ibm.com 7506435756b1.png]]


![[2024-04-29 12.17.59 ole03.yourlearning.ibm.com bbc37cca3a46.png]]


Cross-Industry Standard Process for Data Mining

![[2024-04-29 12.29.34 ole03.yourlearning.ibm.com d5aa41266def.png]]

**Knowledge Discovery in Database**

![[2024-04-29 12.32.39 ole03.yourlearning.ibm.com 70d109272946.png]]

SEMMA 

![[2024-04-29 12.35.41 ole03.yourlearning.ibm.com 978b0783f224.png]]