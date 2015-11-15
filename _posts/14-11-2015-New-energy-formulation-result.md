---
layout: post
title : New energy and some results
category: progress
use_math: true
---
## New Optimization function with four terms 

$$ F(\mathbf{t}, \sigma_B, \sigma_L, C) = \sum_{i} w_i^L \cdot (L(e_i) )^2 + \sum_{i} w_i^B\cdot(B(e_i))^2 \\
     + \sum_{i} w^D_i \cdot (L(e_i) -d_i)^2 + \sum_{i} w_P \cdot (t_i-0.5)^2 $$

$$\mathbf{t} = <t_0, t_1, ... , t_{n-1} > $$

$$e_i = t_i\cdot P_{i0}+(1-t_i) \cdot P_{i1}$$

$$ w_i^L = e^{-(\frac{\|d_i\|}{\sigma_L})^2}, w_i^B = e^{-(\frac{\|b_i\|}{\sigma_B})^2}, w_i^D = C\cdot(2.0-w_i^L-w_i^B). w_P = 0.001$$.

## Results

The following results show different strategies of computing laplacian.
In general, the laplacian vector $$L(e_i) $$ is computed as $$ L(e_i) = e_i - a \cdot e_{i-1} + (1-a) \cdot e_{i+1}$$.
The constant results in the following pages use $$ a = 0.5 $$ across all iterations.
The update results in the following pages update $$ a $$ for every iteration using the update mesh.
<http://www.cs.ubc.ca/~ichaos/research/nbview/circle109-a-comp.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/rect1-a-comp.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/rect3-a-comp.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/rect4-a-comp.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/flag-a-comp.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/pacman-a-comp.html>

For different shapes, we should apply different  $$\sigma_L, \sigma_B$$, and $$C$$.
I listed some experiment in the following pages.
For each case, I tested different sets of parameters after 1, 2, 10 iterations.
As we can find out, for shapes with sharp corner like rect, the sigma should be small enough that don't smooth out the structure.
Noted that the $$w_D^i = c \cdot (2.0-w_L^i-w_B^i) $$, which is compliment to the other two weights.
For the smooth shape, we then have to enlarge the sigma for better smoothing results.
<http://www.cs.ubc.ca/~ichaos/research/nbview/circle109-grid-tuning.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/rect1-grid-tuning.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/pacman-grid-tuning.html>
 
