---
layout: post
title: Optimization draft
category: progress
use_math: true
---
## Optimization with spatial-varying weights 

$$ E_{curve} = E_{min} + E_{const}$$

### Term1 : minimizing curvature  $$ (E_{min})  $$

$$  \sum_{e_i} W_1(e_i)\| e_i - (e_{i-1}+e_{i+1})/2\| _2^2 $$ 

### Term2 : keeping curvature constant  $$ (E_{const})  $$

$$  \sum_{e_i } W_2(e_i) \| e_i - (e_{i-1} + e_{i+1})/2  - (e_{i-1} - (e_{i-2} + e_{i})/2 + e_{i+1} - (e_{i} + e_{i+2})/2  )/2  \|_2^2 $$          

### Note 

- Now I use square distance of 2-norm.
- The only constraints I have now for each $e_i$ is $ 0 \leq e_i \leq 1$.
 
### Experiment 

To try out the optimization, I optimize different shapes and different weights combinations.

#### uniform weights 

In these examples, I use both weighting as 0.5, i.e. $W_1(e_i) = 0.5, W_2(e_i) = 0.5$ for each $i$. 


Please see the following results:

- <https://www.cs.ubc.ca/~ichaos/research/nbview/solver%20viz-circle109.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/solver%20viz-rect1.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/solver%20viz-heart298.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/solver%20viz-triangle36.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/solver%20viz-phone.html>

#### spatial-varying weights

The thing is that I tried to add anisotropic weights into the optimization, but I didn't get reasonable results when I manually set the weights.
Most of the time, the result are just very close to the isotropic weights results.
So I did a test that randomly generate the weights for every $e_i$, and the results still looks very close, and the optimized energy from the solver are close.

I am trying to find out what is the problem right now... 