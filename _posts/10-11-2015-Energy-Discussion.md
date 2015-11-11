---
layout: post
title : Energy discussion		
category: draft
use_math: true
---
## Optimization function with two terms and spatial-varying weights 

$$ E_{total} = \sum_{e_i} w_i^L (L(e_i))^2 + \sum_{e_i} w_i^C (C(e_i))^2$$,

where $$L(e_i)$$ is the local laplacian, and $$C(e_i)$$ is bilaplacian.

### Goal describe: 

#### Training 
With ground truth shape in hand, we know all the $$e_i$$ so we know all the $$L(e_i)$$ and $$C(e_i)$$, so we can formulate a linear programming with unknown $w_i^L$ and $w_i^C$.
With constraints like $$\sum_{i}w_i^L= n$$, and $$\sum_{i}w_i^C = n$$ (n is the number of total sample in the shape, it can be also normalized as 1.).
And our dataset will consist of pairs of local shape pattern (low resolution feature) with $$w_i^L$$ and $$w_i^C$$.

#### Reconstructing
For reconstruct, using each local pattern, we infer the corresponding $$w_i^L$$ and $$w_i^C$$ through the learning method.
And we use these $$w_i^L$$ and $$w_i^C$$ to complete the formulation and solve for $$e_i$$.

#### Problem1 : linear programming regularize?
When solving this linear programming, it will leads to a very big value assign to the smallest laplacian value sample and to the smallest bilaplacian value sample.
So for example, with a circle shape with 180 samples, the output of w_i^L will be a vector with all 0 but only 1 180 which assigned to the smallest laplacian e_i.
And on the other hand, the output of w_i^C will be a vector with all 0 but only 1 180 which assigned to the smallest bilaplacian e_i.

#### Problem 2 : relative weight value meaning..
When solving the linear programming, we set some constraints like $$\sum_{i}w_i^L= n$$, and $$\sum_{i}w_i^C = n$$ (n is the number of total sample in the shape, it can be also normalized as 1.).
I think the spatial-varying weighting here represents, for each term, it's strongeness is different from sample to sample, so it's a relative value.
However, this relative value, may not be able to use across different shapes.

For example, I have a circle with 180 samples, and another shape, with 100 samples.
Even though there is a same local pattern happens in both shape, and their weight value are both 10, but the absolute value 10 means different in both shapes.
