# MODULE 1: Kickstarting with Excel

One of the earliest applications to combine spreadsheets with graphs and charts was Excel, which is still one of the most used data analysis systems today. Excel is a fantastic tool for both novice and experienced users because of its adaptability and simplicity. Excel is also incredibly adaptable. It may be used for a variety of purposes, including business, schoolwork, and personal record-keeping.

We'll discuss advanced Microsoft Excel formulae and vocabulary in this session, use Excel pivot charts to make interactive charts and graphs, and organize data using filters and conditional formatting. We may organize and display data using these algorithms, charts, and filters to identify trends.

Consider a financial adviser who creates dynamic charts from spreadsheets for presentations or an account manager who can combine information from many sheets into a single, easily understood set of takeaways. What features do they share? To improve their analysis and create a data-driven narrative, they are both utilizing Excel's sophisticated visualization features.

With Excel, data is easily organized, filtered, sorted, and visualized all within this single program. It takes much of the busywork out of the number-crunching that data analysis involves. It's no wonder that Excel skills are in high demand. 

Let's take an in-depth look at advanced Excel tools.

## Overview of the Analysis
In this module, I helped an up-and-coming playwright, Louise, who wants to start a crowdfunding campaign to help fund her play, Fever. She is estimating a budget of over $10,000 USD and is understandably hesitant about jumping into her first fundraising campaign. So Louise decided to contact me, an Excel power user, to help her organize, sort, and analyze several thousand crowdfunding projects with 12 variables to uncover any hidden trends to determine whether there are specific factors that make a project’s campaign successful.

### Purpose
Louise will use these insights to plan her own campaign and set it up for success, mirroring other successful ones in the same category.

## Analysis and Challenges
After Louise’s play Fever came close to its fundraising goal in a short amount of time, she wanted to know how different campaigns fared in relation to their launch dates and their funding goals. Using the Kickstarter dataset that I’ve already combed through, I visualized campaign outcomes based on their launch dates and their funding goals.

### Analysis of Outcomes Based on Launch Date
For this analysis I wanted to know if there is a relationship between the month in which a campaign was created, and its outcome. Meaning if there is a higher probability of success according to the month in which Louise launches her campaign. For this, as seen on Image 2.1.1 “Outcomes Based On Launch Date” Overview, a pivot table was created from the original data frame present in KickStarter sheet using parent category and years as filters, only including observations with “theater” as their parent category. I used “outcome” (I.e., successful, failed, canceled) as columns variables in my pivot table, the month in which the campaign was created and the number of plays (count) that had a certain outcome given a certain month of creation.

### Analysis of Outcomes Based on Goals
For this analysis I wanted to know if there is a relationship between the fundraising goal and its outcome. For this, as seen on Image 2.2.1 “Outcomes Based On Goals” Overview, a summary table was created from the original data frame present in KickStarter sheet, using the columns: Goal, Number Successful, Number Failed, Number Canceled, Total Projects, Percentage Successful, Percentage Failed, and Percentage Canceled. This meant that I wanted to calculate the number of observations with a given outcome according to its original fundraising goal. For this, I had to segment fundraising goals into 12 buckets, starting from less than $1,000 to more than $50,000, mainly with $4,999 increments (except for the lower buckets). Using the =COUNTIFS() function I was able to count the number of observations with more than one filter parameter as input, using both the outcome column and the goal column from the original data frame present in the KickStarter sheet. Finally, I summed the number of observations for a given goal and calculated the percentage that each outcome represented given a certain goal.

### Challenges and Difficulties Encountered with Outcomes Based on Launch Date
After creating the pivot table, I wanted my chart to show the frequency of a certain outcome given the month in which the campaign was launched. Nevertheless, the pivot table displayed the information by years and then by quarter and finally by month (as seen on Image 2.1.2 “Outcomes Based On Launch Date” Challenges and Difficulties). What I had to do was to remove the “Años” and “Trimestres” filters that Excel automatically created for me in the rows section of the pivot table field list, and thus, only months would be automatically shown (Image 2.1.3 “Outcomes Based On Launch Date” Challenges and Difficulties).

### Challenges and Difficulties Encountered with Outcomes Based on Goals
While working on this analysis I encountered four main challenges:
i. I did not want to write down by hand the names of all of the 12 different buckets, so I
created two columns with the lower and upper bound of the bucket and used the =CONCAT() function using “ to ” as a separator.
ii. As it was my first time working with the =COUNTIFS() formula, I had trouble working with it. I read the documentation and noticed that the applied criterias must be applied to different columns in question.
iii. As not all buckets were separated by a linear difference, I had to fill in the filters (numbers, i.e., lower and upper bound of the bucket) by hand. Also, some criterias included greater or EQUAL than and others just greater than, which made the process manual.
iv. While running the formula for the rest of the columns I used the =UPPER() and the =REPLACE() formulas so the outcome could be extracted from the name of the column so I wouldn’t have to fill in manually the outcome for every cell.

## Results of the Analysis

- What are two conclusions you can draw about the Outcomes based on Launch Date?
1. My hypothesis was that the behavior of successful and failed theater plays would be opposite, meaning that in the months where there are more successful theater plays, there would be a drop in failed theater plays. Nevertheless, this is not the case, with successful and failed outcomes following the same trend no matter the month, successful theater plays having a more visible trend, suggesting that the database might be biased towards theater successful plays, i.e. The database has more
observations with successful outcomes.
2. Because of the conclusion stated in the previous point, launching a campaign in May
does not necessarily mean that there is a higher probability of success in May than in the rest of the months, as failed plays also reach a maximum during this month. Nevertheless, my recommendation would be to launch the campaign in May as the difference between successful and failed is greater, but having the previous point under consideration.

- What can you conclude about the Outcomes based on Goals?
1. I was not able to reproduce the exact same graph as the one presented on the Module 1 Challenge explanation. I believe the statement is not well described as it does not clearly state to filter out observations whose goals are not in USD. I did filter out everything besides USD and used “plays” as a sub category. It is also extremely weird that there are no canceled observations using the filters I used for the =COUNTIFS() formula.
2. Despite not having the exact same graph, the general tendency remains the same. Percentage failed and percentage successful are mutually exclusive, meaning they are inversely related. The general tendency says that as the monetary goal in USD increases, your probability of success decreases (and thus, your probability of failure increases). There is a point in the $25,000 USD to $29,000 USD where Louise has the same probability of succeeding and failing, every goal before this bucket is more probable for Louise to succeed and vice versa.

- What are some limitations of this dataset?
- What are some other possible tables and/or graphs that we could create?
1. I would like to analyze a base that has 50% successful, 50% failed or 33.33% successful, 33.33% failed, 33.33% canceled, this way we can really know with sufficient information the temporal tendency of failed and canceled theater plays.
2. I would like to further segment the base having a conversion of all goals to USD, this way we can compare pears with pears and apples with apples.
