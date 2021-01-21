---
title: "Artificial Neuron"
categories: [machine-learning]
---
Artificial neuron is simply a computational unit, which makes a particular computation based on other units it is connected to.

![Artificial Neuron](../images/io_neuron.jpg)

Pre-activation (or input activation): a(x) = b + ∑wi + xi

Neuron (output) activation: h(x) = g(a(x))

where, g(.) is called activation function, b is called neuron bias and w is the connection weights.


Activation functions:

- **Linear activation function**

    g(a) = a
    
    Performs no input squashing

- **Sigmoid activation function**

    g(a) = sigm(a) = 1/1 + exp(-a)
    
    Squashes the neuron’s pre-activation between 0 and 1.
    
    Always positive
    
    Bounded
    
    Strictly increasing

- **Hyperbolic tangent(tanh) activation function**

    g(a) = tanh(a)
    
    Squashes the neuron’s pre-activation between -1 and 1
    
    Can be positive or negative
    
    Bounded
    
    Strictly increasing

- **Rectified Linear Activation function**
    
    g(a) = reclin(a) = max(0,a)
    
    Bounded below by 0 and always non-negative
    
    Not upper bounded
    
    Monotomically increasing
    
    Tends to give neurons sparse activities. That is, the value is zero across many different sets of inputs.

**Capacity of a single neuron**

Capacity essentially means, the complexity of the computation that a neuron can perform.

- It could do binary classification with Sigmoid,
  which can interpret neuron as estimating p(y=1|x). That is, the probability of input ‘x’ belonging to class 1. (Since, we are using sigmoid activation function the output is bounded b/w 0 and 1). It is also known as logistic regression classifier. If the value is greater than 0.5, predict class 1, otherwise, predict 0.

- The classifier is performing linear classification, so, if we have a problem where we want to classify objects described by input vectors into different classes, if we can draw a hyperplane or a line (in case of 2d) between these two types of objects, then a single artificial neuron could do that for us!

- However, a single neuron cannot model a non-linearly seperable output.

If the input is transformed in a better representation, we can actually have a linear seperable.

Thereby, complicated computations cannot be modelled by single neuron. This is the main reason behind why we go for multilayer neural network.
