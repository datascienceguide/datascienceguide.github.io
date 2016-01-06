---
layout: post
title:  "What is Data Science?"
categories: introduction 
---

Booz Allen Hamilton's (BAH)[Field Guide to Data Science](http://www.boozallen.com/insights/2015/12/data-science-field-guide-second-edition) tries to answer the question perfectly:

>"Describing Data Science is like trying to describe a sunset – it should be easy, but somehow capturing the words is impossible."

Some say a data scientist is a data analyst from Silicon Valley, others say it is a person who knows more programming than a statistician and knows more statistician than a software developer.  Others have described it with a variation of the famous Venn Diagram:

![](http://image.slidesharecdn.com/bigdataandtheartofdatascience-gwinnett-140321214826-phpapp01/95/big-data-and-the-art-of-data-science-16-638.jpg?cb=1395449088)

Jokes aside, data science is really about actionable insights. "Data Science is the art of turning data into actions, or performing Data Science requires the extraction of timely, actionable information from diverse data sources to drive data decisions and products."  The study and the role is multi-facted and has many different meanings for different companies (or even within a company).

## Data engineering vs Data science?

Udacity has a [great post](http://blog.udacity.com/2014/11/data-science-job-skills.html) outlining common roles and different skills required to be a Data Scientist, summarized in the figure below:

![](http://i2.wp.com/blog.udacity.com/wp-content/uploads/2014/11/blog_dataChart_white.png?resize=640%2C740)

As you can see, the role is very integrated from people who build data integration systems (sometimes called data engineering), to people doing data analytics, to people working on specific tasks in the data science framework.  The latter are sometimes called hadoop monkey (who write map reduce code on demand), ETL drones (who extract transfer and load data daily but never get to do analysis) or other names of people who dislike their current position.

While this guide can be used as the foundation to learn a variety of topics, our focus is providing the background for people working at "Reasonably sized non-data companies who are data-driven" and providing links which outline the details for the difficult mathemical proofs.  In this way, we hope the guide will provide the fundamentals theough a hands on approach to data science.

## Fusion of Top Down/Bottom Up, Inductive/Deductive Thinking

BAH goes on to state that “Data Science supports and encourages shifting between deductive (hypothesis-based) and inductive (pattern-based) reasoning. This is a fundamental change from traditional analytic approaches. Inductive
reasoning and exploratory data analysis provide a means to form or refine hypotheses and discover new analytic paths.”

The way I like to think about it is the traditional scientific approach is top down, where phenomenon is determined by scientific first principles, and then validated through experiment. In the bottom up or inductive based approach, phenomenon is determined by experimentation and then is check for intuition based on first principles. Data science is the function of both approaches by using an iterative approach to the analysis.

## Causality Analysis

It is well known that [Correlation does not imply causation](https://en.wikipedia.org/wiki/Correlation_does_not_imply_causation)

![](https://imgs.xkcd.com/comics/correlation.png)

There even very [funny spurious correlations](http://www.tylervigen.com/spurious-correlations) to drive the point. Yet some argue that data science is about causality analysis and answering the question "Why?".  The only way that this can be done is harmonizing the inductive and deductive ways of thinking.

## What is a "big data scientist"

First of all, the term "big data" makes many people cringe since it is become such a cliche.  So much so that calling big data a cliche has also become a cliche bringing birth to the term "medium data" and the following question:

### How big is big?

According to me, big data is data which it too large to fit reasonbly in an avaliable comptuer/server's memory (RAM).  If the data fits reasonbably in RAM, then I consider it "medium data", and with mordern servers which have Gigabytes (and even [Terabytes](http://yourdatafitsinram.com/) of RAM), medium data can be quite large.

Big data got it's name due to the "4 V's of big data":

Volume: size of data generated.
Velocity: speed of data generation
Variety: different types of data
Veracity: messiness or trustworthiness of the data

For this reason, there exists specialized tools which allows people to "get value" from big data.  But before learning the [newest released big data tool](https://pixelastic.github.io/pokemonorbigdata/), it is easier to learn the fundamentals of data science on small-medium sized data first, then learn big data. For this reason, first part of the guide will outline the general framework and provide hands on tutorials for data analysis then go into big data, distributed systems and the the other modern paradigms.

## Further reading

The wikipedia article on [data science](https://en.wikipedia.org/wiki/Data_science) outlines the multifaceted approach including "signal processing, probability models, machine learning, statistical learning, data mining, database, data engineering, pattern recognition and learning, visualization, predictive analytics, uncertainty modeling, data warehousing, data compression, computer programming, artificial intelligence, and high performance computing."

Now that we have an general understanding of what is Data Science is and what it involves, lets move onto the [required background](/required-background/) knowledge required to be a good data scientist.


