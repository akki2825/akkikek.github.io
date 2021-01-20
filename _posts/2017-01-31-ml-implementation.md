---
title: "ML implementation"
categories: [machine-learning]
---

One secret you need to know beneath all of the math, and algorithms, is the “black art” to actually build machine learning models.

**Learning = Representation + Evaluation + Optimization**

The first problem faced by people is the bewildering variety of learning algorithms available. Which one to use? There are literally thousands available, and hundreds more published each year. The key to not getting lost in this huge space is to realise that it consists of combinations of just three components. The components are:

**Representation** : Choosing the representation for a learner is tantamount to choosing the set of classifiers that it can possibly learn. This set is called the hypothesis space.

**Evaluation**: An evaluation function is needed to distinguish good classifiers from bad ones. This might be accuracy, f1 score, squared error, information gain etc

**Optimization**: Finally, we need a method to search among the classifiers in the language for the high scoring one. The choice of optimization technique is key to the efficiency of the learner, and also helps determine the classifier produced if the evaluation function has more than one optimum.

The fundamental goal of machine learning is to generalize beyond the examples in the training set. 

Here are some of the hacks for implementing ML:

Do not contaminate your classifier by lots of tuning on the test data

Of course, holding out data reduces the amount available for training. This can be mitigated by doing cross validation: randomly dividing your training data into (say) ten subsets, holding out each one while training on the rest, testing each learned classifier on the examples it did not see, and averaging the results to see how well the particular parameter setting does.

Every learner must embody some knowledge or assumptions beyond the data its given in order to generalize beyond it. This was formalized by Wolpart in his famous “no free lunch” theorems, according to which no learner can beat random guessing over all possible function to be learned. Luckily, the function we want to learn in the real world are not drawn uniformly from the set of all mathematically possible functions!

Very general assumptions – like smoothness, similar examples having similar classes, limited dependencies or limited complexity are often enough to do well, and this is a large part of why ML has been so successful.

Bias is a learner’s tendency to consistently learn the same wrong thing.
Variance is the tendency to learn random things irrespective of the real signal.

Besides cross validation, there are many methods to combat overfitting. Th most popular one is adding a regularization term to the evaluation function. Anther option is to perform a statistical significance test like chi-square before adding new structures to decide whether the distribution of the class really is different with and without this structure. These techniques are particularly useful when data is very scarce.

Generalizing correctly becomes exponentially harder as the dimensionality as the dimensionality of the examples grows because a fixed-size training set covers a dwindling fraction of the input space.

“Blessing of non-uniformity” – in most applications examples are not spread uniformly throughout the instance space, but are concentrated on or near a lower dimensional manifold.
