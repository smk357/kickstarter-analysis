# Kickstarter-analysis
A Kickstarter data analytics project

## Project Overview

The client is a playwright who launched a near-successfull Kickstarter campaign for her play *Fever*, and wishes to determine how campaign outcomes for other theater ventures fared based on their launch date, as well as the effect of funding goal on outcomes for plays in particular. The goal of this project was to determine the relationship between outcomes (failed, successful, or canceled) and launch dates and funding goals from a broad Kickstarter dataset. 

Anlayses were performed on a Kickstarter dataset that included funding goals and pledged amounts, launch dates, number of backers, and other pertinent data, for a variety of Kickstarter campaigns across several countries. 

## Analysis and Associated Challenges

### 1. Outcomes based on Launch Date for Theater Ventures

Data was first tabulated in a pivot table in Excel. Launch dates were selected for the row fields and unsorted Outcomes for column fields, with outcome counts for the value fields. Filters were then added for years (the year of the launch dates) and parent category (broad category for each type of venture, eg. *theater* is the parent category for subcategory *plays*). Outcome columns were filtered to exclude plays which were live. The data was subsequently filtered to display only results for *theater*. The following is a screenshot of the resulting pivot table:

![image](https://user-images.githubusercontent.com/79061124/110251214-91c8d700-7f4d-11eb-8bfa-1ea1c27fa74d.png)

With the data now appropriately tabulated and sorted, a line chart was created to determine the relationship between outcomes and launch date for theater ventures (see **Results**).

### 2. Outcomes based on Funding Goals for Plays

Funding goals of various ranges (less than $1,000, between $1,000 and $4,999, and so on, ending in greater than $50,000) were listed as rows. Columns were created (corresponding to each range of funding goal) for the number of successfull, failed, and canceled campaigns, the total number of campaigns, and the percentage of successful, failed, and canceled campaigns. 

In order to correctly populate the first three columns (outcome counts), a count had to be carried out of only the required outcome, within the required range, and corresponding only to plays. The Excel function *countifs()* was used to count outcomes based on the required criteria. For example, to count successful outcomes for plays with funding goals below $1,000, the following Excel command was used:

*=COUNTIFS(Kickstarter!D:D,"<1000",Kickstarter!F:F,"successful",Kickstarter!R:R,"plays")*

The operands within the function correspond to the required funding range, outcome, and subcateogry. For funding goals falling between two amounts, an extra operand had to be added. For example, to count successful outcomes for plays with funding goals between $1,000 and $1,499, the following Excel command was used:

*=COUNTIFS(Kickstarter!D:D,">=1000",Kickstarter!D:D,"<=4999",Kickstarter!F:F,"successful",Kickstarter!R:R,"plays")*

The campaigng totals for each goal range were calculated using Excel's *sum()* function. For example, the Excel command for the total projects with funding goals below $1,000 is as follows: *=SUM(B2,C2,D2)*

Finally, the percentage values were calculated, populating the whole table as follows:

![image](https://user-images.githubusercontent.com/79061124/110252401-300b6b80-7f53-11eb-80e7-25e65afc4356.png)
