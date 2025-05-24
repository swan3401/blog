---
title: "Multiple Linear Regression"
date: "2025-05-23"
draft: false
tags: ["Generalized Linear Models", "Linear regression", "Gradient Descent", "Normal Equation"]
categories: ["Theory", "Supervised Learning"]
description: "This post is about multiple linear regression, gradient descent, and normal equation."
# featured_image
featured: true
---

**Previous article:** [Simple Linear Regression](/blogs/simple-linear-regression/)

**Multiple linear regression** (MLR) is an extension of simple linear regression (SLR) that enables multiple independent variables to be included in the prediction of the dependent variable.

The model was previously represented as follows:

$$
    \hat{y} = wx + b
$$

where:
- **x** is an input to the model.
- **w** is a coefficient that defines how the target variable responds to each *unit change in x*.
- **b** is the base value of the outcome when *x = 0* (i.e. outcome unaffected by the independent variable). However, its more important role is positioning the best fitting line along the y-axis (along axis that represents the outcome).

Multiple linear regression keeps the pattern and represented as:

$$
    \hat{y} = \vec{w} \cdot \vec{x} + b \\ 
    \text{or} \\
    \hat{y} = w_1 x_1 + w_2 x_2 + \cdots + w_n x_n + b
$$

>These two are the same equation

where:
- **n** is the number of independent variables.
- **$ \vec{x} $** is a vector containing the independent variables: $ \vec{x} = \begin{bmatrix} x_1 & x_2 & \cdots & x_n  \end{bmatrix} $.
- **$ \vec{w} $** is a vector containing the matching coefficients for the independent variables: $ \vec{w} = \begin{bmatrix} w_1 & w_2 & \cdots & w_n  \end{bmatrix} $.
- **b** has the same role as in SLR. However, multiple linear regression is about hyperplanes rather than a straight line (actually, lines are hyperplanes in two dimensions). Visualising the predictions of an MLR model requires an additional dimension (axis) for each parameter. The best meaningful plot that can be drawn is a plane in three dimensions, where *b* postions the plane along the dependent variable's axis.

Below is example of a multiple linear regression model:

$$
\hat{y}^{(i)} =  w_1 x_1^{(i)} + w_2 x_2^{(i)} + w_3 x_3^{(i)} + b
$$

$$
\text{Predicted price} = 120 \times \text{SqFt} + 15 \space 000 \times \text{Bedrooms} - 800 \times \text{Age} + 50 \space 000
$$

This way, it is intuitive that:
- the price of a house increases by $120 for each additional square foot.
- each additional bedroom increases the price by $15,000.
- each year counted from the year of construction reduces the price by $800.
- *b* is the base price.

| House ID      | SqFt ( $x_1$ )  | Bedrooms ( $x_2$ ) | Age ( $x_3$ ) | Predicted price ( $\hat{y}$ ) | Price ( $y$ ) |
| ------------- | --------------- | ------------------ | ------------- | ----------------------------- | ------------- |
| 1             | 1 500           | 3                  | 10            | 267 000                       | 267 700       |
| 2             | 2 000           | 4                  | 5             | 346 000                       | 345 800       |
| 3             | 1 200           | 2                  | 20            | 208 000                       | 208 500       |
| 4             | 1 800           | 3                  | 8             | 304 600                       | 303 100       |
| 5             | 2 200           | 4                  | 12            | 364 400                       | 366 700       |
| 6             | 1 600           | 3                  | 15            | 275 000                       | 274 750       |
| 7             | 1 100           | 2                  | 25            | 192 000                       | 192 900       |
| 8             | 2 500           | 5                  | 7             | 419 400                       | 418 400       |
| 9             | 1 400           | 3                  | 18            | 248 600                       | 249 000       |
| 10            | 1 900           | 4                  | 10            | 330 000                       | 329 400       |

In this article and those that follow:
- $ x_j $ &nbsp; --- &nbsp; $ j^{th} $ feature : &nbsp;&nbsp; $ x_2 = \begin{bmatrix} 3 \\ 4 \\ \vdots \\ 4 \end{bmatrix} $
- $ x^{(i)} $ &nbsp; --- &nbsp; all the values of the independent variables in $ i^{th} $ observation : &nbsp;&nbsp; $ x^{(3)} = \begin{bmatrix} 1 200 & 2 & 20  \end{bmatrix} $
- $ x_{j}^{(i)} $ &nbsp; --- &nbsp; a value of feature *j* in observation *i* : &nbsp;&nbsp; $ x_{2}^{(9)} = 3 $

