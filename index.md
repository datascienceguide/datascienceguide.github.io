http://bl.ocks.org/serra/5012770
http://bl.ocks.org/mbostock/raw/4063550/flare.json
https://leanpub.com/D3-Tips-and-Tricks








Tools and Environment Setup!

### Data structures and algorithms:




## Data Tools

	if 


# Data Science Framework


# Acquiring Data

## Types of data

### Structured data
category, ordinal, numeric

### Unstructured data
Natural language text, images, video, audio etc.

Deep learning and big data


## Streaming vs. Batched

### Data scraping

### Data logging



# Prepare and Transform Data

## Processing and Enrichment

### Data cleaning
Regular expressions

### Munging, wrangling

## Aggregation of Data

### Summeriation of data

#### Summarizing Numeric data:

Use descriptive statistics:
mean, median, standard deviation, percentiles, range, min, max

- identify distribution
See background: stats distribution

#### Discrete data:
- distict possible values and frequencies

#### Warning about Summary Statistics and the Flaw of Averages:

It is not enough to use the simle statistical properties (mean, variance, correlation) to describe the data.  This is demonstrated by [Anscombe's quartet](https://en.wikipedia.org/wiki/Anscombe's_quartet)

"Anscombe's quartet comprises four datasets that have nearly identical simple statistical properties, yet appear very different when graphed. Each dataset consists of eleven (x,y) points. They were constructed in 1973 by the statistician Francis Anscombe to demonstrate both the importance of graphing data before analyzing it and the effect of outliers on statistical properties."

