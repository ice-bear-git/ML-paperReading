# Anticorrelated Noise Injection for Improved Generalization
First Read on Feb 14


## State at Front
This paper has solid math support by laying out equation and develop theorems, and is good for building a solid understanding toward Noise Injection Techniques. And this paper let me know: **Besides applying Noise Injection on Data Augmentation and including its in Loss function, we can directly add noise onto optimizer! Good to know!**
  

**Although it has strong mathmatical/theoretical Analysis, I still believe this paper is inspired by an empirical result.-- See The order inside section 3**

## Main content
This paper zooom in on the problem of *correlating the perturbations* of consecutive *perturbed gradient descent* (PGD) steps. They find *anticorelated pertubations "Anti-PGD"* generalizes significatnly better than normal GD and standard PGD.

### Why add Noise onto Optimizer
We want flat minima generalize in loss landscapes of overparameterized models, as flatness itself is sufficient to determine weights with low precision. However, usually those overparameterized model usually have hugh generalization gap. Hence, we have standard stochastic gradient descent (SGD) that is trying to survive. To speed up the escaping process, we introduce perturbation to SGD and make them become PGD. Now, focusing on the perturbation term, this paper correct the noise and make them anti-correlated! Therefore, Anti-PGD can survive from most case with much faster converging speed.

#### Noise Analysis on GD
Although we usually keep using Adam and normal SGD for the most cases, the analysis on generalization measures and SGD optimizer have been done alot.
* Smaller Hessian loss indicate good generalization  performance
* The experimental finding of correlation between loss landscape flatness and good generalization should not necessarily be regarded as a causal relationship ---  theory and pratice gap
* Experimentally, **the intrinsic noise of SGD helps overparamterized models to find minima that generalize supreisinly well.** By increasing levels of noise, the convergence to flat minima feature seems show up.
* In term of Noise shape: heavy-trail noise leads to faster escape from sharp minima
* Label corruption (noise) can also be a way to turn SGD to PGD

### Finding Flat Minima by Anti-PGD
Anti-PGD minimizes the trace of the Hessian

#### Anti-Correlated Vs. Un-Correlated
PGD: Un-correlated means "independent" -- Merely don't consider others -- Might hold 0 average correlation -- Discrete perturbation -- might **have half of redundant noise**!!    

Anti-PGD: Anti-correlated -- **Negative Correlated** --  Trying best to split the noise in multi-dimension -- its correlation is Negative One(-1). -- Consecutive perturbations -- Like a **full rank** noise matrix!! 

#### Math Equation


#### Regularization in Anti-PGD


#### Connection with PAC-Bayes bounds
PAC-Bayes: ?

These bounds connect to the curvature of the loss through the concept of expected sharpness.
Anti-PGD 

The lower the trace the higher is the test accuracy

#### Connection to Smoothing


### Convergence in widening valleys
We have seen above that Anti-PGD acts as a regularizer on the trace of the Hessian. In this section, we will analyze the dynamics of Anti-PGD in more detail on the "windening valley" -- The simplest possible loss landscpe with a changing trace of the Hessian

#### Theoretical Analysis
1. In high dimensions, PGD diverges away from zero

### ConClusion and Future Work




## Suppliment:
* Hessian 
Here is [Blog1](https://jamesmccaffrey.wordpress.com/2017/08/03/the-hessian-and-machine-learning/). It is a technique for machine learning optimization with invloves minimizing error to find values for neural network weights and biases.

Trace of Hessian == Eigenvalue of Hessian

The Hessian is **a matrix of all possible Calculus second derivatives for a function**. The Hessian can be used in two ways:
1. First, the so-called second derivative test to determine if a value is a function minimum or a maximum or undetermined. 
2. The second way to use the Hessian is directly, to iteratively get closer and closer to a minimum error.

**Notice that you need the inverse of the Hessian matrix. If you have 10 weights to solve for, the Hessian would be 10×10. So, this direct approach won’t work if n gets very, very large. Therefore there are several variations of this technique that estimate the Hessian in various ways.**

