---
layout: post
title:  "Required Background"
categories: introduction 
---

What background knowledge would be helpful to know as a datascientist? Know of any good (and free) resources? The following list is not complete, so please consider contributing via a [pull request](http://github.com/datascienceguide/datascienceguide.github.io/) or sending [me an email](mailto:andrew@andrewandrade.ca) with suggestions or edits.

In the previous lesson on [What is Data Science?](what-is-data-science/) we learnt that it is multifacted and requiers strong scientific analysis to create meaningful results. For this reason, to be a good data scientist, one requires a strong background in math: statistics and computer science as well as linear algebra and multivariable caluclus.  Why? Not understanding the fundamentals will lead to incorrect analysis and result is poor decision making.

Most people give more emphasis on statistics (or computer science) over linear algebra and calculus since many of the machine learning algorithms are already implemented (so why learn the math?). While it is true that it is recommended to use already implemented algorithms, it is important to have a fundamental undestranding of how the algorithms are implemented.  This way you understand the assumptions in using the algorithm both quickly and correctly. 

The required knowledge is broken down into the following sections:

1. Precalculus and Mathematical Thinking
1. Statistics
1. Linear Algebra
1. Calculus
1. computer science/programming
1. Important topics and concepts

# Precalculus and Mathematical Thinking

Data is fundamentally represented by numbers, so having a strong foundation
in mathematics is very important. The following are links to good resources
to provide a background:

[Precalculus](https://www.khanacademy.org/math/precalculus)
[Mathematical Thinking](https://www.coursera.org/course/maththink)
[Introductiuon to Logic](https://www.coursera.org/course/intrologic)
[Better Explained Math Concepts](http://betterexplained.com)

When I am learning a new math concept, I usually search it on BetterExplained first to get a more intuitive explanation.

# Statistics

Stats is arguably the most important background knowledge required since machine learning is applied statistics.  I highly recommend reading [StatsBookOnline](http://onlinestatbook.com/2/) and going through all the modules.  It will provide a very comprehensive foundation the the frequentist approach to statistics.  After reading the modules you should have a good understanding of the following topics:

## Data basics:

Nominal, ordinal, interval, ratio scales and how to compare

## Discriptive Statistics
mean, median, range, standard deviation, variance, and exploratory data analysis

## Inferenial Statistics
Probability Theory
Random variables
Distribution functions (normal, poisson, gaussian)
Percentiles and Outliers
Skewness
Analysis of Variance
Prob Desnsity Function
Central Limit theorem
Monte carlo
Hypothesis testing
p-value
chi^2
estimation
confidence interval
maximum-likelihood estimation
Kernel density estimate
regression
co-variance
corellation
pearson coeff
causation
least squares
Factor analysis

## Bayesian vs Frequentist Approach
In addition, a data scientist should know the bayesian vs Frequentist approach to statistics and should be familiary with bayes theory and Bayesian Statistics. The notes go into Bayes Theorem.

## Bayesian Statistics

[Bayesian Methods for Hackers](camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/) Monte carlo markov chain


# Linear Algebra

What concepts are important?

From [here](https://www.quora.com/What-concepts-of-linear-algebra-should-one-master-to-be-a-good-data-scientist)

A lot of machine learning (ML) or applied statistics concepts are tied to linear algebra concepts. Some basic examples, PCA - eigenvalue, regression - matrix multiplication... As most ML techniques deal with high dimensional data, they are often times represented as matrices.  Concepts such as singular value decomposition, projections, principal components, eigenvalue, eigenvectors, regression, matrix multiplication, matrix operations, matrix, inverse, solving differential equations using matrices are all important.

For Mathematical Modeling: for example, if you want to capture behaviors (sales, engagement, etc.) in a mathematical model, you can use matrix to breakdown the samples into their own subgroups, and each has its own parameter instead of using a global value. This requires some basic matrix manipulation. Matrix inversion, derivation, solving partial differential or first order differential equations with matrices, for example.For Understanding High Dimensional Distribution: multinomial as the basic example and there are many more.

## Good resources:

[Matrix Cookbook](http://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf)
[Khan Academy's Linear Algebra Videos](https://www.khanacademy.org/math/linear-algebra)
If you are really having difficulty, you can buy [Linear Algebra Done Right](http://amzn.to/1YT2dcj) which is both a comprehensive guide and provides great intuition.
[Hands on Linear Algebra for Data Scientists](http://alexhwoods.com/2015/07/11/linear-algebra-for-data-scientists/)

# Calculus

Khan Academy provides a great overview of many of the necessary concepts:

[Calculus](https://www.khanacademy.org/math/calculus)
[Integral Calculus](https://www.khanacademy.org/math/integral-calculus)
[MultiVariable Calculus](https://www.khanacademy.org/math/multivariable-calculus)
[Differential Equations](https://www.khanacademy.org/math/differential-equations)

Calculus and differential equations is very important for methematic modeling of systems and used in optimization.

# Computer Science/programming

## Programming Fundamentals

### Basics

Arrays, loops, functions, reading/writing data, objects
vectors, lists, variables, expressions, factors

[Udacity's Intro to Computer Science](https://www.udacity.com/course/intro-to-computer-science--cs101) and [Programming Foundations with Python](https://www.udacity.com/course/programming-foundations-with-python--ud036) are great resources to both learn programming and python.  You can view and learn the course material for free or you can take the course and get extra help.

## Data structures

Specifically focus on understanding graphs, trees (binary trees), hash functions,  algorithm complexity, big O notation
TODO: find good resource

## Algorithms

Searching and manupilating graphs and trees

Sorting Algorithms, and searching algorithms are also useful.

TODO: find good free resource

## Numerical methods

Understand how rounding errors affect calculations.


## Data Fundamentals

### Tabular data
spreadsheet, csvs, dataframes, data series

### JSON, XML
"data of the web", no key value or any organized tablular structure.
[Data wrangling with mongodb](https://www.udacity.com/course/data-wrangling-with-mongodb--ud032)

### Unstructured data
Images, voice, natural language text

## Databases

### Relational algebra and DB basics

### SQL

[SQL on Khan Academy(https://www.khanacademy.org/computer-programming/sql/)

[Hands on SQL Tutorial with SQLite](https://github.com/uWaterlooDataTeam/IntroSQL/wiki)

[SQL joins](http://blog.codinghorror.com/a-visual-explanation-of-sql-joins/)

### NoSQL

[Data wrangling with mongodb](https://www.udacity.com/course/data-wrangling-with-mongodb--ud032)

# Important Background Concepts

Since these topics are a must read, we created a new section called [important concepts](important-concepts/).


