---
layout: post
title:  "Naive Bayes Classifier"
categories: introduction 
date:   2015-02-19 21:46:04
---

The Bayesian approach offers an alternative method to statistics, and is actually quite intuitive once you wrap your head around it.  Statistics can be daunting, but I will attempt to explain Bayes theorem intuitively and leave the mathematical proofs for textbooks.

The foundation for the Bayesian approach is Bayes theorem.  I recommend you read this primer on an intuitive (and short) explanation of [Bayes' theroem](http://betterexplained.com/articles/an-intuitive-and-short-explanation-of-bayes-theorem/) and [understanding bayes' theorem with ratios](http://betterexplained.com/articles/understanding-bayes-theorem-with-ratios/).

# Bayes' Theorem

Let's say we have event A and event B. We are trying to determine the probability of event A when B is observed.

The idea is that the probability of event B times the probability of B when A is observed is equal to the probability of A times the probability of B when A is observed.  In equation:

$$P(B) \times P(A|B) = P(A) \times P(B|A)$$

Now, we are usually concerned with the probability of event A when event B is observed P(A\|B).  If we rearrange the equation above we get:


$$P(A|B) = \frac{P(A) \times P(B|A)}{P(B)}$$

In words:

>Probability of event A when event B is observed is equal to the product of the probability of event B when event A is observed and the product of event A all divided by the probability of event B

Terminology:
P(A|B):  posterior probability
P(A): prior probability
P(B|A): likelihood
P(B): Predictor prior probability

Now lets look at an example of a statistics problem, and see if we can apply Bayes theorem.

# Dishonest Casino Problem: Identifying a loaded dice

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

Now lets apply Bayes theorem:
P(A|B) = P(B | A) P(A) / P(B)

$$P(loaded| 666) = \frac{P(666 | loaded ) \times P(loaded )}{P(666)}$$

Now lets break each part of the equation down.

We know right away that:
P(loaded) = 1/100 
P(fair) = 99/100
This is because a dishonest casino has a 99% fair dice and 1% loaded dice.

We also know what rolling a dice is independent of each other (see the [gamblers fallacy](https://en.wikipedia.org/wiki/Gambler's_fallacy)).  For this reason:

$$P(666 | loaded ) = P(6 | loaded) \times P(6 | loaded) \times P(6 | loaded) = P(6 | loaded)^3$$

We know from the question that:

P(6 \| loaded) = 0.5

therefore :

$$P(666 | loaded ) = P(6 | loaded)^3 = 0.5^3$$

Now we lets calculate the probability of rolling 6 three times.  We know that either the dice is loaded or not loaded.  This means that the probability is disjointedor we have to take the weighted sum of rolling 666 for loaded and not loaded.  This means it will be the probability of rolling 666 for a loaded dice times the probability the dice is loaded plus the probability of rolling 666 for a loaded dice plus times the probability the dice is fair.  In equation form:

$$P(666) = P(666|loaded) \times P(loaded) + P(666|fair) \times P(fair)$$

Now lets sub all of this back into bayes theorem equation:

$$P(loaded dice | 666) = \frac{P(666 | loaded) \times P(loaded)}{P(666)}$$

$$P(loaded dice | 666) = \frac{P(6 | loaded)^3 \times P(loaded)}{P(666|loaded) \times P(loaded) + P(666|fair) \times P(fair)}$$

$$P(loaded dice | 666) = \frac{0.5^3 \times 0.01 }{0.5^3 \times 0.01 + (1/6)^3 \times 0.99} = 0.21$$

The answer to the question is that we believe that there is a 21% probability that the dice is loaded based on the observation of rolling 6 three times consecutively.  Our ___prior___ belief (based on the information in the question) was that there is a 1% chance the dice was loaded, and our new ___posterior___ belief is that there is a 21% chance the dice was loaded. 

Question 2: Rolling 6 only once 

Now what if you only rolled the dice once and got a 6.  What is the posterior probability of the dice being loaded? 
 
$$P(loaded dice | 6) = \frac{P(6 | loaded) \times P(loaded)}{P(6|loaded) \times P(loaded) + P(6|fair) \times P(fair)}$$


$$P(loaded dice | 6) = \frac{0.5 \times 0.01 }{0.5 \times 0.01 + 1/6 \times 0.99} = 0.03$$

# Naive Bayes Classifier

Now let us generalize bayes theorem so it can be used to solve classification problems.  The key "naive" assumption here is that independent for bayes theorem to be true. The question we are asking is the following: What is the probability of value of a class variable (C) given the values of specific feature variables ($$X_1 .. X_k$$).  Again we are going to assume that the specific feature variables are independent of each other (which is sometimes not true!).

$$P(class|features) = \frac{P(features|class) \times P(class)}{P(features)}$$

## Income tax example

For example, lets build a classifier to determine the likelihood if someone is cheating on their income tax.  In this example we are trying to determine a class (Yes or No for cheating) given a set for features (got refund, and marital status).  In this case, the feature for got refund is yes (y) or no (n) and for martial status is divorced (d), married (m) and single (s).

Here is the data we are given:

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

Now lets say we are asked to look at an example where refund = no and and marital status (M.S.) = single.  Using naive bayes (given the naive assumption that getting a refund and MS are independent) determine the probability what the person cheated on their taxes:

$$  P(cheat = y | refund = n \: and \: M.S. = s) = \frac{P (refund = n \: and \:  M.S. = s | cheat = y) \times P(cheat=y)}{P(refund = n \: and \: M.S. = s)}$$

$$ = \frac{P (refund = n \: and \:  M.S. = s | cheat = y) \times P(cheat=y)}{P (refund = n \: and \:  M.S. = s | cheat = y) \times P(cheat=y)+P (refund = n \: and \:  M.S. = s | cheat = n) \times P(cheat=n)}$$

By independance:

$$ = \frac{P(M.S. = s | cheat = yes) \times P(refund = n | cheat = yes) \times P(cheat=y)}{P(M.S. = s | cheat = y) \times P(refund = n | cheat = y) \times P(cheat=y)+ P(M.S. = s | cheat = n) \times P(refund = n | cheat = n) \times P(cheat=n)}$$

Now by counting the data provided:

$$P(M.S. = s | cheat = y) = 2/3$$
$$P(refund = n | cheat = y) = 3/3 = 1$$
$$P(cheat = y) = 3 / 10$$

$$P(M.S. = s | cheat = n) = 2/7$$
$$P(refund = n | cheat = n) = 4/7$$
$$P(cheat = n) = 7 / 10$$

$$ P(cheat = y | refund = n \: and \: M.S. = s) = \frac{ 2/3 \times 3/3 \times 3/10}{3/10 \times 1 \times 2/3+ 4/7 \times 2/7 \times 7/10} = 7/11 $$

Based on the data, our assumptions of independence, we predict that with 7/11 (63.63%) probability the person cheated on their taxes.  The posterior probability is 7/11 compared to the 3/10 (33.33%) prior probability.

## Numerical Predictors

Naive Bayes can also work with numerical  features, but they must first be transformed into categorical values.  One option is to use binning described in [Preparing Data](datascienceguide.github.io/preparing-data/) and the other option (and common practice) is to assume a (usually normal) distribution and probability density function based on the mean ($$mu$$)and standard deviation $$\sigma$$of the dataset.  This assumption can be done by plotting a histogram of the data in addition to computing the mean and standard deviation.

The following is the equation for a normal distribution:

$$P(x) = \frac{e^{- \frac{(x- \mu)^2}{2 \sigma^2}}}{\sigma \sqrt {2\pi } }$$

Where:

$$\mu = \frac{1}{n}\sum_{i=1}^n x_i$$

$$\sigma = \sqrt{\frac{1}{n-1} \sum_{i=1}^n (x_i - \mu)^2} $$

### Example: Predict playing golf based on temperature

A typeset version of this example will be coming soon!  Now you can see the example below.

<iframe src="http://docs.google.com/viewer?url=https://datascienceguide.github.io/assets/naivebayes_numeric.pdf&embedded=true" width="900" height="780" style="border: none;"></iframe>


	# Closing thoughts

	## Pros:
	1. Fast and easy to predict class, and works well with multi class problems
	2. Performs very well (compared to logistic regression and other algorithms) when imdependence assumption is held (you need less training data)
	3. Works very well for categorical inputs

	## Cons:
	1.  For numeric features must assume a distribution such as a Gaussian (which might not be true)
	2.  If a variable has a category in the test data, but not in the training data, the model will assign a "zero frequency" or zero probability.  One must apply a smoothing technique such as Laplace estimation or additive smoothing (smoothing algorithms content is coming soon!)
	3.  Since occurances (and probabilities) can be very small (with a large number of features and observations), there can be floating-point underflow.  This means the probability is so small that rounding errors will cause issues.  One solution is to use a log function and convert the decimals into negative numbers (a property of logarithms) and use those
	4.  Performance can be very poor if assumptions are incorrect, for this reason is it not wise to use the probability (`predict_proba in python`)  
	5.  Some expert call Naive Bayes, idiot's Bayes since in real life if it almost impossible to have a set of predictors which are completely independent

	## When to use:

	___Real time prediction___ of streaming data: naive bayes is simple and fast, great to use for predictions in real time with stream data
	__Multiclass prediction___ by definition naive bayes can work on multi-class problems since it is able to predict the probability of multiple classes
	__Natural Language Processing__ naive bayes is great for text classification, spam filtering, sentiment analysis since it naturally works with multi-class problem.  The simplest implementation is using a bag of words approach or by splitting the text corpus in to words or n-gram and using the occurrences.  Tutorial on this coming soon!

	Combining the three points, naive bayes is great for streaming text data such as tweets, news or email.

## Further reading

### Naive Bayes

[Naive Bayes Examples](gicl.cs.drexel.edu/images/2/21/Regli-casino-example.pdf)

[The Optimality of Naive Bayes](http://www.saedsayad.com/docs/Optimality_of_Naive_Bayes.pdf)

### NaiveBayes and NLP

[Nomograms for Visualizing Naive Bayes](http://www.saedsayad.com/docs/Nomograms.pdf)

### Bayesian Statistics

[Bayesian Statistics on Wikipedia](https://en.wikipedia.org/wiki/Bayesian_statistics)

[Introduction to Bayesian Statistics](https://www.maths.nottingham.ac.uk/personal/tk/files/talks/Cran_10_12.pdf)

[Tutorial in Bayesian Statistics](https://www.maths.nottingham.ac.uk/personal/tk/files/talks/nott_radiology_01_11.pdf)


