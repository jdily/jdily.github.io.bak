---
layout: page
title: Problem
use_math: true
---
## Overview ##
-------------
(We first discuss **2D** case only. )
Consider a $w\times h$ binary image $I$ contains a single shape, and it's polygon representation  $S$.
Pixels in $I$ can be classified into shape pixels $P_s$ (white) and background pixels $P_b$ (black).
> Our goal is given the shape pixels $P_s$, we want to recover it's shape polygon $S$.

Our problem consists of two stages: **training** and **prediction**. 
Now we first discuss a simple setting, say we only have one training shape (star) and one testing shape (triangle).
We will extract features from both shapes. 

## Training ##
-------------
> **TODO**:  
> 1. describe the generation of training data (both feature and crossing value).

## Prediction ##
-------------
We separate prediction part into two steps:   

1. **Pattern Matching**: using network to do the feature pattern->crossing value mapping, because it's hard to formulate as a numerical optimization.
2. **Post-optimization (smoothing)** : this one is easier to do optimization.

####variables ####
Currently we have each $e_i$ as **mid-edge** point.  (we can also switch according to Alla's suggestion.)

$$e_i = p_{i1}*(1-t) + p_{i2}*t$$

### Pattern Matching###
After training, we will get  a regression function $\Phi$ (a trained model).
For each boundary pixel, we extract it's feature $f_i$, and predict the crossing value ($e_i$) using:

$$\Phi(f_i) = e_i$$

### Post-optimization ###

####objective function ####
Here we try to leverage local laplacian, i.e. describe a pixel crossing with two neighbors' crossings.

**Laplacian** : local coordinate $$ \delta_i = e_i - \frac{1}{2}(e_{i-1}+e_{i+1})$$

**Energy** (similar to [^Sorkine2004]): 

$$E({e}') = w_r\sum_n \|\delta_i - L({e_i}')\|^2 + w_d\sum_n \| {e_i}'-e_i\|^2$$

${e}'$ is the optimized point position, $L$ is the laplacian operator. 
By minimizing this energy, we hope the optimized position ${e_i}'$ can be as close to the predicted value $e_i$.
Meanwhile, we also want to maintain the local coordinate, i.e. $\delta_i$.

> **Problem**  
> - After getting the output from network (pattern matching step), i.e. bunch of initial $e_i$, we don't have the local coordinate of the testing shape (in this case, the **triangle**).  

## Feature##
> **TODO**:  
> 1. describe the properties of the features, context or context-free..

## Reference ##
[^Sorkine2004]: Olga Sorkine and Daniel Cohen-Or and Yaron Lipman and Marc Alexa and Christian R\"{o}ssl and Hans-Peter Seidel, 2004, "**Laplacian Surface Editing**",   SGP.