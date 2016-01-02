---
layout: post
title:  "Regression"
categories: predict
---

Regression is fitting a line or curve to do numeric prediction or to do predicted causility analysis (in some cases).

## Generalized linear models

### Linear regression

Fit a line to a set of data, for example think Scatter plot of Grade vs. Hours of Study

|Hours of study | Grade|
|:-------------:|:----:|
|data1          | data1|
|...            |   ...|

Simple linear regressoin (with one feature (or attribute)):
$$y = mx +b$$

Input:   

|id | x | y | ŷ | y-ŷ|
|--:|--:|--:|--:|:--:|
|p1 | 1 | 2 | 1 | 1  |
|p2 | 1 | 1 | 1 | 0  |
|p3 | 3 | 2 | 3 |-1  |

Where x is a feature, y is the true output, ŷ is the predicted output and y-ŷ is called residual (observed - predicted)   

Suppose we obtain in the following linear model:       
y = x    

Sum of the squares residuals (SSQ)  =  $$\sum (y- \hat{y} )^{2}$$

Ordinary least squares (OLS) or linear least squares computes the least squares solution using a [singular value decomposition](https://relate.cs.illinois.edu/course/cs357-f15/file-version/59babe8be91b4665456aae2abfdc1e1e732643ec/media/least-squares/linregr_least_squares_fit.html) of X. This means the algorithm attempts to minimize the sum of squares of residuals.  If X is a matrix of size (n, p) this method has a cost of $$O(n p^2)$$, assuming that $$n \geq p$$.  This means that for small number of features, the algorithm scales very well, but for a large number of features (p), it is more efficient (in terms of run time) to use a [gradient descent approach](http://scikit-learn.org/stable/modules/sgd.html#regression) after feature scaling.  You can read more about the theory [here](http://www.holehouse.org/mlclass/04_Linear_Regression_with_multiple_variables.html) and in [more detail here](http://cs229.stanford.edu/notes/cs229-notes1.pdf)

Other related metrics:  
Mean Squared Error (MSE) = $$\frac{SSQ}{total number of data points}$$
Root Mean Squared Error (RMSE) = $$\sqrt{MSE}$$

In example:   
SSQ = $$1^2 + 0^2 + (-1)^2 + 0^2 + 0^2 = 2$$
MSE = 2/5   
RMSE = $$\sqrt{2/5}$$   


## More complicated Example

Now let's take a look at one of the datasets from Anscombe's quartet.  The full analysis and code to generate the figures are outlined in the [simple linear regression tutorial](http://nbviewer.ipython.org/github/datascienceguide/datascienceguide.github.io/blob/master/tutorials/Linear-Regression-Tutorial.ipynb)

<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>x</th>
      <th>y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0 </th>
      <td> 10</td>
      <td>  8.04</td>
    </tr>
    <tr>
      <th>1 </th>
      <td>  8</td>
      <td>  6.95</td>
    </tr>
    <tr>
      <th>2 </th>
      <td> 13</td>
      <td>  7.58</td>
    </tr>
    <tr>
      <th>3 </th>
      <td>  9</td>
      <td>  8.81</td>
    </tr>
    <tr>
      <th>4 </th>
      <td> 11</td>
      <td>  8.33</td>
    </tr>
    <tr>
      <th>5 </th>
      <td> 14</td>
      <td>  9.96</td>
    </tr>
    <tr>
      <th>6 </th>
      <td>  6</td>
      <td>  7.24</td>
    </tr>
    <tr>
      <th>7 </th>
      <td>  4</td>
      <td>  4.26</td>
    </tr>
    <tr>
      <th>8 </th>
      <td> 12</td>
      <td> 10.84</td>
    </tr>
    <tr>
      <th>9 </th>
      <td>  7</td>
      <td>  4.82</td>
    </tr>
    <tr>
      <th>10</th>
      <td>  5</td>
      <td>  5.68</td>
    </tr>
  </tbody>
</table>
</div>

The scatter plot looks like:

![](mages/anscombe_i_scatter.png)

We can now use simple least squares linear regression to fit a line:

![](images/anscombe_i_scatter_fitted_line.png)

The residual (difference between y and y predicted (ŷ)) can then be calculated.  The residuals looks like:

![](images/anscombe_i_scatter_line_residuals.png)

y - ŷ vs x  can now be plotted:

![](images/anscombe_i_residuals.png)

We can now plot the residual distribution:

![](images/anscombe_i_scatter_line_residual_distribution.png)

As seen the the histogram, the residual error should be (somewhat) normally distributed and centered around zero.  This [post](http://stattrek.com/regression/linear-regression.aspx#ReqressionPrerequisites) explains why.

### Vertical vs Horizontal vs Orthogonal Residuals

![](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3601633/bin/elife00638f001.jpg)

Usually we calculate the (vertical) residual, or the difference in the observed and predicted in the y.  This is because "the use of the least squares method to calculate the best-fitting line through a two-dimensional scatter plot typically requires the user to assume that one of the variables depends on the other.  (We caculate the difference in the y)  However, in many cases the relationship between the two variables is more complex, and it is not valid to say that one variable is independent and the other is dependent. When analysing such data researchers should  consider plotting the three regression lines that can be calculated for any two-dimensional scatter plot.


![](images/anscombe_i_scatter_line_all_three.png)


Plotting all three regression lines gives a fuller picture of the data, and comparing their slopes provides a simple graphical assessment of the correlation coefficient. Plotting the orthogonal regression line (red) provides additional information because it makes no assumptions about the dependence or independence of the variables; as such, it appears to more accurately describe the trend in the data compared to either of the ordinary least squares regression lines."  You can read the [full paper](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3601633/) [here](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3601633/pdf/elife00638.pdf)

 [Simple linear regression tutorial](http://nbviewer.ipython.org/github/datascienceguide/datascienceguide.github.io/blob/master/tutorials/Linear-Regression-Tutorial.ipynb) covers a complete example with all three types of regression lines.

1.  create residual plot for each feature and if x and y are indeed linearly related, the distribution of residuals should be normal and centered around zero
1.  if poor fit, consider applying a transform (such as log transform) or non-linear regression
1.  residual plot should not have any patterns (under/over estimation bias)
1.  residual plot is a great visualization of fit, but should be used in combination of other statiscal methods (see tutorial 2 and 3)
1.  After an initial model is created, it can be modified by doing a data transform, changing the features (called feature engineering) or model selection.  

### Data transforms

It linearizes the model so linear regression can be used on some non-linear relationships.

For example, if x is expoential compared to y apply log transform:
$$y = b e^x$$
$$ln y = ln (b e^x) = ln b + ln e^x  = ln b + x$$

There are other methods for transforming variables to achieve linearity outlined [here](http://stattrek.com/regression/linear-transformation.aspx?Tutorial=AP:


|Method                      | Transformation(s)             |  Regression equation         |  Predicted value (ŷ)     |
|---------------------------:|------------------------------:|-----------------------------:|-------------------------:|
|Standard linear regression  | None                          | $$ y = b_0 + b_1x         $$ | $$ ŷ = b_0 + b_1x     $$ |
|Exponential model           | Dependent variable = log(y)   | $$ log(y) = b_0 + b_1x    $$ | $$ ŷ = e b_0 + b_1x   $$ |
|Quadratic model             | Dependent variable = sqrt(y)  | $$ sqrt(y) = b_0 + b_1x   $$ | $$ ŷ = ( b0 + b1x )^2 $$ |
|Reciprocal model            | Dependent variable = 1/y      | $$ 1/y = b_0 + b_1x       $$ | $$ ŷ = 1 / ( b_0+b_1x)$$ |
|Logarithmic model           | Independent variable = log(x) | $$ y= b_0 + b_1 log(x)    $$ | $$ ŷ = b_0 + b_1log(x)$$ |
|Power model                 | Dependent variable = log(y)   | $$                        $$ | $$                    $$ |
|                            |Independent variable = log(x)  | $$log(y)= b_0 + b_1 log(x)$$ | $$ ŷ = eb_0 +b_1log(x)$$ |


Transforming a data set to enhance linearity is a multi-step, trial-and-error process.

1. Conduct a standard regression analysis on the raw data.
2. Construct a residual plot.
- If the plot pattern is random, do not transform data.
- If the plot pattern is not random, continue.
3. Compute the coefficient of determination (R2).
4. Choose a transformation method (see above table).
5. Transform the independent variable, dependent variable, or both.
6. Conduct a regression analysis, using the transformed variables.
7. Compute the coefficient of determination (R2), based on the transformed variables.
- If the tranformed R2 is greater than the raw-score R2, the transformation was successful. Congratulations!
- If not, try a different transformation method.


[Generalized and Non-linear regression tutorial](http://nbviewer.ipython.org/github/datascienceguide/datascienceguide.github.io/blob/master/tutorials/Non-Linear-Regression-Tutorial.ipynb) outlines an example of linear regression after a log transformation.

### Feature Transformations

1. Forward Selection
Try each variable one by one and find the one the lowest sum of squares error
- not used in practice
2. Backward Selection (more practical than FS)
- Try with all the variables and remove the worse one (greedy algorithm) (bad variable = highest impact on SSQ)
3. Shrinkage
- LASSO: uses matrix algebra to shrink coefficient to help with eliminating variables

The techniques are used in feature engineering section (TODO add link) and are outlined in the [Scikit-learn documentation](http://scikit-learn.org/stable/modules/feature_selection.html)

### Linear and Non-linear Regression using Generalized Linear Models

Piece-wise regression, polynomial regression, ridge regression, bayesian regression and [many more generalized linear models](http://scikit-learn.org/stable/modules/linear_model.html) are all valid methods of applying regression  depending on the application. The Scikit Learn documentation has a very good outline and examples of many different techniques and when to use them.

### Advanced Regression Techniques

In addition, we learn later in the course about classification methods which can also be used for regerssion.  These include [decision trees](http://scikit-learn.org/stable/auto_examples/ensemble/plot_adaboost_regression.html#example-ensemble-plot-adaboost-regression-py), [nearest neighbour](http://scikit-learn.org/stable/auto_examples/neighbors/plot_regression.html#example-neighbors-plot-regression-py), [support vector regression](http://scikit-learn.org/stable/auto_examples/svm/plot_svm_regression.html#example-svm-plot-svm-regression-py), [isotonic regression](http://scikit-learn.org/stable/auto_examples/plot_isotonic_regression.html).

For now, understand that these methods exist, and by applying the principles of model selection, evaluation and parameter tuning, you can identify which algorithm and method to use.


### Multi-Regression

After regression with 1 single feature, the intuition can be extended to deal with multiple features called [multi-regresion](http://onlinestatbook.com/2/regression/multiple_regression.html) In simple linear regression, a criterion variable is predicted from one predictor variable. In multiple regression, the criterion is predicted by two or more variables. The basic idea is to find a linear combination of each of the features to predict the output.  The problem is to find the values of $$m_1, m_2, ... m_k$$ and b in the equation shown below that give the best predictions. As in the case of simple linear regression, we define the best predictions as the predictions that minimize the squared errors of prediction.

$$y = m_1 x_1 + m_2 x_2 + m_3 x_3 ... m_k x_k + b $$

![](http://image.slidesharecdn.com/multipleregression-130320062840-phpapp02/95/multiple-regression-7-638.jpg?cb=1363760985)

Instead of a line for one features and an output, with more than one feature, the result is a plane.  Tutorial 4 covers examples of multi-regression with real world data.
