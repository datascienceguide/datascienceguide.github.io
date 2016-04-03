---
layout: post
title:  "Cross Validation"
categories: predict 
date:   2015-02-19 21:46:04
---

Recall that building a prediction or classification model requires a labeled data set.  One might be tempted to say that performance of the model on the labeled data set (performance = accuracy/error rate or residual sum of squares) it was given is a good indication of performance on future data.  However, this may not be true.  A good model needs to generalize beyond the given data set to be useful for predicting/classifying future data.

One way to validate a model is to split the labeled data set into two subsets: a training data set and a testing data set.  The training data set will be used to build the model.  The testing data set will be used to test the model.  However, it’s not clear how to dived the labeled dataset.  We want as much training data as possible to build a good model, but we also want as much testing data as possible to come up with an accurate estimate of its performance.

K-fold cross-validation is a solution to the above dilemma.  It randomly divides the labeled dataset into k subsets, called folds.  Then, it works as follows:

1. for i = 1 to k
2.    Build a model using all but the k-th fold
3.    Test the model on the k-th fold and record the error rate or residual sum of squares
4. end for
5. Return the average of the error rates or residual sum of squares obtained in line 3

Special case: if k=the size of the labeled dataset, we get Leave-one-out cross-validation.  Every iteration of the for-loop in line 1 “leaves one data point out” for testing.

Note: ultimately, we can use the entire labeled data set to build the model.  Cross-validation is only used to calculate the goodness of the model.