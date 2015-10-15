---
layout: post
title : Some thoughts and experiment about simplified function.
category: progress		
use_math: true
---
## Simplified function

$$ E_{curve} = \sum_{e_i} \| e_i - (w_{i-1}^{i}e_{i-1}+w_{i+1}^{i}e_{i+1}) - b_i \| ^2_2$$

## Solve approach
To solve $E_{curve}$, we need $$w_{i-1}$$, $$ w_{i+1}$$ and $b_i$ for each $e_i$.

For $b_i$, we are basically try to learn it from data, so that it is a **data-driven** bias, that can encode style of the input dataset while we are reconstructing the surface.

For $$w_{i-1}$$ and $$w_{i+1}$$, they are used for compute the weighted laplacian.
And I think we have two different approaches to get these values.

### direct inferring 
As Nathan described in the meeting, because we can also get this values from ground truth, we can also try to learn it from data.
I put some initial results at 

<https://www.cs.ubc.ca/~ichaos/research/nbview/gt-laplacian-and-weights-results.html>

The results looks perfect, but I am still trying to figure out why I don't even provide a positional constraint.

### alternative optimization
I can also use alternative optimization method, that only take inferred bias as known, and alternatively optimize the weights and $e_i$.

<https://www.cs.ubc.ca/~ichaos/research/nbview/alt-opt-circle-comparison.html>
