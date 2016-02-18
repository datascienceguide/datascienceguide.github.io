---
layout: post
title:  "Rule Based Learning"
categories: classification
date:   2015-02-19 21:46:04
---

Rule based learning is a related technique to [decision trees](datascienceguide.github.io/decision-trees) as trees can be converted to rules and rules can be converted to trees.  In this section we will learn three concepts: the 1R algorithm, the PRISM algorithm, and converting rules to trees and vice versa.

# 1R Algorithm

The 1R algorithm stands for One Rule and it is simply a  1-level decision tree.  Why would you use only 1 rule?  The answer is for simplicity and to be used as a baseline.  

Pseudo-code for 1R:

	For each attribute:
		For each value of the attribute, make a rule as follows:
			count how often each class appears
			find the most frequent class
			make the rule assign that class to this attribute-value
		Calculate the error rate of the rules
	Choose the rules with the smallest error rate

To see a worked example, please read the first 10 slides of [Chapter 4](http://www.cs.utsa.edu/~jruan/teaching/CS6243_spring_2012/Chapter4.pdf) from [Data Mining by I. Witten and E. Frank](http://www.cs.waikato.ac.nz/ml/weka/book.html).


# Prism

Prism is another rule based learning algorithm.  Here is a worked example:

<iframe src="http://docs.google.com/viewer?url=https://datascienceguide.github.io/assets/prism_one.pdf&embedded=true" width="900" height="780" style="border: none;"></iframe>

<iframe src="http://docs.google.com/viewer?url=https://datascienceguide.github.io/assets/prism_two.pdf&embedded=true" width="900" height="780" style="border: none;"></iframe>

<iframe src="http://docs.google.com/viewer?url=https://datascienceguide.github.io/assets/prism_three.pdf&embedded=true" width="900" height="780" style="border: none;"></iframe>


# Trees and Rules

It is also important to understand that rule-based and tree-based classification models are similar.  We can always covert a decision tree to an equivalent set of rules that make the same prediction.  There will be one rule per leaf node in the tree.  On the other hand, it can be harder to convert a set of if-then rules to an equivalent tree.  For more details and an example, see Witten and Frank's first 14 slides in [chapter 3](http://www.cs.waikato.ac.nz/~tcs/DataMining/TEKBAC2013/Slides/Chapter3.pdf).


# Further reading

[ZeroR](http://www.saedsayad.com/zeror.htm) 

[OneR](http://www.saedsayad.com/oner.htm) 

[Knowledge Representation](http://www.cs.waikato.ac.nz/~tcs/DataMining/TEKBAC2013/Slides/Chapter3.pdf) 

[Data Mining Algorithms](http://www.cs.waikato.ac.nz/~tcs/DataMining/TEKBAC2013/Slides/Chapter4.pdf) 
