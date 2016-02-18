---
layout: post
title:  "Model Evaluation"
categories: predict 
date:   2015-02-19 21:46:04
---

Model Evaluation is one of the most important parts of the model development process. The purpose is to find the best model which represents the data based on how well the chosen model will work in the future.  The model evaluation involves the following concepts:

1. Metrics for evaluation (this post)
2. Cross Validation
3. Bias vs Variance and Learning Curves
4. Parameter Tuning and Grid Search
5. Ensembling and combining models
6. Boosting and building models on sampled data


The first concept to understand evaluation is metrics for evaluation.  The idea behind a metric is a measure to determine "how good" the model is performing.  In this post, we will cover the metrics for evaluation of classification, regression and clustering (in this order).

## Classification

The basic visualization of the performance of an classification algorithm is the confusion matrix, also known as a contingency table or an error matrix.  It shows the number of correct and incorrect predictions made by the classification model compared to the actual outcomes (target value) in the data. The matrix is NxN, where N is the number of target values (classes). Performance of such models is commonly evaluated using the data in the matrix.

The following table displays the most basic 2x2 confusion matrix for two classes (Positive and Negative) and related metrics.
 
| Model/ Target | Positive | Negative
| Position |   a | b |
|Negative  |  c  | d |

___Accuracy___ $$(a+d)/(a+b+c+d)$$: the proportion of the total number of predictions that were correct.  

Positive Predictive Value or ___Precision___ ($$a/(a+b)$$) : the proportion of positive cases that were correctly identified.

Negative Predictive Value ($$d/(c+d)$$) : the proportion of negative cases that were correctly identified.

Sensitivity or ___Recall___ $$ a/(a+c) $$ : the proportion of actual positive cases which are correctly identified. 

___Specificity___ $$d/(b+d)$$: the proportion of actual negative cases which are correctly identified. 

While this is the most basic metrics you can use for classification, I highly recommend you read the Wikipedia article on the [confusion matrix](https://en.wikipedia.org/wiki/Confusion_matrix) and related classification metrics.



Further Reading:

[Confusion Matrix](https://en.wikipedia.org/wiki/Confusion_matrix)

[Confusion Matrix Terminology](http://www.dataschool.io/simple-guide-to-confusion-matrix-terminology/)

[Model Evaluation Classification](http://www.saedsayad.com/model_evaluation_c.htm)

[Model Evaluation Regression](http://www.saedsayad.com/model_evaluation_r.htm)

[ROC101](http://wikiww.saedsayad.com/docs/ROC101.pdf)


