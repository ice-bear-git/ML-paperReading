# Anticorrelated Noise Injection for Improved Generalization

## Abstract

## 1. Introduction

### suppliment:
* Hessian 
Here is [Blog1](https://jamesmccaffrey.wordpress.com/2017/08/03/the-hessian-and-machine-learning/). It is a technique for machine learning optimization with invloves minimizing error to find values for neural network weights and biases.

The Hessian is **a matrix of all possible Calculus second derivatives for a function**. The Hessian can be used in two ways:
1. First, the so-called second derivative test to determine if a value is a function minimum or a maximum or undetermined. 
2. The second way to use the Hessian is directly, to iteratively get closer and closer to a minimum error.

**Notice that you need the inverse of the Hessian matrix. If you have 10 weights to solve for, the Hessian would be 10×10. So, this direct approach won’t work if n gets very, very large. Therefore there are several variations of this technique that estimate the Hessian in various ways.**

#### SGD tends to find minima that generalize surprisingly well in overparameterized models. --- DUE TO ITS INTRINCIS NOISE