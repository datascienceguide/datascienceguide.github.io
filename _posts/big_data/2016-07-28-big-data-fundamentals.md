---
layout: post
title:  "Big Data Fundamentals"
categories:  big-data 
date:   2015-02-19 21:46:04
---

## Essential Concepts and Tools

Originally created by [Darrell Aucoin](https://github.com/NormallySane) for a Big data talk at uWaterloo's Stats Club

> In pioneer days they used oxen for heavy pulling, and when one ox couldn’t budge a log, they didn’t try to grow a larger ox. We shouldn’t be trying for bigger computers, but for more systems of computers.  
> —Grace Hoppe

# What is Big Data?
![](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/4-Vs-of-big-data.jpg)

## The 4 V's of Big Data

__Volume__: The _quantity_ of data. 

+ Usually too big to fit into the memory of a single machine.

__Veracity__: The _quality_ of data can vary. The inconsistency of data. 

__Variety__: Data often comes in a variety of __formats__ and __sources__ often needing to be combined for a data analysis.

__Velocity__: The speed of generation of new data.

### Volume
+ 100 terabytes of data are uploaded to Facebook daily.
+ 90% of all data ever created was generated in the past 2 years.
    
__Problem__: Impossible to do data analysis with one computer on data this size.

__Solution__: A distributed computing system.

![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Yahoo-hadoop-cluster_OSCON_2007.jpg)

### Veracity
+ Big Data sets do not have the controls of regular studies (Naming inconsistency , Inconsistency in signal strength)
+ Cannot simply assume data missing at random

Veracity naming inconsistency: a musician named several different ways in several different files

### Variety
+ Most of Big Data is unstructured or semi-structured data (Doesn't have the guarantees of SQL)
+ Data can be structured, semi-structured, or unstructured  
+ Often have to combine various datasets from a variety of sources and formats  

### Velocity
+ Speed that data is created, stored, analyzed to create actionable intelligence  
Every min:  
+ 100 hours is uploaded to Youtube  
+ 200 million emails are sent  
+ 20 million photos are viewed  

Often need to be very agile in creating a data product

