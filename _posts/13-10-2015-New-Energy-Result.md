---
layout: post
title : Results from new optimization function
category: progress		
use_math: true
---
I have the first version of a new alternative solver to solve our new optimization function.
Let me briefly re-explain what I am doing in this solver.
Here is the function:

$$ E_{curve} = E_{min} + E_{const}$$

Here we first define a laplacian function for each $e_i$:

$$ \mathcal{L}(e_i) = e_i - (w_{i-1}^{i}e_{i-1}+w_{i+1}^{i}e_{i+1})  $$

$$ E_{min} = \sum_{e_i} \mathbf{W}_1(e_i)\| \mathcal{L}(e_i) - b_i^1\| _2^2 $$

$$ E_{const} =  \sum_{e_i } \mathbf{W_2}(e_i) \| \mathcal{L}(\mathcal{L}(e_i)) - b^2_i  \|_2^2 $$

### Optimization process
1. initialize the variables ($t_i$ for each $e_i$) as 0.5.

> **TODO**: check whether initial values of $t_i$ affects the results. 

2. Use current $e_i$ to compute the weights for laplacian
3. Solve $e_i$ by optimizing $E_{curve}$ with know weights from step 2.

**Repeat 2, 3 until converge**..

### Optimization result.
For all the results shown below, I first set both $\mathbf{W}_1$ and $\mathbf{W}_2$ as 0.5, for every $e_i$.

**Please see the following results:**

- <https://www.cs.ubc.ca/~ichaos/research/nbview/alt-solver-viz-bubble.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/alt-solver-viz-circle109.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/alt-solver-viz-heart298.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/alt-solver-viz-phone.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/alt-solver-viz-rect1.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/alt-solver-viz-rect2.html>
- <https://www.cs.ubc.ca/~ichaos/research/nbview/alt-solver-viz-triangle36.html>

> **Discussion**:  
> 1. I think the visualization is not so easy to view, do you have any good suggestion to show the boundary lines clearer? (in contrast to the background shape..)  
> 2. Right now we have two kinds of weights  
	1. spatial-varying weights Alla proposed : ($$\mathbf{W}_1$$ and $$\mathbf{W}_2$$)  
	2. the weights for distance weighted laplacian ($$w_{i-1}$$ and $$w_{i+1}$$ and more in $$\mathcal{L}(e_i)$$)        
> I think we can come up some different names or notations for express them. Or it is a little bit confusing during discussion..
> 3. I'll start to work on manually assign different **spatial-varying** weights.   
> 4. I am also interested in testing the different initialization values for each $t_i$.    
> 5. Observed from all the above examples, I found out that our thoughts about bias term might be right.   
The reason is that for most of the new optimized results I got, their energies are lower than their ground truth's energies.
I think this means to ``reproduce'' the ground truth, the targets of laplacian and bi-laplacian are not perfectly zero.
(I do found out this during some tests, so if needed, I can come up some tables to show these statistics.)