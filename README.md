#Analyzing the NYC Subway Dataset


##Overview
This project consists of two parts. In Part 1 of the project, you should have completed the questions in Problem Sets 2, 3, 4, and 5 in the Introduction to Data Science course.  

This document addresses part 2 of the project. Please use this document as a template and answer the following questions to explain your reasoning and conclusion behind your work in the problem sets. You will attach a document with your answers to these questions as part of your final project submission.
Section 0. References

####Please include a list of references you have used for this project. Please be specific - for example, instead of including a general website such as stackoverflow.com, try to include a specific topic from Stackoverflow that you have found useful.

###[ipython notebook for this project](http://nbviewer.ipython.org/github/jtg2078/nd002-p1/blob/master/p1.ipynb)

```
http://stackoverflow.com/
https://www.youtube.com/watch?v=SqcxYnNlI3Y
http://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.shapiro.html#scipy.stats.shapiro
http://www.statisticshowto.com/what-is-an-alternate-hypothesis/
http://en.wikipedia.org/wiki/Shapiro%E2%80%93Wilk_test
https://answers.yahoo.com/question/index?qid=20110220091827AAa3VJY
http://en.wikipedia.org/wiki/Welch%27s_t_test
http://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mannwhitneyu.html
http://en.wikipedia.org/wiki/Mann%E2%80%93Whitney_U_test
http://www.itl.nist.gov/div898/handbook/pri/section2/pri24.htm
http://strftime.org/
http://dss.princeton.edu/online_help/analysis/interpreting_regression.htm#coefficients
http://stackoverflow.com/questions/12190874/pandas-sampling-a-dataframe
http://imgur.com/
http://discussions.udacity.com/t/problem-set-3-q1/4848
http://pandas.pydata.org/pandas-docs/version/0.15.2/basics.html
https://ggplot.yhathq.com/docs/geom_bar.html
http://pandas.pydata.org/pandas-docs/version/0.15.2/groupby.html
http://stackoverflow.com/questions/16905028/why-is-matplotlib-plot-produced-from-ipython-notebook-slightly-different-from-te
http://pandas.pydata.org/pandas-docs/version/0.15.2/cookbook.html#cookbook-plotting
```

##Section 1. Statistical Test
#####1.1 Which statistical test did you use to analyze the NYC subway data? Did you use a one-tail or a two-tail P value? What is the null hypothesis? What is your p-critical value?
```
- I used Mann-Whitney U test
- One-tail P value
- My null hypothesis is "Rain does not change the ridership in New York Subway system"
- My p-critical value is 0.05
```
#####1.2 Why is this statistical test applicable to the dataset? In particular, consider the assumptions that the test is making about the distribution of ridership in the two samples.
```
- I used Mann-Whitney U test becaouse of the following:
    1. the data is not normal distributed, so I can't use Welch's t test
    2. Mann-Whitney U test worked because it does not assume any underlying probability distribution
```
#####1.3 What results did you get from this statistical test? These should include the following numerical values: p-values, as well as the means for each of the two samples under test.
```
- Mann-Whitney U test result:
    statistics:  1924409167.0
    probability: 0.0249999127935
- means:
    with rain:    1105.446377
    without rain: 1090.278780
```
#####1.4 What is the significance and interpretation of these results?
```
rain is likely a factor to cause differences in subway ridership 
```
##Section 2. Linear Regression

#####2.1 What approach did you use to compute the coefficients theta and produce prediction for ENTRIESn_hourly in your regression model:
```
I used a. Gradient descent (as implemented in exercise 3.5)
```
####2.2 What features (input variables) did you use in your model? Did you use any dummy variables as part of your features?
```
- features used:
    - weekday
    - rain
    - Hour
- dummy variables used:
    - UNIT
```
####2.3 Why did you select these features in your model? We are looking for specific reasons that lead you to believe that
* the selected features will contribute to the predictive power of your model.
Your reasons might be based on intuition. For example, response for fog might be: “I decided to use fog because I thought that when it is very foggy outside people might decide to use the subway more often.”
* Your reasons might also be based on data exploration and experimentation, for example: “I used feature X because as soon as I included it in my model, it drastically improved my R2 value.”    

