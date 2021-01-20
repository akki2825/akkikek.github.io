---
title: "Some intuition on Feature Scaling, Feature Selection and Feature Transformation"
categories: [machine-learning]
---

**Feature Scaling**

Feature scaling is a method used to standardize the range of independent variables or features of data. In data processing, it is also known as data normalization and is generally performed during the data pre-processing step.

The simplest method is rescaling the range of features to scale the range in [0, 1] or [−1, 1]. The general formula is given as:

X’ = (X – Xmin)/(Xmax – Xmin)

where, X’ is the value we want to rescale, X is the given value, Xmax is the largest value of X and Xmin the smallest.

Let us consider, old weights = [115,140,175] and we are going to scale for the value 140.

X’ = (140 – 115)/(175 – 115) = 0.41666

Therefore, the range is, [0,0.41666,1]

**Feature Selection**

Why do we have to perform feature selection?

- Knowledge discovery, Interpretability and to gain some insights.
- Curse of dimensionality.

There are two methods of Feature Selection :

- Filtering – Filter type methods select variables regardless of the model. They are based only on general features like the correlation with the variable to predict. Filter methods suppress the least interesting variables. They are mainly used as a pre-process method.

- Set of all features --> Selecting the best subset --> Learning Algorithm --> Performance

- Wrapping – Wrapper methods evaluate subsets of variables which allows, unlike filter approaches, to detect the possible interactions between variables.

**Feature Transformation**

Feature transformation is a group of methods that create new features (predictor variables). Feature selection is a subset of feature transformation.

Consider an ‘X’ space having ‘n’ features, using feature transformation we are going to transform X to have ‘m’ features, where m < n.

This is done by defining some matrix Px which is a subspace to which we are going to project ‘X’ space. The new features are combination of the old features.

There are many types explained below –

**Principal Component Analysis (PCA)**

A movie camera takes a 3-D information and flatten it to 2-D without too much loss of information.

What does all of this have to do with PCA?

PCA takes a dataset with a lot of dimensions and flatten it to two or three dimensions so we can look at it.

It tries to find a meaningful way to flatten the data by focusing on the things that are different between cells.

Here, the weights are termed Loadings. And array of loadings is called “Eigen Vector”.

PCA review :

- Systematized way to transform input features into principal components (PC)
- Use new PCs as new features.
- PCs are directions in data that maximize variance when you project/compress down onto them.
- The more variance of data along a PC, the higher that PC is ranked.
- Most variance, most information would be the first PC.
- Second-most variance would be the second PC.
- Max number of PCs = number of input features.

Typical example of PCA is in eigenfaces.

PCA is a linear algebraic approach.

**Independent Components Analysis (ICA)**

It  is a computational method for separating a multivariate signal into additive sub-components. This is done by assuming that the sub-components are non-Gaussian signals and that they are statistically independent from each other.

A common example application is the “cocktail party problem” of listening in on one person’s speech in a noisy room.

ICA is a probabilistic approach.

**Random Component Analysis (RCA)**

Uses random way to transform input features into principal components (PC)

**Linear Discriminant Analysis (LDA)**

Finds a projection that descriminates based on the label.


Fundamental assumption is different, although they do the same thing, which is to capture the original data in some new transform space that is somehow better. 
