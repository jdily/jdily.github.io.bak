---
layout: post
title : Revised optimization function
category: draft
use_math: true
---
According to the discussion on Oct 07, we have to modify the function in terms of the problem mentioned in 
<http://jdily.github.io/draft/2015/10/06/Energy-Discussion/>

Also, we want to add a bias term for each data point, i.e. $b_i$, to reveal the fact that not all laplacian values from ground truth are 0..

## Optimization with weighted laplacian (i.e. normalize the distance)

$$ E_{curve} = E_{min} + E_{const}$$

### Term1 : minimizing curvature  $$ (E_{min})  $$

$$  \sum_{e_i} \mathbf{W}_1(e_i)\| e_i - (w_{i-1}e_{i-1}+w_{i+1}e_{i+1}) - b_i\| _2^2 $$

where $b_i$ is a bias value for each $e_i$, and we can learn this $b_i$ from data.


### Implementation

#### variable : 

### Term2 : keeping curvature constant  $$ (E_{const})  $$

$$  \sum_{e_i } W_2(e_i) \| e_i - (e_{i-1} + e_{i+1})/2  - (e_{i-1} - (e_{i-2} + e_{i})/2 + e_{i+1} - (e_{i} + e_{i+2})/2  )/2  \|_2^2 $$          

