---
layout: post
title:  "Logistic Regression"
categories: classification 
date:   2015-02-19 21:46:04
---

Logistic regression is a popular classifier for problems where the class label is binary and the feature variables are numeric.  In linear regression, we were predicting y based on the values of x_1, x_2, …, x_n.  The model was: y = m_1 x_1 + m_2 x_2 + … m_n x_n + b.  The coefficients m_i and b were computed by minimizing the residual sum of squares.  Now suppose that y is a binary class label instead of a numeric variable, and the x_i’s are numeric feature variables.  We might be tempted to fit a least-squares linear regression model, but there are several problems.  For example, our predictions for y may be below zero or above one, but in the new problem, y is a binary class label whose value can only be 0 or 1.  So, it would be difficult to interpret the results.

Instead, we can use logistic regression.  Here, the model is: z = 1 / 1 + e^(-(m_1 x_1 + m_2 x_2 + … + m_n x_n + b)).  We can interpret z as the probability that y=1.  Note that z can ranges between 0 and 1.

See the following Wikipedia article for more info: https://en.wikipedia.org/wiki/Logistic_regression.

===

Linear models for classification

In addition to logistic regression, linear models for classification (e.g., Support Vector Machines (SVM)) are designed for problems with a binary class label and numeric feature variables.  Suppose we have the following labeled dataset, with two numeric features - credit score and credit limit - and a binary class label loan, denoting whether the given customer was able to pay off his/her loan:

credit score | credit limit | loan
100	|	500	 |	n |
200	|	500	 |	n |
100	|	1000 |	n |
400	|	500	 |	y |
500	|	500	 |	y |
300	|	1000 |	y |
400	|	1000 |	y |
500	|	1000 |	y |

Now draw a scatter plot with credit score on the x axis and credit limit on the y axis.  Notice that the following line divides the points with loan=yes from those with loan=no

15/4 x + y - 1500 = 0

This is the linear model that we can use for classification.  To predict the class label of a new data point, we plug in the x and y values (i.e., the credit score and credit limit) to the above equation and see if we get a value below or above zero.  If below zero, then the new data point lies below the dividing line, and we predict loan=no.  Otherwise, we predict loan=yes.

For example, for (x,y)=(credit score,credit limit)=(500,500), we get 15/4 * 500 + 500 - 1500= 875 > 0, so predict loan = yes.  For (x,y)=(credit score,credit limit)=(100,500), we get 15/4 * 100 + 500 -1500 = -625 < 0, so predict loan = no.

An interesting question is how to select the best line that divides the two class values.

# Further Reading

[Maximum Likelihood Estimation of Logistic Regression](http://www.saedsayad.com/docs/mlelr.pdf)

[Logistic Regression](http://scikit-learn.org/stable/modules/linear_model.html#logistic-regression)

