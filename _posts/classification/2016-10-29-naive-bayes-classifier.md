---
layout: post
title:  "Naive Bayes Classifier"
categories: introduction 
---

The bayesian approach offers an alterative method to statistics, and is actuall quite intuitive once you wrap your head around it.  Statistics can be daunting, but I will attempt to explain bayes theorem intuitively and leave the mathematical proofs for textbooks.

The foundation for the bayesian approach is bayes theorem.  I recommond you read this primer on an intuitive (and short) explanation of [Bayes' theroem](http://betterexplained.com/articles/an-intuitive-and-short-explanation-of-bayes-theorem/) and [understanding bayes' theorem with ratios](http://betterexplained.com/articles/understanding-bayes-theorem-with-ratios/).

## Bayes' Theorem

Let's say we have event A and event B which are ___independant___ of each other.  The key assumption here is that A and B have to be independant for bayes theorem to be true. Now we are trying to determine the probability of event A when B is observed.

The idea is that the probability of event B times the probability of B when A is observed is equal to the probability of A times the probability of B when A is observed.  In equation:

$$P(B) \times P(A|B) = P(A) \times P(B|A)$$

Now, we are usually concerned with the probablity of event A when event B is observed P(A\|B).  If we rearrange the equation above we get:


$$P(A|B) = \frac{P(A) \times P(B|A)}{P(B)}$$

In words:

>Probability of event A when event B is observed is equal to the product of the probability of event B when event A is observed and the product of event A all divided by the probability of event B

Now lets look at an example of a statistics problem, and see if we can apply Bayes theorem.

### Dishonest Casino Problem: Identifying a loaded dice

Question 1: Rolling 3 numbers in a row

A dishonest casino has a 99% fair dice and 1% loaded dice, where:

fair dice:
P (1) = P (2) = P (3) = P (4) = P(5) = P(6) = 1/6    

loaded dice:
P (1) = 0.1, P(2) = 0.1, P(3) = 0.1, P(4) = 0.1, P(5) = 0.1  
P(6) =  0.5 = 1/2


We are asked to find the probability of the dice being loaded given the number 6 was rolled three times consecutivly.  In equation form:

P(loaded dice \| rolling 6 three consecutive times)

First to save typing, lets just use 666 as the notation for rolling 6 three consecutive times:
p(loaded | 666) = P(dice | rolling 6 three consecutive times)
In the same way I use the following notation (to save typing):
p(rolling 6 once) = p(6)

Now lets apply bayes theorem:
P(A|B) = P(B | A) P(A) / P(B)

$$P(loaded| 666) = \frac{P(666 | loaded ) \times P(loaded )}{P(666)}$$

Now lets break each part of the equation down.

We know right away that:
P(loaded) = 1/100 
P(fair) = 99/100
This is because a dishonest casino has a 99% fair dice and 1% loaded dice.

We also know what rolling a dice is independant of each other (see the [gamblers fallacy](https://en.wikipedia.org/wiki/Gambler's_fallacy)).  For this reason:

$$P(666 | loaded ) = P(6 | loaded) \times P(6 | loaded) \times P(6 | loaded) = P(6 | loaded)^3$$

We know from the question that:

P(6 \| loaded) = 0.5

therefore :

$$P(6 | loaded)^3 = 0.5^3$$

Now we lets calculate the probability of rolling 6 three times.  We know that either the dice is loaded or not loaded.  This means that the probability is disjointedor we have to take the weighted sum of rolling 666 for loaded and not loaded.  This means it will be the probability of rolling 666 for a loaded dice times the probability the dice is loaded plus the probability of rolling 666 for a loaded dice plus times the probability the dice is fair.  In equation form:

$$P(666) = P(666|loaded) \times P(loaded) + P(666|fair) \times P(fair)$$

Now lets sub all of this back into bayes theorem equation:

$$P(loaded dice | 666) = \frac{P(666 | loaded) \times P(loaded)}{P(666)}$$

$$P(loaded dice | 666) = \frac{P(6 | loaded)^3 \times P(loaded)}{P(666|loaded) \times P(loaded) + P(666|fair) \times P(fair)}$$

$$P(loaded dice | 666) = \frac{0.5^3 \times 0.01 }{0.5^3 \times 0.01 + (1/6)^3 \times 0.99} = 0.21$$

The answer to the question is that we believe that there is a 21% probability that the dice is loaded based on the observation of rolling 6 three times consecutively.  Our ___prior___ belief (based on the information in the question) was that there is a 1% chance the dice was loaded, and our new ___posterior___ belief is that there is a 21% chance the dice was loaded. 

Question 2: Rolling 6 only once 

Now what if you only rolled the dice once and got a 6.  What is the posterior probability of the dice being loaded?  I will leave this example for you to solve, but the solution is:

$$P(loaded dice | 6) = \frac{0.5 \times 0.01 }{0.5 \times 0.01 + 1/6 \times 0.99} = 0.03$$


