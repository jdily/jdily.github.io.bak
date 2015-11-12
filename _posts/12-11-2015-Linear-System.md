---
layout: post
title : Linear System 
category: draft
use_math: true
---
## The linear system
If we only look at the third term (laplacian positioning term) : $$ ( L(e_i) -d_i )^2  $$, I think we got 

$$e_i - 0.5 e_{p} - 0.5 e_{n} - d_i = 0 $$

where $p = i-1$ and $n = i+1$.

So far, I formulate the optimization in terms of $t_i$, so the previous equation can be transformed into:

$$ 
P_{i0}\cdot (1-t_i)+P_{i1} \cdot t_i - 0.5 \cdot (P_{p0}\cdot (1-t_p)+P_{p1}\cdot t_p) - 0.5 \cdot (P_{n0}\cdot (1-t_n)+P_{n1}\cdot t_n) 
= d_i
$$

$$
t_i \cdot (P_{i1} - P_{i0}) - t_p \cdot 0.5 \cdot (P_{p1}-P_{p0}) -  t_n \cdot 0.5 \cdot (P_{n1}-P_{n0}) =  d_i - P_{i0} + 0.5\cdot P_{p0} + 0.5\cdot P_{n0}
$$

and all the $P_{xx}$ and $d_i$ are 2D vectors in current 2D setting.
It means we have two equations for each $i$, i.e. 

$$
t_i \cdot (P_{i1}.x - P_{i0}.x) - t_p \cdot 0.5 \cdot (P_{p1}.x-P_{p0}.x) -  t_n \cdot 0.5 \cdot (P_{n1}.x-P_{n0}.x) =  \\
d_i .x- P_{i0}.x + 0.5\cdot P_{p0}.x + 0.5\cdot P_{n0}.x
$$
and 

$$
t_i \cdot (P_{i1}.y - P_{i0}.y) - t_p \cdot 0.5 \cdot (P_{p1}.y-P_{p0}.y) -  t_n \cdot 0.5 \cdot (P_{n1}.y-P_{n0}.y) =  \\
d_i .y- P_{i0}.y + 0.5\cdot P_{p0}.y + 0.5\cdot P_{n0}.y
$$


and i think it leads to an over-determined system.
So if we have $n$ unknowns (i.e. $$t_0... t_{n-1}$$), then we will get a $$2n\times n$$ matrix $A$ before add any positional constraints (boundary condition.)