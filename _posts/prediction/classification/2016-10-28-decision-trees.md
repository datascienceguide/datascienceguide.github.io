---
layout: post
title:  "Decision Tree"
categories: classification 
date:   2015-02-19 21:46:04
---

While many decision tree algorithms exist, we will learn a decision tree construction algorithm (ID3 by J. R. Quinlan) that relies on the information-theoretic concept of [entropy](http://datascienceguide.github.io/information-entropy) and information gain.  Before discussing the algorithm, please fully read the background information on entropy [here](http://datascienceguide.github.io/information-entropy).

Now, on to the decision tree algorithm.  Decision tree builds classification or regression models in the form of a tree structure. It breaks down the dataset into smaller and smaller subsets as the tree is incrementally developed. The final result is a tree with decision nodes and leaf nodes.  


For an example, we will use the same labeled data set as in the [naive Bayes classification](http://datascienceguide.github.io/naive-bayes-classifier).  The two features are refund and marital status, and the class attribute (to be predicted) is cheat.  The objective is to predict if someone will cheat on their income tax return based on their marital status and whether they are due a tax refund.

Here is the dataset:

Refund | marital status | cheat
y | s | n
n | m | n
n | s | n
y | m | n
n | d | y
n | m | n
y | d | n
n | s | y
n | m | n
n | s | y


A decision node (e.g. refund) has two or more branches (e.g., yes or no) and the leaf node (e.g., cheat) represents a classification or decision. The topmost decision node in a tree which corresponds to the best predictor called root node. Decision trees can handle both categorical and numerical data.

The first step is to decide on the root node of the decision tree.  There are as many choices as features.  In our example, the root node can be refund or marital status.

Option 1:

If we choose refund at the top, there will be two edges out of this node: refund=yes and refund=no.  For refund = yes, we have 3 data points, of which all three have cheat=no.  For refund = no, we have 7 data points, of which four have cheat=no and 3 have cheat=yes.  Now we will calculate the entropies of these two distributions (of the class variable cheat, assuming that refund = yes or no, respectively).

For refund = yes, we have a distribution of cheat where cheat=no is the only possible outcome, so the entropy is zero.

For refund = no, we have a distribution of cheat where P(cheat=no) = 4/7 and P(cheat=yes) = 3/7.  The entropy = $$-4/7 log 4/7 - 3/7 log 3/7 = 0.98$$.

Finally, we compute the weighted average entropy for refund.  We take the entropy for refund = yes and weigh it by the proportion of data points that have refund = yes (3 out of 10), and add the entropy for refund = no, weighted by the proportion of data points that have refund = no (7 out of 10).  We get:

weighted average entropy for refund = $$3/10 * 0 + 7/10 * 0.98 = 0.686$$.

Option 2:

If we choose marital status at the top, there will be three edges out of this node: marital status = single, marital status = married and marital status = divorced.  For marital status = single, we have 4 data points, two of which have cheat = no and two have cheat = yes.  For marital status = married, we have 4 data points, all of which have refund = no.  For marital status = divorced, we have 2 data points, one with refund = no and one with refund = yes.  We need to calculate the entropies of these three distributions.

For marital status = single, we get entropy = $$-2/4 log 2/4 - 2/4 log 2/4 = 1$$.

For marital status = married, we get zero.

For marital status = divorced, we get $$-1/2 log 1/2 - 1/2 log 1/2 = 1$$.

Now we compute the weighted entropy for marital status: $$4/10 * 1 + 4/10 * 0 + 2/10 * 1 = 0.6$$.

Finally, we choose the option with the lowest weighted average entropy.  In our example, marital status will be the root node.

The algorithm then completes the tree by choosing nodes with the lowest weighted average entropy, as above.

## Information Gain

Another method for decision trees is the use of information gain or the decrease in entropy after a dataset is split on an attribute. Constructing a decision tree is all about finding attribute that returns the highest information gain.  The example on [this site](http://www.saedsayad.com/decision_tree.htm) provides an additional example of both an entropy based and information gain based decision tree.

# Closing thoughts

## Pros:
1. Results are human interpretable: you can explain the classification rules based on the decision tree
2. Variations of the algorithm can work with both categorical or numerical 
3. When paired with boosting and ensembling (Random forests and XGboost), decision trees are one of the most commonly used classification technique

## Cons:
1. Decision trees alone are very prone to overfitting as a greedy search is performed based on entropy.  As such, many additional algorithms were created such as [C4.5](https://en.wikipedia.org/wiki/C4.5_algorithm), [Random Forest](https://en.wikipedia.org/wiki/Random_forest), [XGboost](https://github.com/dmlc/xgboost)

Further reading:

[Decision Trees](http://www.saedsayad.com/decision_tree.htm)

[Random Forests](http://www.saedsayad.com/docs/rf.pdf)
