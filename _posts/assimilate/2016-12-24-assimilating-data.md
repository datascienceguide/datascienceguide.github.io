---
layout: post
title:  "Assimilating Data"
categories:  Assimilation 
---
Ask > Aquire > ___Assimilate___ > Analyze > Answer > Advise > Act


## Extract/Transform/Load

![](http://www.saedsayad.com/images/ETL.png)

Extract: data is usually stored in a form of a source in a specific type (such as flat files, relational databases, streaming data, XML/JSON files, Open Database Connectivity (ODBC) and/or Java Database Connectivity (JDBC) data sources.
Transform:  Cleanse, convert, aggregate, merge, and split and modify data so it use useful.
Load: Once transformed, it can be loaded into another database or warehouse

# Transforming and Normalizing Data

## Binning Numerical Data

If numerical data needs to transformed into categorical data, it can be binned into groups

## Encoding Categorical Data

If categorical data needs to be transformed into numerical data (for example if a classifier only works with numerical data), it can be encoded.  If the data is binary, it can be encoded into 1 or 0.  The issue if the data is not binary, is that by adding 

## Normilization

Fitting data betwen a specific range (such as 1 or -1)

## Format conversion

binary conversion, time conversion,   

## Coordiate Conversion

geo conversion.

For example gps coordiate vs distance

## Fourier Transfer
Convert to frequency domain using Fast Fourier Transform or Discrete wavelet transform


## Data Cleaning

### Outlier Detection

As part of the data cleaning stage, outliers can be detected through [outlier detection](/outlier-detection).  Once outliers are determined, they can be removed and then ignored or imputed.  Alternatively there are algorithms which robustly ignore (or deal with) outliers.

### Imputation

Random sampling, distributions, mean, regression

### Filtering

### Deduplication

Removing duplicates

## Dimensionality Reduction

### Principal Compnent analysis

### Membership Assignment

First use clustering (X means, canopy clustering) to determine the cluster, than assign a membership.

### Feature hashing

### Text data: Term Frequecy Inverse Document Frequency

# Data enrichment

In addition to cleaning data, data can be enriched by additional sources of data.  For example, features can be added based on a specific feature and an additional dataset.  For example geography or weather can be added to a dataset to predict if someone is going to take a taxi, bike or walk.

# Further Reading

[Data Preparation](http://www.saedsayad.com/data_preparation.htm)

[Dealing with outliers](http://r-statistics.co/Outlier-Treatment-With-R.html)

## Dimensionality Reduction

[A Tutorial on Principal Component Analysis](http://arxiv.org/pdf/1404.1100.pdf)

[Princiapl Components Analysis](http://www.saedsayad.com/docs/pca.pdf)

[PCA step by step](http://sebastianraschka.com/Articles/2014_pca_step_by_step.html)



