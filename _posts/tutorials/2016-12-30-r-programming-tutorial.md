---
layout: post
title:  "R Programming Tutorial"
categories:  required-background 
---

This R programming tutorial was orignally created by the uWaterloo stats club and MSFA with the purpose of providing the basic information to quickly get students hands dirty using R. Fine the original [here](https://github.com/uWaterlooDataTeam/r-programming-tutorial)

## Contents:

- *R Programming Reference*: complilation of useful information and code snippets      
[ Reference in html](http://rpubs.com/uwaterloodatateam/r-programming-reference)  /  [Reference in pdf](https://github.com/uWaterlooDataTeam/r-programming-tutorial/raw/master/r-programming-reference.pdf) /  [Source (r markdown)](r-programming-reference.Rmd)
- *R Programming 101 (Beginner Tutorial)*: Introduction to R Presentation     
[Presentation in html](http://rpubs.com/uwaterloodatateam/r-programming-101)  /  [Presentation in pdf](https://github.com/uWaterlooDataTeam/r-programming-tutorial/raw/master/r-programming-101.pdf)  /  [Source (r markdown)](r-programming-101.Rmd)


## Useful Resources:

Learn more R using [swirl](http://swirlstats.com/students.html)

  
## R for Statisitical Computing
Download R from [CRAN](http://cran.r-project.org/mirrors.html) and install


Recommended supplement but not necessary: RStudio from [http://www.rstudio.com/products/rstudio/download/](http://www.rstudio.com/products/rstudio/download/)

- R Studio: A (very matlab like) IDE for R 

## Comments
Comments are typed with hashtags '#'
{% highlight R %}
# This is a comment
cat("This is not a comment")
{% endhighlight %}


No block comments. So sad. =(


## Data Types
### Integers & Numerics
Examples: 1,2.0,1.1,pi
{% highlight R %}
c(1,2.0,1.1,pi)
{% endhighlight %}
- `Inf` can also be used in calculations

{% highlight R %}
1/Inf
{% endhighlight %}



### Complex Numbers

We can even use complex numbers.

{% highlight R %}
complex(real = 1, imaginary = 2)
8+6i
{% endhighlight %}

### Characters
Example: 'One', '1', 'pi'  
{% highlight R %}
c('One', '1', 'pi')
{% endhighlight %}



### Boolian (Logical) Values

Boolian values can take only two values: `TRUE` (`T`) or `FALSE` (`F`).
{% highlight R %}
c(TRUE, FALSE, TRUE)
{% endhighlight %}

### Factors

A factor is a categorical variable that can take on only a finite set of values. i.e. Sex, Faculty in University
{% highlight R %}
factor(c('Male','Female','Male','Male'))
{% endhighlight %}

Everything is an object, including functions!  

## Vectors
Most common objects are called vectors.  
__Examples__: vector of numbers

{% highlight R %}
a1 <- c(1,2,3)
a1
{% endhighlight %}

{% highlight R %}
a2 <- c('one','two','three')
a2
{% endhighlight %}



{% highlight R %}
a3 <- c('1','2','3')
a3
{% endhighlight %}

You can also create a range of values using
`start:end`
{% highlight R %}
4:10
4:-3
0.1:4
{% endhighlight %}

## Basic Numerical Operations: +, -, *, /, ^

Numerical operations are: +, -, *, /, ^   
- These operate elementwise between vectors.  

| Operator | Description |
|-|-|
| + | Addition |
| - | Subtraction |
| * | Multiplication |
| / | Division |
| ^ | Power |



{% highlight R %}
c(1,2,3) * c(4,5,6)
{% endhighlight %}
__Note__: They don't have to have the same length. If they don't then the vector will recycle though the shorter vector. The longer has to be a multiple of the shorter vector.
{% highlight R %}
c(1,2,3) ^ c(1,2,3,4,5,6)
{% endhighlight %}

## Logical Operators
- Return a boolan value of `TRUE` or `FALSE`

| Operator | Description |
|-|-|
| < | Less than |
| > | Greater than |
| <= | Less than or equal to |
| >= | Greater than or equal to |
| == | Equal to |
| != | Not equal to |
| \| | Elementwise Or |
|-|-|
| & | Elementwise And |
| \|\| | Or |
| && | And |


{% highlight R %}
c(TRUE, FALSE) | c(FALSE, FALSE)
{% endhighlight %}

{% highlight R %}
c(1,2,3) < c(2,1,4)
{% endhighlight %}

__Pro Tip__: When interacting with number, boolians are converted to an integer: 0, or 1.

## Type check
`is.(typename)` 

__Example__: `is.vector`, `is.integer`, `is.numeric`, `is.data.frame`, `is.matrix`  

- Not sure which type? Use `typeof()` !

{% highlight R %}
is.numeric(a1)
is.vector(a1)
is.data.frame(a1)
{% endhighlight %}

## Assignment Operator
Assignment can come in 3 forms:   
`var_name <- evaluation`  
`var_name = evaluation`  
`evaluation -> var_name`

{% highlight R %}
x <- 1
x
{% endhighlight %}

*Be careful:* <- is not the same as < -
{% highlight R %}
x < -1
{% endhighlight %}




{% highlight R %}
y = "string"
y
{% endhighlight %}

{% highlight R %}
"This isn't used much" -> z
z
{% endhighlight %}

## Concatenating Vectors

They are different vectors!
To concatenate two vectors, use `c(vector.1, vector.2)`
{% highlight R %}
b12 <- c(a1,a2)
b12
{% endhighlight %}



{% highlight R %}
b23 <- c(a2,a3)
b23
b13 <- c(a1,a3)
b13
{% endhighlight %}



{% highlight R %}
b21 <- c(a2,a1)
b21
{% endhighlight %}



Notice that when combined with characters, numerics are changed into characters automatically. So `b23 == b21`.
{% highlight R %}
b23 == b21
{% endhighlight %}
{% highlight R %}
b123 <- c(a1,a2,a3)
{% endhighlight %}

## Dot Product
To use dot product of two vectors (instead of elementwise) use `%*%`

{% highlight R %}
a1 %*% a1
c(1,4,5) %*% c(6,7,2)
{% endhighlight %}


##Exercise
1. What are the datatypes available in R?
2. What datatype would the vector `c(1,2,"three")` be?
3. What is the vector `c(3,4,5,6)` to the power of 4?
4. What elements of `c(3,4,5,6)` greater than 4?

##Answer
1. What are the datatypes available in R?
  - Numeric
  - Integer
  - Complex
  - Character
  - Boolian
  - Factor



2. What datatype would the vector `c(1,2,"three")` be?
  - Character
{% highlight R %}
class(c(1,2,"three"))
{% endhighlight %}



3. What is the vector `c(3,4,5,6)` to the power of 4?

{% highlight R %}
c(3,4,5,6) ^ 4
{% endhighlight %}



4. What elements of `c(3,4,5,6)` greater than 4?
{% highlight R %}
c(3,4,5,6) > 4
{% endhighlight %}


## Lists
Different from vectors, they allow us to put multiple structures in a list.  
- Useful when we need to store a list of objects with different datatypes
{% highlight R %}
l12 <- list(a1,a2)
l12
{% endhighlight %}



{% highlight R %}
l23 <- list(a2,a3)
l23
l13 <- list(a1,a3)
l13
{% endhighlight %}
Notice they are stored in two 'different arrays'

 

`as.vector`, `as.list` can interchange list to vectors and vectors to list via as.vector and as.list

{% highlight R %}
as.vector(l23)
as.list(a1)
{% endhighlight %}


## Exercise
1. Generate a vector of 1 to 10, a list of characters 2.1 to 2.5 separated by 0.1  
2. Add the list to the vector and return a vector  
3. Define 2 vectors, x1, x2, by using rnorm(7,mean = 13, sd = 5)  
4. Do the inner product of x1,x2  

## Answer
{% highlight R %}
q1 = 1:10 #Question 1
q1c = as.list(as.character(seq(2.1,2.5,0.1)))

q1 + as.numeric(q1c) # Question 2

x1 = rnorm(7,mean = 13, sd = 5) #Question 3
x2 = rnorm(7,mean = 13, sd = 5)

x1 %*% x2 #Question 4
{% endhighlight %}

## Matrix
- Each column needs to contain same type. 
- Like a high level vector.
{% highlight R %}
M1 <- matrix(c(1,2,3,4,5,6,7,8,9),nrow=3,ncol=3)
M1
M2 <- matrix(9:1 ,3 ,3)
M2
{% endhighlight %}



{% highlight R %}
M3 <- matrix(c(a1,a2),2,3)
M3
{% endhighlight %}

## Data Frames
- Generalised matrix. Now we can store different data types in different columns! =)  
- Like high level list
{% highlight R %}
df1 <- data.frame(a1,a2,a3)
df1
{% endhighlight %}

## Attributes

| Attribute | Description |
|--|-|
| `names` | Names of an object |
| `dimnames` | Names of the dimensions of an object |
| `dim` | Dimension of an object |
| `class` | Class of an object |
| `length` | Length of an object |

{% highlight R %}
length(a1)
{% endhighlight %}



{% highlight R %}
names(a1) = c("a","b","c")
a1
{% endhighlight %}

{% highlight R %}
names(df1) = c("var_1","var_2","var_3")
df1
{% endhighlight %}

{% highlight R %}
dim(M1)
{% endhighlight %}

## Data Manipulation
Indices, just like linear algebra, for vectors, specify thy entry, and matrix row first then column.
{% highlight R %}
a1[2] # Second entry
M1[1,2] #First row second column
df1[2,3] # Second row third column
{% endhighlight %}



{% highlight R %}
M1[1,] # First row
M1[,3] # Third column
{% endhighlight %}

You can also Boolian values to get a subset of values:
{% highlight R %}
a1[a1 <= 2]
{% endhighlight %}



Accessing the elements of a list is slightly different. Use double `[[]]` notation:
{% highlight R %}
l13[[1]]
{% endhighlight %}

## Assigning names to data.frame and matrices
{% highlight R %}
rownames(M1) <- c('Ein','Zwei','Drei')
colnames(M1) <- c('Un','Deux','Trois')
M1
{% endhighlight %}



{% highlight R %}
rownames(df1) <- c('Uno','Dos','Tres')
colnames(df1) <- c('yi','er','san')
df1
{% endhighlight %}

## Adding new rows or columns into matrix or data.frame
`rbind()`: Add new row to 
rbind, cbind

{% highlight R %}
M1.rbind <- rbind(M1,M1)
M1.rbind
{% endhighlight %}



{% highlight R %}
M2.rbind <- rbind(M1,M2) # Notice the names of columns and rows
M2.rbind
{% endhighlight %}

{% highlight R %}
M1.cbind <- cbind(M1,M1)
M1.cbind
{% endhighlight %}


## Calling by Column Names
{% highlight R %}
df1$yi
df1$er
df1$san
{% endhighlight %}


## Reading csv/delim files
`read.file_type(file = "Name.file_type", header = TRUE, sep = "")`


## Useful functions
{% highlight R %}
attach(iris)
head(iris)
{% endhighlight %}



{% highlight R %}
summary(iris)
{% endhighlight %}



{% highlight R %}
print(iris)
{% endhighlight %}

## apply, sapply, lapply
- sapply, lapply takes in vectors/list
- sapply(lapply) returns a vector(list) of same length

__WARNING__: DO NOT USE ANY OF lapply OR sapply under normal circumstances

{% highlight R %}
sapply(iris$Sepal.Width,floor)
{% endhighlight %}



{% highlight R %}
lapply(iris$Sepal.width,floor)
{% endhighlight %}



{% highlight R %}
floor(iris$Sepal.Width) 
{% endhighlight %}
Notice that this returns same thing as sapply, so there is no reason to use sapply under most of the cases.



- `apply` is a function to apply a function to a matrix by row or column or both

{% highlight R %}
apply(M2,1,min)# Minimum for each row
{% endhighlight %}



{% highlight R %}
apply(M2,2,min)# Minimum for each column
{% endhighlight %}



{% highlight R %}
apply(M2,c(1,2),min)# Minimum of all entries, same as min(M2)
{% endhighlight %}


## User define functions
Can predefine default value for argument(s)
- Can take in vectors instead of scalars
{% highlight R %}
random.walk <- function(n=1000,p=0.5, start = 0,min = 0, max = 1){
  rand <- runif(n = n,  min = min, max = max)/(max - min);
  
  steps <- sign(2*(rand - p));
  out <- start + cumsum(steps);
  
  return(out)
}
{% endhighlight %}



{% highlight R %}
plot(random.walk(),type = "l")
{% endhighlight %}

## Exercise
Use the iris dataset in R and build a matrix call iris.matrix with the followings:  
1. Columns and rows of iris corresponds to columns and rows of iris.matrix  
2. Change the Species column of iris.matrix into the following indicator variables  
        - 1 - setosa, 2 - versicolor, 3 - virginica    
3. Get the mean of every column except for Species column  
4. Take away respective mean from each column except for the Species column  
5. Produce the summary of the new matrix  

## Futher Notes

- `browser()` is useful to help debugging, talk about this later
- `?function_name` is useful to look up what a function does

Interesting reads:  

`ggplot2`: Plot package based around ["the grammer of graphics"](http://amzn.to/1HeDhc0)
`data.table`: Package showcasing a faster version of data.frame

## Next Steps:

R Programming Reference:
http://rpubs.com/uwaterloodatateam/r-programming-reference

Contribute useful code snippets:
https://github.com/uWaterlooDataTeam/r-programming-tutorial
