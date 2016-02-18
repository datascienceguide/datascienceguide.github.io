---
layout: post
title:  "Information Entropy"
categories: required-background 
date:   2015-02-19 21:46:04
---

Information entropy (more specifically, [Shannon entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)) is the expected value (average) of the information contained in each message.  The [following video](https://www.khanacademy.org/computing/computer-science/informationtheory/moderninfotheory/v/information-entropy) outlines the concept very well.


Let X be a random variable that takes on n possible values, x_1 through x_n.  Suppose the probability that X = x_i is p_i, i.e., P(X = x_i) = p_i, for i = 1 to n.  We define the (shannon) entropy of X, call it H(X), as follows:

$$H = - \sum_i p_i \log_b p_i$$ 

Where $$p_i$$ is a specific probability of the event and b is the base.  Base 2 is mostly used in information theory and is determined by the unit of information (base 2 = bits, base 3 = trits, base 10 = [Hartleys](https://en.wikipedia.org/wiki/Hartley_%28unit%29) etc.).  When used in decision trees, base 2 is usually used since most decision trees are binary trees.


# Examples

## Complete Certainty (No Uncertainty)

The lowest possible value of H(X) is zero, and this occurs when there is no uncertainty in the probability distribution of X.  That is, X can take on only one value, say, $$x_1$$, meaning that P(X = $$x_1$$) = 1.  Therefore, x2, x3 ... xn = 0

In this case:

$$H(x) = -1 \log_2 1 - 0 \log_2 0 ... - 0 \log_2 0 = 1 \times 0 - 0 = = -1 \log_2 1 = 0$$

We have have 100% certainty (or no uncertainty), the information entropy is 0.

## Equal Uncertainty

The highest possible value of H(X) occurs when there is complete uncertainty about the value of X, i.e., when every possible outcome is equally likely.  

### 50:50

Suppose X is a random variable with two possible outcomes: x_1 and x_2, such that P(X = x_1) = P(X = x_2) = 1/2.  In this case:

Given: P(X = x1) = p1 = 1/2 = 0.5 and P(X = x2) = p2 = 1/2 = 0.5

$$H(x) = - 0.5  \log_2 0.5  - 0.5 \log_2 0.5 = 1 $$


### 1/4, 1/4 , 1/4, 1/4

Suppose X is a random variable with four equally likely outcomes. In this case:

Given: p1 = p2 = p3 = p4 = 1/4 = 0.25

$$H(x) = 4\Big(-{1\over 4} \log_2 {1\over 4}\Big) = 2 $$

Thus, as we increase the number of possible outcomes, the maximum possible value of H(X) increases.


## Digital Circuit Example

$$p_i$$ is the probability of character number i showing up in a stream of characters of the given a simple digital circuit which has a two-bit input (X,Y) and a two-bit output (X and Y, X or Y). Assuming that the two input bits X and Y have mutually independent chances of 50% of being HIGH, then the input combinations (0,0), (0,1), (1,0), and (1,1) each have a 1/4 chance of occurring, so the circuit's Shannon entropy on the input side is

$$H(X,Y) = 4\Big(-{1\over 4} \log_2 {1\over 4}\Big) = 2 $$

Now lets say the possible output combinations are (0,0), (0,1), and (1,1) with respective chances of 1/4, 1/2, and 1/4 of occurring.  The circuit's Shannon entropy on the output side is

$$H(X \text{and} Y, X \text{or} Y) = 2\Big(-{1\over 4} \log_2 {1\over 4}\Big) - {1\over 2} \log_2 {1\over 2} = 1 + {1\over 2} = 1 {1\over 2} $$

The circuit reduces (or orders) the information going through it by half a bit of Shannon entropy (due to its logical irreversibility).

# Further Reading

[Entropy (information theory)](https://en.wikipedia.org/wiki/Entropy_%28information_theory%29)

[Information & Entropy](http://www.csun.edu/~twang/595DM/Slides/Information%20&%20Entropy.pdf)

[An introduction to information theory and entropy](http://csustan.csustan.edu/~tom/sfi-csss/info-theory/info-lec.pdf)

[Entropy and Information Theory](http://ee.stanford.edu/~gray/it.pdf)

