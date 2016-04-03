---
layout: post
title:  "K Nearest Neighbor and Lazy Learning"
categories: classification 
date:   2015-02-19 21:46:04
---


The nearest neighbour classifier works as follows.  Given a new data point whose class label is unknown, we identify the k nearest neighbours of the new data point that exist in the labeled dataset (using some distance function).  We then check the class labels of these k nearest neighbours and select the most frequently occurring one (just within the k nearest neighbours, not in the entire dataset).  This is the prediction for the class label of the new data point.

For example, consider the following dataset, where income is a numeric feature variable and loan is a binary class label, denoting whether a particular customer with a particular income was able to pay off his/her loan:

income |   loan
30    | n
32    | n
35    | y
35    | n
40    | y
42    | n
43    | y
44    | y
50    | y

Question: Using Euclidean distance, what prediction will 1-nn and 3-nn give for a new data point with income=39.5?

Answer: 1nn = one nearest neighbour.  The closest point to 39.5 is the one with income=40 and loan=yes, so predict loan=yes.  3nn = 3 nearest neighbours.  The three closest points to 39.5 are those with income=40, 42 and 43.  Two of them have loan=yes, one has loan=no, so take the majority vote and predict loan=yes.

Notes about the nearest neighbour classifier:
- It is often called “lazy learning”.  It does not build any “model”.  Instead, all the work (i.e., finding the nearest neighbours) is done at prediction time.
- How to choose a good value of k for a particular dataset/application?  Try several different values and compute the error rate using cross-validation.