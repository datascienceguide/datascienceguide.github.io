---
layout: post
title:  "Open Source Tools for Data Science"
categories: introduction 
---

Many tools for datascience exist. One can start with excel since it is the most basic for dealing with tabular data, later we focus on open source tools: first with workbenches/ interfaces and then programming frameworks.

I personally recommend python if you are interesting in doing analysis and build production systems.  Python is easy to learn and in high demand in industry.  If you want to focus on analysis and want access to more statistical packages (instead of a general programming language) I recommend R.  If you do not want to code, WEKA might have the functionality you are looking for.

## Why open source?

Open sourced tools are recommended since they based upon open innovation and collaboration of many people.  Many of the world's best companies contribute to open source projects and work on building amazing tools.  With open sourced tools you can view the soruce code, contribute without being not tied down or expensive licenses (or have to deal with license issues).  Most open sourced tools worked cross platforms (windows, mac and linux).

## Running servers

While dealing with small data is managable on your personal computers, as data gets larger or more complex, there is more an more a need to run analysis on more powerful dedicated machines called servers.  We recommend to use your personal machines to get started with small sets of data, learning how to run servers, being familiar with the commandline and using a server to do your data analysis is recommended.  This is because servers generally have more RAM than your local computers and are able to deal with medium to large data.  Learning how to use servers will also help when you are dealing with big data when you need a distributed network of computers.

For this reason we recommend using python or R since both of them can run on servers in the same way they run on your local computers (using Rstudio, ipython notebook for example).

## Excel / Open Office

Pros:
1. most basic tool you can use and simple to use for easy tasks
2. Commonly found on most windows/ mac computers
3. Visually see the data

Cons:
1. Slow and uses lots of RAM
2. Lack of standard packages and functionality
3. Crashes with small/medium sized data
4. Costs money

I personally recommend staying away from Excel and get the in the habit of writing code (as we will outline why later).


## WEKA

Java based data mining workbench made by the University of Waikato.

### Pros:
1. graphical user interface (click to do things)
2. great functionality and many data mining packages
3. cross platform (windows, mac, linux)
4. Great out of the box visualizations and functionality

### Cons:
1. stores all of data in RAM (can crash/run slow with medium data)
2. Advanced tools are lacking (compared to R or Python)
3. Industry does not use WEKA, Python and R have become standards for many jobs
4. Difficult to run on a remote server

WEKA is great for quick analysis and for if you do not want to learn how to code.  The issue with using a GUI is that the results are not reproducable and you manually have to do analysis.  By writing code the results are reproducable and it scales better.  This means that it works for larger sets of data and it involves small amount of work to do the analysis for a new set of data.  There are also a number of other [java based machine learning tools](http://machinelearningmastery.com/java-machine-learning/) which I have not used.  [This link](http://machinelearningmastery.com/java-machine-learning/) outlines other options than WEKA.

### How to install and getting started:

You can download Weka [here](http://www.cs.waikato.ac.nz/ml/weka/downloading.html)

[Weka Intro](http://ortho.clmed.ncku.edu.tw/~emba/2006EMBA_MIS/3_16_2006/WekaIntro.pdf)

[Full Tutorial](http://www.cs.waikato.ac.nz/ml/weka/mooc/dataminingwithweka/)


## Python + datastack (Scipy + Scikitlearn + other packages)

### Pros:
1. Extensive, full featured popular programming language
2. Easy to learn and get started
3. Many packages, guides, tutorials
4. Full customability
5. Have to write code (analysis is reproducable)

### Cons:
1. Not as fast performance as other languages
2. Have to learn to write code
3. Have to install many packages
4. Fewer statistical functions compared to R

I personally recommend Python since it is a good skill to have.  Python is used more on the engineering side of data science.  This means python is more commonly used to build data products compared to just doing analysis.

### How to install and getting started:

The simpliest and arguagable best way to install python and the requicked packages for data science is through the [Anaconda Python distribution](https://www.continuum.io/downloads) created by Continuum.  Their GUI will save you a lot of time and the modules it doesn't provide out of the box can easily be installed via a GUI. The distribution is also available for all major platforms (windows, linux mac).  To save time and headache please use the Python 2.7 installer.  I also wrote a guide for how to install the data science stack in python [here](http://datascienceguide.github.io/how-to-install-the-python-data-science-stack-on-a-remote-server/) if you perfer to install it manually.


Python 2 also has many (free) tutorials and courses online:
http://docs.python-guide.org/en/latest/intro/learning/
My favourite resources:
https://docs.python.org/2/tutorial/introduction.html
https://docs.python.org/2/tutorial/
http://learnpythonthehardway.org/book/
https://www.udacity.com/wiki/cs101/%3A-python-reference
http://rosettacode.org/wiki/Category:Python

Once you are familar with python, the first part of this guide is useful in learning some of the libraries we will be using:

http://cs231n.github.io/python-numpy-tutorial/


## [R]

Pros:
1. Many statistical packages
2. Easy to learn and get started
3. Many packages, guides, tutorials
4. Full customability
5. Have to write code (analysis is reproducable)

Cons:
1. Loads data into memory
2. Have to learn to write code
3. Have to install many packages
4. Programming paradigm is different than python or java (more similar to matlab since everything is represented as a vector)

If you are more focused on doing analysis then R is usually a better option.  Many data scientits have told me that they can do anlaysis faster in [R] but use python to implement products.

### How to install and getting started:

You can download [R] from the [offical website](https://cran.r-project.org/) or follow the guide [here](http://a-little-book-of-r-for-bioinformatics.readthedocs.org/en/latest/src/installr.html).  I also recommend installing and using [Rstudio](https://www.rstudio.com/products/rstudio/) and MATLAB like environment for R.  You can also find my guide [here](http://datascienceguide.github.io/beginner-tutorial-how-to-get-started-with-data-science-using-servers/) to installing R and RStudio for Linux or a Linux server.

With the stats club at uWaterloo, I presented a getting started with R tutorial which can found [here](http://rpubs.com/uwaterloodatateam/r-programming-101) and a reference guide [here](http://rpubs.com/uwaterloodatateam/r-programming-reference). There are also many other [data science tutorials](https://www.kaggle.com/wiki/Tutorials) you can find on the web.

### Paid Alternatives: 

Matlab, Azure ML, SAS Enterprise Miner, IBM SPSS, and many others.

Pros:
- Lots of features
- Includes all packages required
- Large scientific community (used by many universities and large companies)

Cons:
- Algorithms are proprietary (trust that they were implemented correctly)
- Expensive (used by people with sufficient funds to buy a license)
- Portability (the ability to run your code on someone elses computer)
- Few third party extensions (compared to open source)

# Database tools

There are many database tools which exist with many in the works.  The [big data tools](/opensource-bigdata-tools/) page outlines other database tools, but the most basic tool is a relational database.  Three popular opensourced relational databases are SQLlite, MySQL and PostgreSQL (postgres).  They are very similar in their SQL language, but SQLlite offers are more limited number of features (and is great for beginners) compared to MySQL or PosgreSQL.  MySQL is commonly used in industry and PosgreSQL is also commonly used in industry for geographical data (due to additional packages)

# Big data tools and Next Steps

We created a section for [big data tools](/opensource-bigdata-tools/) which outline popular opensource tools for big data.  This section is optional for now (until you get to big data).  If you want to move on, you can go to the [DataScience Framework](/data-science-framework/).

# Further reading:

[R vs Python for Data Science](http://www.kdnuggets.com/2015/05/r-vs-python-data-science.html)

[Statistical Language Wars](http://blog.datacamp.com/statistical-language-wars-the-infograph/)
