# An Analysis of Kickstarter Campaigns

## Overview of Project
  - Analyze the trend of success and failures of kickstarter projects based on when they are launch and what range of goals are more likely to succeed.

### Purpose
  - Determine which period of time for projects launched are more likely to reach their goals.
  - Determine if the goals set affects the odds of success or failure on kickstarter.

## Analysis and Challenges

### Outcomes Based on Launch Dates
  - First I took this datasheet to begin my analysis. [Kickstarter Date]()
  - To begin the analysis of outcomes based on launch dates I first had to segment out from categories into subcategories using the delimiter function under the "Convert Text to Columns Wizard"
  - After segmenting out this subcategories I was than able to create a pivot table with the fields being filled out as such:
    1.) Outcomes goes under Columns and Values
    2.) Date created conversion goes under Rows
    3.) Parent Category and Years goes under the Filter field
    4.) In the pivot table set the Parent Category as 'theater'
  - After applying the filters and applying the data into a chart it should have an outcome that looks like [this](resources/Theater_Outcomes_vs_Launch.png)
  - Looking at the chart it becomes obvious that for theatre projects that are launched in the first half of the year are more likely to succeed with the success rate gradually dropping lower after the month of May.

### Analysis of Outcomes Based on Goals
  - To create the analysis of outcomes based on Goals I had to first segment out all the projects into different goal tiers. This was to make it easier to see which goal tier would have higher odds of succeeding.
  - After setting the goals tiers to jump by $5,000 per section I am able to use the COUNTIFS function in excel to pull data from the main excel sheet.
    - For successes I used this COUNTIFS formula: =COUNTIFS(Kickstarter!$D:$D,"<1000",Kickstarter!$R:$R,"plays",Kickstarter!$F:$F,"successful")
    - For failures I used: =COUNTIFS(Kickstarter!$D:$D,"<1000",Kickstarter!$R:$R,"plays",Kickstarter!$F:$F,"failed")
    - For Canceled I used: =COUNTIFS(Kickstarter!$D:$D,"<1000",Kickstarter!$R:$R,"plays",Kickstarter!$F:$F,"canceled")
  - Using the SUM function I totaled the amount of projects into its own column and use that number to calculate the percentage of success and failures for each tier.
  - I then plugged this data into a line table using the percentage of success as the y-axis and the dollar amount tiers into the x-axis. The table came out looking like [this](resources/Outcomes_vs_Goals.png)
### Challenges and Difficulties Encountered
 - Challenges encountered were some personal errors in following instructions for deliverable 2. Initially, I had the COUNTIFS filtering out specifically for projects launched in USD. The equation was inputted as:
    - "=COUNTIFS(Kickstarter!$D:$D,">=30000",Kickstarter!$D:$D,"<35000",Kickstarter!$H:$H,"USD",Kickstarter!$R:$R,"plays",Kickstarter!$F:$F,"successful")""
  - Which led my outcome chart to look like [this](resources/Bad Data.png). This data was completely incorrect as it only took into account that were launched in USD and not a worldwide tally of projects.
## Results

### Outcomes Based on Launch Date
  - We can see that specifically for theater projects there were equal amounts of projects launched during the first and second half of the year. Of those however, project that were launched in the first half of the year were more likely to succeed.
  - May is when the success of theater projects launched reaches its peak with the successful project almost doubling that of failures. Based on this data we can conclude that if you are launching a theater project it would be better to launch it either in the first half of the year or specfically in the month of May.
  - Projects that are launched in December have an almost 50% chance of succeeding or failing.

### Outcomes Based on Goals
- Project with sub $5,000 launch goals are more likely to succeed before the success rates start to drop off. In the 20,000+ goal range the failure rate ticks up sharply, but once it goes into the $35,000 range it flips over with successes being higher than failures.
- Once a project is launched with a goal of $45,000+ it is more likely to fail than to succeed. Of the 17 projects that were launched with a goal of $45,000+ only 2 actually succeeded.

### Data Limitations
  - Some limitation of the dataset if that there are many external factors that can affect the outcome of projects. The is the possibility that for some theater projects there were major names attached to projects. Or there have been projects that were tapping into major pop culture topics at the time which can give them a boost in terms of their chance of success. Additional limitations can also include if potentially certain countries are not amenable to certain types of projects. To account for a limitation like this additional graphs should be created with pivot table fields to filter also for countries. This will allow us to see if there are certain countries that are more likely to support certain types of projects.