## Cost function

In the article on simple linear regression, the cost function, which measures the sum of squared errors, was presented as follows:
$$
    J(w,b) = \frac { 1 } { 2m } \sum_{i=1}^{m} ( wx^{(i)} + b - y^{(i)} )^2
$$

The cost funtion of multiple linear regression does the same and remains almost unchanged:
$$
J(\vec{w},b) = \frac { 1 } { 2m } \sum_{i=1}^{m} ( \vec{w} \cdot \vec{x}^{(i)} + b - y^{(i)} )^2
$$

## Gradient descent
Gradient descent is an optimisation algorithm that iteratively adjusts the parameters of a function — in the case of MLR, the parameters are the slopes ( $\vec{w}$ ) and the intercept ( *b* ) — towards optimal values (i.e. towards values that minimise the cost function).<br>
Gradient descent can be applied to any differentiable function to locate its minimum point. Thus, it is widely used, from optimising regression models to training neural networks.<br>
The algorithm is covered more in detail in the [article on SLR](/blogs/simple-linear-regression/).

Here is how gradient descent is implemented:
1. Calculate the gradient of the cost function.
2. Update the parameters based on the gradient.
3. Repeat steps 1 and 2 until convergence (i.e. until point where updating the parameters reduces the cost function too little).

---

The **gradient** of a function is a vector containing all the values resulting from the calculation of all its partial derivatives.<br>
The partial derivative is calculated separately for each parameter of a function. Each partial derivative yields a number that represents the direction and rate of change of the (cost) function.<br>
For instance, if the partial derivative were taken with respect to the coefficient of the first feature ( $w_1$ ) and the resulting number were 2, this would indicate that increasing the coefficient ( $w_1$ ) would also increase the cost function. If the number were -10, this would mean that decreasing the coefficient ( $w_1$ ) would increase the cost function and to a much greater extent.<br>
Gradient descent aims to reduce the partial derivative of each parameter to zero, in order to minimise the cost function.

Here is the partial derivatives of an SLR model:

$$ \frac{\partial J}{ \partial w} = \frac { 1 } { m } \sum_{i=1}^{m} ( wx^{(i)} + b - y^{(i)} )x^{(i)} $$
$$ \frac{\partial J}{ \partial b} = \frac{ 1 } { m } \sum_{i=1}^{m} (wx^{(i)} + b - y^{(i)}) $$

For multiple linear regression again it is very similar:

$$
    \frac{\partial J}{\partial w_1} = \frac{1}{m} \sum_{i=1}^{m} (\vec{w} \cdot \vec{x}^{(i)} + b - y^{(i)})x_1^{(i)} \\
    \vdots \\ 
    \frac{\partial J}{\partial w_n} = \frac { 1 } { m } \sum_{i=1}^{m} ( \vec{w} \cdot \vec{x}^{(i)} + b - y^{(i)} )x_n^{(i)}
$$
$$ \frac{\partial J}{\partial b} = \frac{1}{m} \sum_{i=1}^{m} (\vec{w} \cdot \vec{x}^{(i)} + b - y^{(i)}) $$

---

It is not hard to adjust the parameters after partial derivatives were taken. Here are the update rules for an SLR:

$$ w_{new} := w - \alpha \times \frac{dJ}{dw} $$
$$ b_{new} := b - \alpha \times \frac{dJ}{db} $$

These rules are applied simultaneously after each iteration. $ \alpha $ is a small number that scales the derivative. It is referred to as the *learning rate*.<br>
In the first iteration, the parameters *w* and *b* are randomly guessed, they are usually set to 0; in SLR and MLR, they only affect the number of iterations until convergence.<br>
If the derivatives are positive, updating the parameters decreases them. If the derivatives are negative, adjusting the parameters increases them. This is the intended behaviour. 

Update rules for an MLR:

$$
    w_1 := w_1 - \alpha \times \frac{\partial J}{\partial w_1} \\ 
    \vdots \\ 
    w_n := w_n - \alpha \times \frac{\partial J}{\partial w_n}
$$
$$
    b := b - \alpha \times \frac{\partial J}{\partial b}
$$

The default values for the learning rate are *0.01* or *0.1*. If the features are not scaled the model becomes very sensitive to the learning rate. While there are approaches to adjust $ \alpha $, brute force (gradually increasing/decreasing it, trying few numbers) is also an option. <br>
If learning rate is too big, gradient descent could not find the best hyperplane. If it is too small, it might take hours to train the model.


