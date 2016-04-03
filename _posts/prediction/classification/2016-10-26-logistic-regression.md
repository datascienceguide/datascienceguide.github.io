---
layout: post
title:  "Logistic Regression"
categories: classification 
date:   2015-02-19 21:46:04
---

Logistic regression is a popular classifier for problems where the class label is binary and the feature variables are numeric.  In linear regression, we were predicting y based on the values of $$ x_1, x_2, …, x_n$$.  The model was: $$y = m_1 x_1 + m_2 x_2 + … m_n x_n + b$$.  The coefficients $$m_i$$ and $$b$$ were computed by minimizing the residual sum of squares.  Now suppose that y is a binary class label instead of a numeric variable, and the $$x_i$$’s are numeric feature variables.  We might be tempted to fit a least-squares linear regression model, but there are several problems.  For example, our predictions for y may be below zero or above one, but in the new problem, y is a binary class label whose value can only be 0 or 1.  So, it would be difficult to interpret the results.

Instead, we can use logistic regression.  Here, the model is: $$z = 1 / 1 + e^{-(m_1 x_1 + m_2 x_2 + … + m_n x_n + b)}$$.  We can interpret z as the probability that y=1.  Note that z can ranges between 0 and 1.


See the following Wikipedia article for more info: Logistic Regression [Logistic Regression](http://en.wikipedia.org/wiki/Logistic_regression).   
[Maximum Likelihood Estimation of Logistic Regression](http://www.saedsayad.com/docs/mlelr.pdf)  
[Logistic Regression](http://scikit-learn.org/stable/modules/linear_model.html#logistic-regression)  


