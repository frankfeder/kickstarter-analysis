# Kickstarting with Excel
### Analysis by Frank Feder for UT Austin Data Analytics Bootcamp December 2020
## Overview of Project
This analysis is intended to visualize insights about "theater/play" category Kickstarter projects, focusing on correlating Date Created and Fundraising Goals with the success of a project in that category.

### Purpose

## Analysis and Challenges
Analysis was performed using basic excel summary and visualization functions. Most of the data was provided in a usable format, but some light feature engineering was required to turn unicode dates into more readable format, as well as extract Years for analysis.
If you run into a Unix date that looks something like "1402949760" while working in Excel, you can convert that to a more human-readable format like so:
```
=(((<UNIX-DATED CELL LOCATION>/60)/60)/24)+DATE(1970,1,1)
```
### Analysis of Outcomes Based on Launch Date
[Outcomes Based on Launch Date Graph](resources/Theater_Outcomes_vs_Launch.png)
### Analysis of Outcomes Based on Goals
[Outcomes Based on Goals](resources/Outcomes_vs_Goals.png)
### Challenges and Difficulties Encountered
When developing a new column for Average Pledge, some records will create #DIV/0 error, as some projects in the dataset have not recieved any pledges.
To handle these errors, use IFERROR(), as below:
```
=IFERROR(RE19/L19,0)
```
This will replace the error with "0" so subsequent analyses can reference the column as a numerical type without issues.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
	1. The summer months (May-August) have relatively more Theater category KS project launches than others.
	2. May is the most favorable month of the year to launch a Theater KS campaign. It is the month with the most total successful launched projects, but also historically has best ratio of succeeded:failed theater campaigns launched.

- What can you conclude about the Outcomes based on Goals?
	- Theater campaigns that set a goal of over $15000 historically succeed more than those over $15000. While the graph suggests that there might be a potential "sweet spot" for a large production in the $35000-$45000 range, there are only 6 theater projects in our dataset with goals in that range, which is insufficient to model a prediction. Although historically sub-$15000 theater campaigns tend to succeed more than they fail, the difference is more favorable under $5,000.

- What are some limitations of this dataset?
	- This analysis lacks more granular data on how time-to-deadline impacts fundraising. Some of the campaigns in the dataset barely met their goal, and had a very low Backers count - suggesting that at the last moment, someone may have donated a large sum just to make sure the goal was reached before the deadline. Unless the client specified that this was part of her fundraising strategy, more accurate recommendations could be made by filtering those campaigns out.
	- This data would also be more helpful if it had more details about each campaign. Particularly for the Theater side of this analysis, it seems like the summer months are best for fundraising plays. This surge may be due to an increase in outdoors productions being marketed to backers who want to enjoy the warm weather - if our client was looking to fund an indoor production, a May launch recommendation could be less defensible.

- What are some other possible tables and/or graphs that we could create?
	- Future analyses could focus on total length of campaign vs. average backer pledge (using end date included in data). From a marketing perspective, it might also be helpful to drill into the length of the "blurb" and its impact on success or amount raised.
