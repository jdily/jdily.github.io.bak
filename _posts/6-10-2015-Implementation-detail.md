---
layout: post
title : Implementation detail
category: progress
use_math: true
---
## Optimization with spatial-varying weights 

$$ E_{curve} = E_{min} + E_{const}$$

### Term1 : minimizing curvature  $$ (E_{min})  $$

$$  \sum_{e_i} W_1(e_i)\| e_i - (e_{i-1}+e_{i+1})/2\| _2^2 $$ 

### Implementation
#### variable : 

### Term2 : keeping curvature constant  $$ (E_{const})  $$

$$  \sum_{e_i } W_2(e_i) \| e_i - (e_{i-1} + e_{i+1})/2  - (e_{i-1} - (e_{i-2} + e_{i})/2 + e_{i+1} - (e_{i} + e_{i+2})/2  )/2  \|_2^2 $$          

