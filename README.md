# AB-Testing-Engagement
Many Sites make money by selling ads. For these sites, the number of pageviews by users on each session is one of the most important metrics. The company plans to add a feature to increase the pageviews per sessions on the site, so they ran an A/B experiment to see how effective the feature is and if they should launch this feature on the whole site. The model is tested just on on a random subset of users to see how it performs. If the number of pageviews per session increase, it will be a successful test and feature.

## Metrics define
Average Pageviews/session/user

## Data Explore
1. There were in total 100,000 joining this experiment. 
* Control group: 48,737 users
* Experiment group: 49,136 users

2. Users came from five browsers.
* Opera browser has the least number of user and the least avg pageviews
* Count of users are about evenly split between test and control group    
* The avgerage pageviews in experiment group are higher than control group, but just a little big.
* No record for the avg pageviews of experiment group. Could caused by very few number of user with no many pageviews or something else we need to dig into.

3. The test ran consectively accross August 2015.
* Daily count follows a very strong weekly pattern
* The sample size split evenly between control and test group    
* Average daily pageviews follows a strong patten within every 7 days
* When daily pageviews of test group drops, it drops even more intense compared to control group

## A/B test result analysis
* H0: mean(control) = mean(test)
* H1: mean(control) <> mean(test)

result: Pvalue > 0.05 --> fail to reject Null Hypothesis: there is no significant difference between means of those two groups, which suggests new feature is not successful

## A/B test Sanity Check
Users are segmented by five different browser, and it's worth to check the test performace for each browser.

result:

| Browser | diff(mean)        |  P-value | Test result
| ------------- | ------------- |-------------|-------------
| IE  | 0.087507  |0.007781 |OHYEAH! Increase significant
| Chrome  | 0.077339  |0.00091| OHYEAH! Increase significant
| Safari  | 0.054156  |0.241212	|Bummer
| Firefox  | 0.114095  |0.000597		|OHYEAH! Increase significant
| Opera  | -4.546438	  |0.000000	|Bummer

we see significant increase of pageview increase in brower: IE, Chrome, Firefox, which are the most used browser on our site. At this point, I would say the test is successful.

Also, it seems like each browser responded differently to the test. IE, Chrome, Firefox are successful in this test, compared to Opera which doesn't have any page_visited in the experiment group. Any problem on the UI of Opera brower during the test?

## Result
Ater removing one issue browser, the rest of the data points shows the program did increase the pageview per session by 0.09. However, this increase is very small and it is not even one pageview, I will talk with the product manager and the engineer to see if it is even worth to launch.
    
* Any problem on the UI of Opera brower during the test?