```
- rain: intuition. I think that the rain will caused people who normally walks to take subway
- weekday: intuition. There should be substantial difference bwetween work and non-work days
- Hour: intuition. rush and non-rush hour should make a difference
```

####2.4 What are the coefficients (or weights) of the non-dummy features in your linear regression model?
```
weekday: 92.9091583928
rain:    15.7852837887
Hour:   464.029152408
```
####2.5 What is your model’s R2 (coefficients of determination) value?
```
0.459131808548
```
####2.6 What does this R2 value mean for the goodness of fit for your regression model? Do you think this linear model to predict ridership is appropriate for this dataset, given this R2  value?
```
- I think my R2 value is pretty bad, it is closer to 0 than it is to 1
- no, i dont think this linear model is appropriate given this R2 value
```

##Section 3. Visualization

Please include two visualizations that show the relationships between two or more variables in the NYC subway data.
Remember to add appropriate titles and axes labels to your plots. Also, please add a short description below each figure commenting on the key insights depicted in the figure.
####3.1 One visualization should contain two histograms: one of  ENTRIESn_hourly for rainy days and one of ENTRIESn_hourly for non-rainy days.
* You can combine the two histograms in a single plot or you can use two separate plots.
If you decide to use to two separate plots for the two histograms, please ensure that the x-axis limits for both of the plots are identical. It is much easier to compare the two in that case.
* For the histograms, you should have intervals representing the volume of ridership (value of ENTRIESn_hourly) on the x-axis and the frequency of occurrence on the y-axis. For example, each interval (along the x-axis), the height of the bar for this interval will represent the number of records (rows in our data) that have ENTRIESn_hourly that falls in this interval.
* Remember to increase the number of bins in the histogram (by having larger number of bars). The default bin width is not sufficient to capture the variability in the two samples.

![](http://i.imgur.com/htV35gE.png)
![](http://i.imgur.com/3CWGD2V.png)

####3.2 One visualization can be more freeform. You should feel free to implement something that we discussed in class (e.g., scatter plots, line plots) or attempt to implement something more advanced if you'd like. Some suggestions are:
* Ridership by time-of-day

![](http://i.imgur.com/ZBAKH0A.png)

* Ridership by day-of-week

![](http://i.imgur.com/szuVozw.png)


##Section 4. Conclusion

Please address the following questions in detail. Your answers should be 1-2 paragraphs long.
####4.1 From your analysis and interpretation of the data, do more people ride the NYC subway when it is raining or when it is not raining?  
```
Inconclusive.

(Assuming that my code and steps involved in this analysis are correct)
    - The differences bwtween ridership when rain and no rain is very small
    - coefficient for rain feature is very small
    - visualization also shows that the difference is very little
 
```
####4.2 What analyses lead you to this conclusion? You should use results from both your statistical tests and your linear regression to support your analysis.
```
statistical test
    - Mann-Whitney U test does indicat ridership in rain and no-rain are two different
      populations
linear regression
    - the coefficient for rain feature small compare to others 
```

##Section 5. Reflection

Please address the following questions in detail. Your answers should be 1-2 paragraphs long.
####5.1 Please discuss potential shortcomings of the methods of your analysis, including:
* Dataset,
* Analysis, such as the linear regression model or statistical test.  

```
- Dataset
    - makes no sense to distinguish data by turnstile
    - should probably transform data to be grouped by weekday
    - I don't understand some of the weather columns mean, e.g. meandewpti
- Analysis
    - no way to know if linear regression is suitable prior
    - I dont full understand the mechanism of dummy features
```

####5.2 (Optional) Do you have any other insight about the dataset that you would like to share with us?
```
NO. Hopefully I will come to some insights as I spend more time and effort learning data analysis
```