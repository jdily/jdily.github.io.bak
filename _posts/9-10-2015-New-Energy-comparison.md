---
layout: post
title: New energy comparison
category: progress
use_math: true
---
According to the discussion on Oct 07, we have to modify the function in terms of the problem mentioned in 
<http://jdily.github.io/draft/2015/10/06/Energy-Discussion/>

Also, we want to add a bias term for each data point, i.e. $b_i$, to reveal the fact that not all laplacian values from ground truth are 0..

## Optimization with weighted laplacian (i.e. normalize the distance)

$$ E_{curve} = E_{min} + E_{const}$$
Here we first define a laplacian function for each $e_i$:

$$ \mathcal{L}(e_i) = e_i - (w_{i-1}^{i}e_{i-1}+w_{i+1}^{i}e_{i+1})  $$

where $$w_{i-1}^{i}$$ denotes as weight for $e_{i-1}$ with respect to $e_i$.


### Term1 : minimizing curvature  $$ (E_{min})  $$

$$  \sum_{e_i} \mathbf{W}_1(e_i)\| \mathcal{L}(e_i) - b_i^1\| _2^2 $$

where $b_i^1$ is a bias value for each $e_i$, and we can learn this $b_i^1$ from data.

### Term2 : keeping curvature constant  $$ (E_{const})  $$

$$  \sum_{e_i } \mathbf{W_2}(e_i) \| \mathcal{L}(\mathcal{L}(e_i)) - b^2_i  \|_2^2 $$       

And can be expand as complicated version as follow:

$$  \sum_{e_i } W_2(e_i) \| e_i - (w_{i-1}^{i}e_{i-1} +w_{i+1}^{i}e_{i+1})  - ( {w}'_{i-1}[e_{i-1} - (w_{i-2}^{i-1}e_{i-2} + w_{i}^{i-1}e_{i})]+ {w}'_{i+1}[e_{i+1} - (w_{i}^{i+1}e_{i} + w_{i+2}^{i}e_{i+2})]  )  \|_2^2 $$  

where $${w}'_{i+1}$$ and ${w}'_{i+1}$  are respect to $\mathcal{L}(e_i)$.


## TODO:

- check rect1 groud truth   

|  data | type  | term1  | term2  | total |
|:--:|:---:|:---:|:---:|:---:|
| bubble  | gt | 0.33 | 0.35 | <font color='blue'>0.68 </font> |
|   |  optimized | 0.69 | 0.40 | 1.09|
|  circle109 | gt | 0.047 | 0.052 | <font color='blue'>0.099</font> |
|   | optimized | 0.69  | 0.61 | 1.30 | 
|  heart298| gt  | 0.39 | 0.45 | <font color='blue'>0.84 </font>| 
|  | optimized |0.74 | 0.47 | 1.21 | 
|  phone-hang-up | gt | 0.27 | 0.26 | <font color='blue'>0.53 </font>| 
| | optimized| 0.44 | 0.21 | 0.65 | 
|  <del>rect1</del>| <del>gt (wrong gt) </del>|  <del>0.67</del> | <del>0.84 </del>|<del> 1.51</del> | 
|  | <del>optimized</del> | <del>0.25 </del>| <del>0.06</del> |<del>0.31 </del>| 
|  triangle36| gt | 0.46 | 0.76 | <font color='blue'>1.22 </font>| 
| | optimized | 0.83 | 0.94 | 1.77 | 