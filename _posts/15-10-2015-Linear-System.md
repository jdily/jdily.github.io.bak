---
layout: post
title : Linear System 
category: draft
use_math: true
---
## Detail of the linear system

For each $e_i$, we have 

$$e_i - w_{p}e_{p} - w_{n}e_{n} = b_i $$

where $p = i-1$ and $n = i+1$.

So far, I formulate the optimization in terms of $t_i$, so the previous equation can be transformed into:

$$ 
P_{i0}\cdot (1-t_i)+P_{i1} \cdot t_i - w_{p}\cdot (P_{p0}\cdot (1-t_p)+P_{p1}\cdot t_p) - w_{n}\cdot (P_{n0}\cdot (1-t_n)+P_{n1}\cdot t_n) 
= b_i
$$

$$
t_i \cdot (P_{i1} - P_{i0}) - t_p \cdot w_p \cdot (P_{p1}-P_{p0}) -  t_n \cdot w_n \cdot (P_{n1}-P_{n0}) =  b_i - P_{i0} + w_p\cdot P_{p0} + w_n\cdot P_{n0}
$$

and all the $P_{xx}$ and $b_i$ are 2D vectors in current 2D setting.
It means we have two equations for each $t_i$, and i think it leads to an over-determined system.
So if we have $n$ unknowns (i.e. $$t_0... t_{n-1}$$), then we will get a $$2n\times n$$ matrix $A$ before add any positional constraints (boundary condition.)