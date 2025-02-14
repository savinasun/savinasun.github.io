---
layout: post
title: "ML Notes for Quantitative Finance Interviews"
categories: misc
---
### Linear Models

For details, you may refer to ESL Chapter3 or PRML.

### Classification with Linear Models

Logistic regression is one of the generalized linear models to perform classification tasks. For ease of discussion, we will focus on the binary response case. We call logistic regression linear models that it assumes the log-odds of an observation $y$ can be expressed as a linear function of the $K$ input variables $\mathbf{x}:=(x_1, x_2, ..., x_K)$:

$$
\log{\frac{p(x)}{1-p(x)}} = \sum_{j=0}^K \beta_j x_j \tag{1}
$$

Here $p(x)$ represents the probability of response being true (i.e. $y=1$) and we call $\frac{p(x)}{1-p(x)}$ the "odds" of the response being true, here the function which links *log(odds)* to probability function $p(x)$ is called "link function" in GLM, in the case of logistic regression, link function is the ****logit**** function:

$$
p(z) = \frac{exp(z)}{1-exp(z)}. \tag{2}
$$

We assumes the coefficients of features are "mutliplicative in odds", which means they contribute independently to *log(odds):*

$$
z=\sum_{j=0}^K \beta_j x_j. \tag{3}
$$

In (2), the function is also called the sigmoid of  $z$ , which maps the real line to the interval $(0, 1)$, and is approximately linear near the origin. A useful fact about $p(z)$ is that the derivative

$$
p'(z)=p(z)(1−p(z)).
$$

Logistic regression does not has an analytical solution, to solve the problem, we may find out the set of parameter $\mathbb{\beta}:=(\beta_0, \beta_1,...,\beta_K)$ which **maximizes the log-likelihood** of the observations, which can be expressed as the product of the predicted probabilities of the $N$ individual observations:

$$
\mathcal{L}_{\beta}(\mathbf{Y=(y_0, y_1,..., y_N)^T}|\mathbf{X}) := \sum_{i=0}^N \log{\mathbb{P}(y=y_i)} \\
= \sum_{i=0, y_i=1}^N \log{\mathbb{P}(y=1)} + \sum_{i=0, y_i=0}^N \log{\mathbb{P}(y=0)}
$$

To estimate the parameter vector $\beta$ consider the $N$ observations with labels either 0 or 1. Mathematically, For samples labeled as **True**, it relates to  is as large as possible. And for samples labeled as **False**, we try to find $\beta$ such that the product of all likelihood is as small as possible, in other words $1 — \mathbb{P}(y_i)$ should be as close to 1 as possible.

Therefore, we aim to solve

$$
\max_{\beta} \mathcal{L}_{\beta}(\mathbf{Y}|\mathbf{X}) = \sum_{i=0, Y_i=1}^N \log{\mathbb{P}(y_i)} +
$$

From what discussed above, we have reached the most important conclusion about logistic regression that it is coordinate-free.

### Decision Trees

#### ID-3 Algorithm (Only Classification)

chooses the splits which best reduces the **entropy** in the subsets versus the original datasets, or and **information gain(a reduction in entropy)**

#### C4.5 Algorithm

Consider **gain ratio** instead of information gain,

**pruning**: removing nodes from the tree that adds to complexity, but lead to overfitting

#### CART Algorithm (Classification And Regression Trees)

CART is an alternative to ID3/C4.5 which extends to include regression, it uses gini index as the metric for classification and uses variance reduction as the metric for regression.

We can compute G(S) for each attribute a, and choose the attribute that minimizes G(S)

#### Cons

Decision trees are very powerful tools that they can find complex non-linear relationships in the training data, however, they are also highly sensitive to the training data, which means it has high variance in training. To solve the problem, we may use ensemble techinque.Ensemble

### Ensemble

### Reference

+ https://win-vector.com/2011/09/14/the-simpler-derivation-of-logistic-regression/