Optional reading:
Flaw of Averages
[Article](http://web.stanford.edu/~savage/flaw/Article.htm) // [Book](http://amzn.to/1Tiax3B)

### Exploratory data analysis

Primer: [Why Data Visualizations](https://www.dashingd3js.com/why-data-visualizations)

- don't try and make fancy visualizations, try and answer questions
- primer on visualization (why spider charts are bad etc.)

#### Plotting libraries
- matplotlib (python)
- seaborn (python)
- Grammer of graphics (ggplot2)
- infovis
- Rshiny
- data driven documents (D3.js)

#### univariate data
box plot, histogram

#### bivariate data
line charts (why stacked line are bad)
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

## Feature engineering

Once you have data, you need to determine what features to use.

Applied machine learning is feature engineering


http://machinelearningmastery.com/discover-feature-engineering-how-to-engineer-features-and-how-to-get-good-at-it/

http://stackoverflow.com/questions/2674430/how-to-engineer-features-for-machine-learning


http://nerds.airbnb.com/overcoming-missing-values-in-a-rfc/


http://datascience.stackexchange.com/questions/2368/machine-learning-features-engineering-from-date-time-data


http://www.cs.princeton.edu/courses/archive/spring10/cos424/slides/18-feat.pdf

### Curse of dimensionality
- Models fail to converge
- Models produce results equivalent to random chance
- You lack the computational power to perform operations across the feature space
- You do not know which aspects of the data are the most important

### Questions:
FROM; https://www.quora.com/MLconf-2015-Seattle/What-are-some-best-practices-in-Feature-Engineering
Are the features continuous, discrete or none of the above?

What is the distribution of this feature?

Does the distribution largely depend on what subset of examples is being considered?
Time-based segmentation?
Type-based segmentation?

Does this feature contain holes (missing values)?
Are those holes possible to be filled, or would they stay forever?
If it possible to eliminate them in the future data?

Are there duplicate and/or intersecting examples?
Answering this question right is extremely important, since duplicate or connected data points might significantly affect the results of model validation if not properly excluded.

Where do the features come from?
Should we come up with the new features that prove to be useful, how hard would it be to incorporate those features in the final design?

Is the data real-time?
Are the requests real-time?

If yes, well-engineered simple features would likely rock.
If no, we likely are in the business of advanced models and algorithms.

Are there features that can be used as the "truth"?

### Filtering


#### Relational algebra projection and selection
Add or remove data based on its value

#### Outlier removal

#### Gaussian filter

#### Exponential smoothing

#### Median filter


### Imputation
Fill in missing values in data

#### Mean, stastical distributions, regression models

#### Random Sampling

#### Markov Chain Monte Carlo (MCMC)

http://jeremykun.com/2015/04/06/markov-chain-monte-carlo-without-all-the-bullshit/
http://setosa.io/blog/2014/07/26/markov-chains/index.html

https://scottlocklin.wordpress.com/2014/07/22/neglected-machine-learning-ideas/


### Dimensionality Reduction

#### Principal component analysis

#### VarianceThreshold

VarianceThreshold is a simple baseline approach to feature selection. It removes all features whose variance doesn’t meet some threshold. By default, it removes all zero-variance features, i.e. features that have the same value in all samples.


#### Sensivity Analysis


#### Univariate feature selection

Univariate feature selection works by selecting the best features based on univariate statistical tests.


#### Recursive feature elimination

#### N grams
#### Term Frequency Inverse Document Frequency (TF IDF)

#### Feature Hashing
Getting a fixed number of features

#### Normalization and Transformation

log transforms
deduplication

normalization: put in range between 0 and 1
Why? Model is able to train faster if using gradient descent

categorical conversion

format conversion

one hot modeling

Encoding

Frequency domain

Fast fourier transform

Coordinate transform


# Analyze


## Clustering
http://scikit-learn.org/stable/modules/clustering.html#clustering

Hierarchical clustering

K means
- known number of clusters

X means
- unknown nubmer of clusters

Fractal

Topic modeling
- text data

Canopy clustering

self organizing maps

## Regression
Regression is fitting a line or curve to do numeric prediction or to do causility analysis (in some cases)

Think Scatter plot of Grade vs. Hours of Study

|Hours of study | Grade|
|:-------------:|:----:|
|data1          | data1|
|...            |   ...|

One feature (or attribute):
$$y = mx +b$$

Multiple features (or attributes)

$$y = m_1 x_1 + m_2 x_2 + m_3 x_3 ... m_k x_k + b $$

### Generalized linear models

#### Linear regression

Input:   

|id | x | y | ŷ | y-ŷ|
|--:|--:|--:|--:|:--:|
|p1 | 1 | 2 | 1 | 1  |
|p2 | 1 | 1 | 1 | 0  |
|p3 | 3 | 2 | 3 |-1  |

Where x is a feature, y is the true output, ŷ is the predicted output and y - ŷ is called residual(observed - predicted)   

Suppose we obtain in the following linear model:       
y = x    

Sum of the squares residuals (SSQ)  =  $\sum (y- \hat{y} )^{2}$

Ordinary least squares (OLS) or linear least squares computes the least squares solution using a [singular value decomposition](https://relate.cs.illinois.edu/course/cs357-f15/file-version/59babe8be91b4665456aae2abfdc1e1e732643ec/media/least-squares/linregr_least_squares_fit.html) of X. This means the algorithm attempts to minimize the sum of squares of residuals.  If X is a matrix of size (n, p) this method has a cost of $O(n p^2)$, assuming that $n \geq p$.  This means that for small number of features, the algorithm scales very well, but for a large number of features (p), it is more efficient (in terms of run time) to use a gradient descent approach after feature scaling.  You can read more about the theory [here](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables.html) and in [more detail here] (http://cs229.stanford.edu/notes/cs229-notes1.pdf)

Other related metrics:  
Mean Squared Error (MSE) = SSQ / num of data points   
Root Mean Squared Error (RMSE) = sqrt (MSE)    

In example:   
SSQ = $1^2 + 0^2 + (-1)^2 + 0^2 + 0^2 = 2$
MSE = 2/5   
RMSE = $\sqrt (2/5)$   

#### Vertical vs Horizontal vs Orthogonal Residuals

![](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3601633/bin/elife00638f001.jpg)

Usually we calculate the (vertical) residual, or the difference in the observed and predicted in the y.  This is because "the use of the least squares method to calculate the best-fitting line through a two-dimensional scatter plot typically requires the user to assume that one of the variables depends on the other.  (We caculate the difference in the y)  However, in many cases the relationship between the two variables is more complex, and it is not valid to say that one variable is independent and the other is dependent. When analysing such data researchers should  consider plotting the three regression lines that can be calculated for any two-dimensional scatter plot.

Plotting all three regression lines gives a fuller picture of the data, and comparing their slopes provides a simple graphical assessment of the correlation coefficient. Plotting the orthogonal regression line (red) provides additional information because it makes no assumptions about the dependence or independence of the variables; as such, it appears to more accurately describe the trend in the data compared to either of the ordinary least squares regression lines."  You can read the [full paper](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3601633/) [here](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3601633/pdf/elife00638.pdf)

Residual plot y - ŷ vs x   

TODO: put plot

Distribution of Residuals   

Frequency of y - ŷ   

TODO: put histogram

- create residual plot for each feature and if x and y are indeed linearly related, the distribution of residuals should be normal and centered around zero
- if poor fit, consider applying a transform (such as log transform) or non-linear regression
- residual plot should not have any patterns (under/over estimation bias)
- residual plot is a great visualization of fit, but should be used in combination of other statiscal methods (see tutorial 2 and 3)
- After an initial model is created, it can be modified by changing the features (called feature engineering) ormodel selection.  Example techniques include:

##### Non-linear Regression
Piece-wise regression (see tutorial), polynomial regression, ridge regression, bayesian regression and [many more generalized linear models](http://scikit-learn.org/stable/modules/linear_model.html).  The Scikit Learn documentation has a very good outline and examples of many different techniques and when to use them.


##### Data transforms

For example, if x is expoential compared to y appply log transform:
````
y = b e^x
ln y = ln (b e^x)
     = ln b + ln e^x
     = ln b + x
````
Why apply transforms?
It linearizes the model so linear regression can be used on some non-linear relationships.

There are other methods for transforming variables to achieve linearity outlined [here](http://stattrek.com/regression/linear-transformation.aspx?Tutorial=AP)

|Method                      | Transformation(s)             |  Regression equation  |  Predicted value (ŷ) |
-------------------------------------------------------------------------------------------------------------
|Standard linear regression  | None                          |  y = b0 + b1x         |  ŷ = b0 + b1x        |
|Exponential model           | Dependent variable = log(y)   |  log(y) = b0 + b1x    |  ŷ = 10b0 + b1x      |
|Quadratic model             | Dependent variable = sqrt(y)  |  sqrt(y) = b0 + b1x   |  ŷ = ( b0 + b1x )^2  |
|Reciprocal model            | Dependent variable = 1/y      |  1/y = b0 + b1x       |  ŷ = 1 / ( b0 + b1x )|
|Logarithmic model           | Independent variable = log(x) |  y= b0 + b1 log(x)    |  ŷ = b0 + b1log(x)   |
|Power model                 | Dependent variable = log(y)   |                       |                      |
|                            |Independent variable = log(x)  | log(y)= b0 + b1log(x) |  ŷ = 10b0 + b1log(x) |


Transforming a data set to enhance linearity is a multi-step, trial-and-error process.

1. Conduct a standard regression analysis on the raw data.
2. Construct a residual plot.
- If the plot pattern is random, do not transform data.
- If the plot pattern is not random, continue.
3. Compute the coefficient of determination (R2).
4. Choose a transformation method (see above table).
5. Transform the independent variable, dependent variable, or both.
6. Conduct a regression analysis, using the transformed variables.
7. Compute the coefficient of determination (R2), based on the transformed variables.
- If the tranformed R2 is greater than the raw-score R2, the transformation was successful. Congratulations!
- If not, try a different transformation method.


##### Feature Transform

1. Forward Selection
Try each variable one by one and find the one the lowest sum of squares error
- not used in practice
2. Backward Selection (more practical than FS)
Try with all the variables and remove the worse one (greedy algorithm) (bad variable = highest impact on SSQ)
- has python implementation
3. Shrinkage
- LASSO: uses matrix algebra to shrink coefficient to help with eliminating variables

Other techniques are used in feature engineering section (TODO add link)

### Tree based models
- Random trees

### K nearest neighours


## Classification

### Decision Tree
- transparent model

### Naive bayes

### Hidden Markov model

### Bayesian Network
- Know dependant relationships between variables


### Logistic Regression

### Support vector machine


### Random Forests

### Deep learning


### Neural networks

## Recommendation

### Collaborative filtering
How people interact with features (items)

### Content based methods
Use item characteristics

### Graph based methods
how items are interconnected




TODO: model selection and evaluation

#Advise

## Logical Reasoning
How to understand different evidence?

### Logical Reasoning

### Expert Systems


## Optimization
How to determine the best course of action


Genetic Algorithms

Simulated Annealing

Gradient Search

Stochastic search

Linear Programming

Integer Programming

Non-linear programming

Active learning









## Simulation
How to characterize systems

Discrete event simulation

Monte Carlo Simulation


### Markov Models
Distinct states

### Agent-based simulation
interaction between autonomous entities


### Systems Dynamics/ Dynamic Modeling
complex system with feedback

### Activity based simulation
Tracking system behaviour


### Fuzzy Logic
Imprecise categories





# Text analytics

N grams

TFIDF










Model Evaluation


It can be difficult to predict which classifier will work best on your dataset.
Always try multiple classifiers. Pick the one or two that work the best to refine and
explore furthe

Learning Curves
http://scikit-learn.org/stable/modules/learning_curve.html

http://www.astroml.org/sklearn_tutorial/practical.html

Bais Vs Variance Tradeoff

http://nbviewer.ipython.org/url/astroml.github.com/sklearn_tutorial/_downloads/06_learning_curves.ipynb



https://github.com/rcompton/ml_cheat_sheet



# Hyper-parameter tuning

http://blog.dato.com/how-to-evaluate-machine-learning-models-part-4-hyperparameter-tuning


http://www.analyticsvidhya.com/blog/2015/06/tuning-random-forest-model/



## Ensembling



http://mlwave.com/kaggle-ensembling-guide/















# Big data tools

## Hadoop

## Hive
SQL on clusters

## Map reduce

Pig


Spark

Storm

Flume, Scribe, Chukwa

http://flume.apache.org/


Apache Nutch, Talend, Scraperwiki

Wbscraper, Sqoop








Markov Chains


MCMC
