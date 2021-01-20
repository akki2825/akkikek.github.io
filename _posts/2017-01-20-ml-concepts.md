---
title: "Notes: Few concepts of machine learning"
categories: [machine-learning]
---

*Deduction*: Given the rule and the cause, deduce the effect.

*Induction*: Given a cause and an effect,  induce a rule.

*Abduction*: Given a rule and an effect, abduce a cause.

*TAXONOMY*

What?   –  Parameters, structure, hidden concepts

What from?   –   Supervised, Unsupervised, Reinforcement

What for?    –     prediction, diagnostics, summarization

How?     –     passive, active, online, offline

Outputs?   –      Classification, Regression

Details?     –    Generative, Discriminative

Occom’s Razor – Everything else being equal, choose the less complex hypothesis.

The Ultimate goal of Machine Learning is to have data models that can learn and improve overtime. 

**Evaluation Metrics**

Learn from data to make predictions.

Classification is about deciding which categories new instances belong to. Then when we see new objects we can use their features to guess which class they belong to.

In regression, we want to make a prediction on continuous data.

In classification, we want to see how often a model correctly or incorrectly identifies a new example, whereas, in regression we might be more interested to see how far off the model’s prediction is true from true value.

Classification ⇒ Accuracy, precision, recall and F-score.

Regression ⇒ mean absolute error and mean square error.

Short comings of accuracy:

- Not ideal for skewed classes
- may want to err on side of guessing innocent.
- may want to err on the side of guessing guilty.

Causes of Error:

- Bias due to a model being unable to represent the complexity of the underlying data.

- Variance due to a model being overly sensitive to the limited data it has been trained on.

- Bias occurs when a model has enough data but is not complex enough to capture the underlying relationships. As a result, the model consistently and systematically misrepresents the data, leading to low accuracy in prediction. This is known as Underfitting. To overcome error from bias, we need more complex model.

- Variance is a measure of how much the predictions vary for any given test sample. High sensitivity to the training set is also known as Overfitting. Occurs when the model is too complex.

- We can typically reduce the variability of a model’s predictions and increase precision by training on more data. If more data is unavailable, we can also control variance by limiting our model’s complexity .

Data Types:

- Numeric data
- Categorical data
- Time-Series data

**Curse of Dimensionality**

As the number of features or dimensions grows, the amount of data we need to generalize accurately grows exponentially.
