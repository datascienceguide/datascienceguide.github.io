---
layout: post
title:  "Support Vector Machines"
categories: classification
date:   2015-02-19 21:46:04
---

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

[Support Vector Machines and Margins simplified](http://www.holehouse.org/mlclass/12_Support_Vector_Machines.html)   
[Support Vector Machine Full](http://cs229.stanford.edu/notes/cs229-notes3.pdf)   
[Support Vector Machines](http://www.saedsayad.com/docs/svm15.pdf)    
