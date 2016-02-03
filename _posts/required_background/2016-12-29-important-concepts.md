---
layout: post
title:  "Important Concepts"
categories: introduction 
date:   2015-02-19 21:46:04
---

What important concepts are critical to know datascientist? Know of any good (and free) resources? The following list is not complete, so please consider contributing via a [pull request](http://github.com/datascienceguide/datascienceguide.github.io/) or sending [me an email](mailto:andrew@andrewandrade.ca) with suggestions or edits.

In the previous lesson on [Required background](/required-background/) we listed a long list of required subjects which are related to learning data science.  In this lesson we outline very important concepts which are critical to know and understand when doing data science. Please do not skip this section! 

We cover the following topics:
1. Regular Expressions 
2. Information Entropy
3. Distance measurements
4. OLAP
5. ETL
6. Business Analytics vs Business Intelligence
7. CAP theorem

# Regular Expressions 

[Regual Expressions](https://en.wikipedia.org/wiki/Regular_expression) are extremely useful!  They are a sequence of characters that define a search pattern, mainly for use in pattern matching with strings, or string matching, i.e. "find and replace"-like operations.  They are very powerful and are used commonly in data cleaning (other wise known as data munging or wrangling).  They are also used in text editors, and Unix utilities such as ed, grep and filter.

For example if you wanted so search for an email address in a text the following regular expression ca be used:
    \b[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}\b 

Yes, regular expressions initially are uninterpretable, but luckily there are useful free online tools such as [Regexpal](http://www.regexpal.com/) or [Regexr](http://regexr.com/) to help you.  I usually just search the web or search for [common](http://code.tutsplus.com/tutorials/8-regular-expressions-you-should-know--net-6149) for a specific regular expression I am interested in, but reading online [introduction to regex](http://codular.com/regex) [guides](http://www.aivosto.com/vbtips/regex.html) helped me to learn to write my own.  Next time you are searching for something in your text editor, try using regular expressions (even for simple searches) and getting practice will help with complicated searchs with dirty data.


# Information Entropy

Since [information entropy](/information-entropy) is a very important topics and is used in decision trees, we created its [own page](/information-entropy) not to crowd this page.

# Distance measurements

Since [distance measurements](/distance-measurements) is a very important topics and is used in clustering and k nearest neighbor, we created its [own page](/distance-measurements) not to crowd this page.

# OLAP

[OLAP](https://en.wikipedia.org/wiki/OLAP_cube) is an acronym for online analytical processing, which is a computer-based technique of analyzing data to look for insights. The term cube here refers to a multi-dimensional dataset, which is also sometimes called a hypercube if the number of dimensions is greater than 3.  The [wikipedia article](https://en.wikipedia.org/wiki/OLAP_cube) has a great outline about the concept.

# ETL
[ETL](https://en.wikipedia.org/wiki/Extract,_transform,_load)  or Extract, Transform and Load refers to a process in database usage and especially in data warehousing that:

1. Extracts data from homogeneous or heterogeneous data sources
2. Transforms the data for storing it in the proper format or structure for the purposes of querying and analysis
3. Loads it into the final target (database, more specifically, operational data store, data mart, or data warehouse)

# Business Analytics vs Business Intelligence

### Business Analytics vs Business Intelligence

[BI vs BA](https://www.quora.com/What-is-the-difference-between-business-intelligence-and-business-analytics-1)

[BI vs Advanced Analytics](https://rapidminer.com/summarizing-differences-business-intelligence-advanced-analytics/)

# CAP theorem

Before learning "big data" or distributed systesm, one must understand CAP theorem.  In short, [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem)  also known as Brewer's theorem, states that it is impossible for a distributed computer system to simultaneously provide all three of the following guarantees:
1. Consistency (all nodes see the same data at the same time)
2. Availability (a guarantee that every request receives a response about whether it succeeded or failed)
3, Partition tolerance (the system continues to operate despite arbitrary partitioning due to network failures)

Here is a [plain english explation](http://ksat.me/a-plain-english-introduction-to-cap-theorem/) which explains it better than I could.

Once you have read through the topics, you can move onto learning differents [tools for data science](/opensource-tools-for-datascience).

