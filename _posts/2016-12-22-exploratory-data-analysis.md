---
layout: post
title:  "Exploratory Data Analysis"
categories: introduction 
---

Exploratory data analysis (EDA) is a very important step which takes place after [feature engineering](feature-engineering) and acquiring data and it should be done before any modeling.  This is because it is very important for a data scientist to be able to understand the nature of the data without making assumptions.  


The purpose of EDA is to use summary statistics and visualizations to better understand data, and find clues about the tendencies of the data, its quality and to formulate assumptions and the hypothesis of our analysis.  EDA is NOT about making fancy visualizations or even aesthetically pleasing ones, the goal is to try and answer questions with data.  EDA is also very iterative since we first make assumptions based on our first exploratory visualizations, then build some models. We then make visualizations of the model results and tune our models.  

# Types of Data

Before we can start learning about exploring data, let us first learn the different types of data or [levels of measurement](http://onlinestatbook.com/2/introduction/levels_of_measurement.html).  I highly recommend you read [Levels of Measurement](http://onlinestatbook.com/2/introduction/levels_of_measurement.html) in the [online stats book](http://onlinestatbook.com/2/), and continue reading the sections to bush up your knowledge in statistics.  This section is just a summary.

Data comes in various forms but can be classified into two main groups: structured data and unstructured.  ___Structured data___ is data which is a form of data which has a high degree or organization such as numerical or categorical data.  Temperature, phone numbers, gender are examples of structured data.  ___Unstructured data___ is data in a form which doesn't explicitly have structure we are used to. Examples of unstructured data are photos, images, audio, language text and many others.  There is an emerging field called [Deep Learning](http://datascienceguide.github.io/deep-learning/) which is using a specialized set of algorithms which perform well with unstructured data.  In this guide we are going to focus on structured data, but provide brief information for the relevant topics in deep learning.  The two common types of structured we commonly deal with are categorical variables (which have a finite set of values) or numerical values (which are continuous).  

### Categorical Variables

Categorical variables can also be nominal or ordinal.  ___Nominal data___ has no intrinsic ordering to the categories.  For example gender (Male, Female, Other) has no specific ordering.  ___Ordinal data___ as clear ordering such as three settings on a toaster (high medium and low).  A frequency table (count of each category) is the common statistic for describing categorical data of each variable, and a bar chart or a waffle chart (shown below) are two visualizations which can be used.

![](/images/2014_energy_consumption.png)

While a pie chart is a very common method for representing categorical variables, it is not recommended since it is very difficult for humans to understand angles.  Simply put by statstician and visualization professor Edward Tufte: ["pie charts are bad"](http://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=00018S), [others agree](https://www.stevefenton.co.uk/2009/04/pie-charts-are-bad/) and some even say that ["pie charts are the worst"](http://www.businessinsider.com/pie-charts-are-the-worst-2013-6).

For example what you you determine from the follow pie chart?

![](http://static4.businessinsider.com/image/51bf1e9becad048c0a000002-620-/screen%20shot%202013-06-17%20at%2010.34.08%20am.png)

The charts look identical, and it takes more than a couple of seconds to understand the data.  Now compare this to the corresponding bar chart:

![](http://static2.businessinsider.com/image/51bf0aa8ecad04a05d00004a-995-382/screen%20shot%202013-06-17%20at%209.07.44%20am.png)

A reader an instantly compare the 5 variables.  Since humans have a difficult time comparing angles, bar graphs or waffle diagrams are recommended.


### Numeric Variables

Numeric or continuous variables can be any value within a finite or infinite interval.  Examples include temperature, height, weight.  There are two types of numeric variables are interval and ratios.  Interval variables have numeric scales and the same interpretation throughout the scale, but do not have an absolute zero.  For example temperature in Fahrenheit or Celcius can meaningfully be subtracted or added (difference between 10 degrees and 20 degrees is the same difference as 40 to 50 degrees) but can not be multiplied.  For example, a day which is twice as hot may not be twice the temperature.  

"The ratio scale of measurement is the most informative scale. It is an interval scale with the additional property that its zero position indicates the absence of the quantity being measured. You can think of a ratio scale as the three earlier scales rolled up in one. Like a nominal scale, it provides a name or category for each object (the numbers serve as labels). Like an ordinal scale, the objects are ordered (in terms of the ordering of the numbers). Like an interval scale, the same difference at two places on the scale has the same meaning. And in addition, the same ratio at two places on the scale also carries the same meaning."  A good example of a ratio scale is weight since it has a true zero and can be added, subtracted, multiplied or divided.

### Binning (Numeric to Categorical)

Binning otherwise known as discretization is the process of transforming numerical variables into categorical.  For example age can be categories into 0-12 (child), 13-19 (teenager), 20-65 (adult), 65+ (senior).  Binning is powerful as it can be used as a filter to reduce noise or non-linearity and some algorithms such as decision trees require categorical data.  Binning also allows data scientists to quickly evaluate outliers, invalid or missing values for numerical values.  [Techniques for binning](http://www.saedsayad.com/unsupervised_binning.htm) include using equal width (based on range), equal frequency in each bin, sorted rank, quantiles, or math functions (such as log).  Binning can be used based on [information entropy or information gain](http://www.saedsayad.com/supervised_binning.htm). 


### Encoding

Encoding, otherwise known as continuization is the transformation of categorical variables into numerical (or binary) variables.  A basic example of encoding is gender: -1, 0, 1 could be used to describe male, other and female.  Binary encoding is a special case of encoding where the value is set to a 0 or 1 to indicate absence or presence of a category.  One hot encoding is a special case where multiple categories are each binary encoded.  Given we have k categories, this will create k extra features (thus increasing the dimensionality of the data)  Another method for encoding is using a target and probability based encoding.  The category is the average value and includes a probability.


# Iris DataSet

For this article (and tutorial) on exploratory data analysis, we are going be investigating [Anscombe's_quartet](https://en.wikipedia.org/wiki/Anscombe's_quartet) and [Fisher's Iris data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).  

"Anscombe's quartet comprises four datasets that have nearly identical simple statistical properties, yet appear very different when graphed. Each dataset consists of eleven (x,y) points. They were constructed in 1973 by the statistician Francis Anscombe to demonstrate both the importance of graphing data before analyzing it and the effect of outliers on statistical properties."  The Iris data set is a multivariate data set introduced by Ronald Fisher in his 1936 paper The use of multiple measurements.  It shows the variation of Iris flowers of three related species.


## Summary Statistics

Summary statistics are measurements meant to describe data.  In the field of descriptive statistics, there are many summary measurements, but we will leave the definition (and derivation ) to textbooks.  Examples of summary/ descriptive statistics for a single numerical variable is the mean, median, mode, max, min, range, quartiles/percentiles, variance, standard deviation, coefficient of determination, skewness and kurtosis.  Summary statistics for categorical variables is the number of distinct counts.  The most basic summary statistic for text data is term frequency and inverse document frequency.  For bivariate data, the summary statistics is the linear correlation, chi-squared, or the p value based z-test, t-test or analysis of variance.  [This link](http://www.saedsayad.com/numerical_variables.htm)  outlines the common summary statistics, their basic equations and a description.  This should come as a review since you should have a solid understanding of statistics at this point.

You can download the Ansombe Excel worksheet with summary statistics from [datascienceguide.github.io/datasets/anscombe.xls](http://datascienceguide.github.io/datasets/anscombe.xls)  and the Iris dataset Excel worksheet with summary statistics for each variable from [datascienceguide.github.io/datasets/iris.xls](http://datascienceguide.github.io/datasets/iris.xls)

Notice how on the Ansombe dataset, the mean,  standard deviation and correlation between x and y are almost identical.  When we learn about linear regression, we will also see the same coefficients for linear regression as well.

## Visualization

In addition to summary statistics, visualizations can be used to explore and describe data.  We will learn in the tutorials the importance of visualizations, and that it is not enough to use simple statistical properties to describe data.  This is demonstrated by [Anscombe's quartet](https://en.wikipedia.org/wiki/Anscombe's_quartet) as outlined in this article [Why Data Visualizations](https://www.dashingd3js.com/why-data-visualizations) (are important).  This is also a great [article](http://web.stanford.edu/~savage/flaw/Article.htm)  and [Book](http://amzn.to/1Tiax3B) on the flaw of averages.  

Examples of visualizations for numeric data are line charts with error bars, histograms, box and whisker plots, for categorical data bar charts and waffle charts, and for bivariate data are scatter charts or combination charts.  The tutorial on exploratory data analysis goes over many of these visualizations.

There are many tools and libraries which can be used for plotting visualizations:
- Excel/ Libre Office
- Weka
- matplotlib (python)
- seaborn (python)
- Grammer of graphics (ggplot2)
- infovis
- Rshiny
- data driven documents (D3.js)
- [panoramix](https://github.com/mistercrunch/panoramix)


In additional, Tibco Spotfire and Tableau are popular but commercial solutions for data visualizations.

### Univariate data

The two visualizations used to describe univariate (1 variable) data is the box plot and the histogram.  The box plot can be used to show the minimum, maximum, mean, median, quantiles and range.  The histogram can be used to show the count, mode, variance, standard deviation, coefficient of deviation, skewness and kurtosis.  






#### bivariate data
line charts
(why stacked bar are bad)
scatter plot

### multivariate visualation
- plot for each variable
- 3d scatter plot with color
- use principal component anlaysis and then visualize

#### categorial
waffle chart (why pie charts are bad)

#### Text Data

- Word clouds
- Topic modeling



tree (decision tree)
tree maps

Commercial tools:
Tableau

spatial charts

survey plots

timelines

- Is there a distribution?






[Why Data Visualizations?](https://www.dashingd3js.com/why-data-visualizations): from the proverb that a "picture is worth a thousand words!"







# Further Reading

[Visual Information Theory](http://colah.github.io/posts/2015-09-Visual-Information/)

[Multivariate Visualization](http://www.saedsayad.com/docs/multivariate_visualization.pdf)

