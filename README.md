# Kickstarting with Excel

## Overview of Project

### Purpose

With Louise's play _Fever_ coming close to its fundraising goal in a short amount of time, we present this analysis with the purpose of figuring out the relationship that exists between the outcomes of different Kickstarter campaigns and their launch dates, as well as their fundraising goals. 

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

The analysis performed for the relationship between outcomes and launch date of the campaigns was carried out by creating a pivot table accross all data in the original Kickstarter worksheet. Afterwards, the table was filtered based on "Parent Category" and "Years". It was important that the filter for "Parent Category" showed only the data for "theater", as it is the Parent Category that we are interested in, since Louise's campaign falls into that category. Our rows represent the months when the campaign launched, because we want to see how the "theater" category performs throughout the year. We placed in the columns the outcomes we needed, since we wanted to see the results of the campaigns, we placed a restriction by looking at the "successful", "failed" or "canceled" campaigns. We produced a table, from which we produced a [line chart](resources/Theater_Outcomes_vs_Launch.png) from which we drew our conclussions. 

### Analysis of Outcomes Based on Goals

Our analysis of outcomes based on goals was carried out by creating a [line chart](https://github.com/josealcivar96/Kickstarter_Challenge/blob/872d1eb0364987a958a1b0f4cd583d36e4343e69/resources/Outcomes_vs_Goals.png) comparing the percentage of successful, failed and canceled outcomes to the initial goal of each campaign. In order to accomplish this, we created a new sheet which summarized the data we needed, we set up "Goal Ranges" that started at "Less than 1000" and start increasing them in increments of 5000 until we got to "More than 50000". After that, we found the count of successful, failed and canceled campaigns for the "plays" subcategory, note that it is very important to exclude outlier projects in the "theater" parent category because they are not directly related with Louise's campaign (e.g. Theaters, Musicals). For that, we used the excel formula `COUNTIFs()` to count the campaigns with the characteristics we were looking for (within the range, part of the "plays" subcategory, matching "successful", "failed" or "canceled").

We then calculated the sum of the three to get a total of all projects in a given range. Finally, we obtained the percentage by dividing the number of successful/failed/canceled plays by that total amount and we graphed the chart based on the outcomes and goal amount.

### Challenges and Difficulties Encountered

The most outstanding difficulty that was encountered while carrying out the analyses was typing out the formula for each goal range when analyzing outcomes based on goals. Due to the nature of the worksheet being presented, the formulas to be typed had to specify a lot of crucial parameters accross different worksheets. This was solved by double-checking that each formula made logical sense, as well as having an ordered system as to where each parameter of the formula, see for example:

`=COUNTIFS(Kickstarter!$D:$D,">=10000", Kickstarter!$D:$D,"<15000",Kickstarter!$R:$R, "plays", Kickstarter!$F:$F,"successful")` 
 
All ranges are ordered based on what we're looking for, so first we look at the goal amount `Kickstarter!$D:$D`, then the subcategory `Kickstarter!$R:$R` and finally the outcome we look for `Kickstarter!$F:$F`, all on the original Kickstarter sheet. Each is followed by the criteria we're looking for, as first we select the lower bound of our interval `">=10000"`, then the upper bound `"<15000"`, before moving on to our subcategory `"plays"` and finally our desired outcome `"successful"`.

Another difficulty was making sure that the quantities for the outcomes were added up properly. Overcoming this step was simple, as with the help of an auxiliary pivot table with filters for subcategory and goal amount would serve as a quick check to make sure the calculations were done correctly.

## Results

We can draw two conclusions from the outcomes based on launch date: 
1. There is a peak of successful campaigns that start in May and spreads throughout the summer.  
2. This spread "cools off" during the fall and winter season, where we see a spike in failed campaigns relative to successful ones. With notable peaks on October (Where the largest amount of failed campaigns is located) and December (Where there is approximately the same number of failed as successful campaigns). 

There is no notable trend with cancelled campaigns.

Regarding the outcomes based on goals, there is really no definitive pattern that emerges from looking at the percentage of outcomes, specially for the "middle" range of goal amount (between 15000 and 45000), the amount of successful/failed campaigns fluctuate with each other. However, depending on the budget that the campaign has, one should try to land on the goal between (35000 and 45000) as this is the range where the ammount of successful campaigns exceed failed campaigns. The "extremes" of the goals are to be noted, the lesser the goal amount the more likely the campaign is to succeed, whereas the greater the goal amount, the more likely the campaign is to fail. This result makes sense given the how Kickstarter itself works, as a campaign with a lower goal may need fewer backers in order to succeed; on the other hand, a campaign with a higher goal would need more backers pledging higher amounts for that campaign to succeed.

The dataset does showcase some limitations that may hamper the results of this analysis. The main limitation to this dataset comes from the missing parameter that may prove crucial in determining the success of a campaign. For example, the amount of perks, stretch goals and the possible cost/reward that may have with the campaign. Feedback from the backing public is also critical as that may influence a creator how do they continue with the funding of their campaign. Also, the fact that a campaign is successfully funded does not equally translate into one that is perpetually successful, one may have to consider complementary datasets that look into the success of similar plays (not necessarily funded through Kickstarter) sorted by things like genre or subject matter to determine if the play would be successful for the future.

If we wanted to obtain a greater and more specific picture from the data, we may be able to take other parameters from the Kickstarter data that might be linked to the outcome of a particular campaign. One of these important examples would be to see the relationship between average donation and outcome as well as number of backers and outcome. Most importantly, an interesting relation to take a look into would be the length of the campaign, that is, the difference between the deadline and the launch date. This would not only give us the profile of whether or not the campaign is more likely to succeed, but also it would broaden the picture as it would help us analyze how a campaign would fare throughout its tun.
