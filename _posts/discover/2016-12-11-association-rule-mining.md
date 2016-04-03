---
layout: post
title:  "Association Rule Mining"
categories: discover
date:   2015-02-19 21:46:04
---

A popular application of association rules involves examining products that were bought together.  Consider the following four sets of items (itemsets) bought together:

1. {bread, diapers, milk}  
2. {beer, diapers, butter}  
3. {bread, beer, diapers, butter}  
4. {beer, butter}  

Definition: Support of itemset A, denoted sup(A) or $$|A|$$ = the number of records (purchase transactions) containing A.

Definition: Let A and B be two itemsets.  An association rule A->B asserts that if a transaction contains A, it is also likely to contain B.

Definition: The support of an association rule A->B is $$|AB|$$

Definition: The confidence of an association rule A->B is $$\frac{|AB|}{|A|}$$

For example, the support of beer->diapers is 2 and its confidence is 2/3.

In practice, we want to find association rules that have sufficiently high support (perhaps at least 1% of the dataset) and sufficiently high confidence (perhaps 90% or 95%).  For examples of business insight that can be obtained from association rules, see Tan, Steinbach & Kumar, chapter 1 slides 23-25.

Since the number of possible association rules can be very large, we need an efficient algorithm.  The APRIORI algorithm can efficiently find association rules with a desired support threshold, call it s, and a desired confidence threshold, call it c.  It exploits the following properties:

1. Let A, B and C be three itemsets.  The support of the following association rules is the same: AB->C, AC->B, BA->C, BC->A, A->BC, B->AC, C->BA.  So, one way to solve the association rule mining problem is to first find all the FREQUENT ITEMSETS, i.e., those with support >= s.  Then we construct possible association rules from the frequent itemsets and return those with confidence >= c

2. For any two itemsets A and B, $$|A| >= |AB|$$.  So, if we find that |A| < s, we don’t have to consider any supersets of A since we already know that their support will be < s.

The APRIORI algorithm first finds frequent itemsets of size one (one item each), then uses them to build frequent itemsets of size 2, and so on.  After finding the frequent itemsets.  Recall the above dataset and suppose s=2 and c=95%.

Step 1: examine all itemsets of size 1 and compute their support
|bread|=2, |diapers|=3, |milk|=1, |butter|=3, |beer|=3
Since |milk| < 2, from now on we never consider any itemsets with milk as a subset because we know they cannot have support >=2

Step 2: examine only those itemsets of size 2 where all of their subsets have support >= 2
|bread,diapers|=2, |bread,butter|=1, |bread,beer|=1, |diapers,butter|=2, |diapers,beer|=2, |butter,beer|=3
Note: none of these include milk
From now on, never consider any itemsetes with milk, or {bread,butter} or {bread,beer} as a subset.

Step 3: examine only those itemsets of size 3 where all of their subsets have support >= 2
|diapers,butter,beer|=2
This is the only itemset of size 3 all of whose subsets have support >=2, as per the previous steps

Step 4: examine only those itemsets of size 4 where all of their subsets have support >=2 
Nothing to examine since there is only one frequent itemset of size 3

Stop.

Answer: the frequent itemsets are: {bread}, {diapers}, {butter}, {beer}, {bread,diapers}, {diapers,butter}, {diapers,beer}, {butter,beer}, {diapers,butter,beer}.

Next step: construct possible association rules from the above frequent itemsets and return those which have confidence >= c

Final answer: bread->diapers, butter->beer, beer->butter, diapers,butter->beer, diapers,beer->butter

Note: association rules are not limited to itemset data.  See, e.g., Frank&Whitten, chapter 4 slides 61-67
