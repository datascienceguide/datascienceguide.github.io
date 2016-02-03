---
layout: post
title:  "Optimization"
categories: advise
date:   2015-02-19 21:46:04
---

More content to come soon!

# Linear Programming  
Deals with finding the max or min of a linear function (objective function is subject to linear constraints). For example, how do you maximize profits selling different products with limited resources?



## Example 1: Resource Allocation Problem

Producing n different products, maximize profit to not exhausting our n different resources.

### Decision Variable
$$X_j$$ = number of unit of product j to be produced
 
This is the decision variable (unknown to be determined from the solution of the model).

$$C_j$$ = denote the profit (utility per unit of product j) then $$C_j X_j $$ = total profit from producing $$X_j$$ units of product j.

$$C_1 X_1 + C_2 X_2 + ... + C_n X_n = $$ total profit from all products

### Objective Function

$${Total Profit = } \max (\sum_{j=1}^n C_j X_j)$$

Objective to be achieved by the system as a mathematical function of the system decision variables (DV).  It is usually maximizing profit or minimizing cost for example.

$$b_i$$ = the amount of resource i needed to produce 1 unit of product j

$$a_{ij} x_j$$ = amount of resource i needed to make $$x_j$$ units of product j

$$a_{i1} x_1 + a_{i2} x_2 + ... + a_{in} x_n    \leq b_i$$

This is the total amount of resource i used or needed.

### Functional Constraints

$$\sum_{j=1}^n a_{ij} x_j \leq b_i$$

Functional contraints are limitations imposed on the variable to satisfy the restriction of the model system expressed as a math function of the system DV.

We usually assume that $$X_j \geq  0 $$.  This is called the non-negativity constraint.  

## Summary

Find $$ X_1, X_2, .. , X_n $$ so as to maximize  $$ Z = \sum_{j=1}^n C_j X_j$$ subject to $$\sum_{j=1}^n a_{ij} x_j \leq b_i$$, i = 1, ... m and j = 1, ..., n and $$X_j \geq  0 $$ where n is the number of decision variables, and m is he number of contraints.

## Canonical Form of Linear Programming

### Maximization

$$ \max (Z = \sum_{j=1}^n C_j X_j$$) subject to $$\sum_{j=1}^n a_{ij} x_j \leq b_i$$and $$X_j \geq  0 $$ 

### Minimization

$$ \min (Z = \sum_{j=1}^n C_j X_j$$) subject to $$\sum_{j=1}^n a_{ij} x_j \geq b_i$$ and $$X_j \geq  0 $$ 

## General Mathematic Form

Find X so as to max f(x) subject to $$g_i (x) \leq b_i x \epsilon \mathbb{R}^n$$


1. Forumlating the Model

2. Solving the Model 

3. Intrepreting the Model

## Assumptions of L. P.

1. Divisibility
a) ___Proportionality___ (assumption about both objective function and functional contraints).  This means that for each item of product j, both the profit contribution and the amount of each resource i consumed are strictly proportional to the number of units of $$x_j$$.

b) ___Continuity___: Variables are continious numbers, meaning we can produce not just interget (whole number) amounts of each product.  Mathematically this is representedby $$X_j \geq 0$$ 

2. Additivity
Both the equation for the value to minimize or maximize are sums, and the contraints are linear as well

Linear Programming has 3 basic components:

1. Decision variables (solution of model)
2. Objective function (min or mix) with a goal (maximize profit, minimize cost)
3. Constraints

# Further Reading:

[History of Linear Programming](https://www.cs.duke.edu/courses/spring07/cps296.2/papers/LinearProgramming_article.pdf)
