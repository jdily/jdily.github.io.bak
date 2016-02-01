---
layout: post
title : Cornucopia method
category: draft
use_math: true
---
Here I will describe the Cornucopia method, start from the input I feed into the method.
After short introduction of the method, I put some options that might be able to enforce the [0-1] range enforcement.

# Input
Given a set of sample points $$\mathcal{P} = \{  p_i \}_{i=1..n}$$, we first use the predicted sharp corner to partition $\mathcal{P}$ into $m$ segments, $$\{ \mathcal{S}_j \}_{j=1..m}$$.
And I put each segment individually into the method separately, i.e. the input the cornucopia now is $S_j$.

Note that in their method, they also did the same thing, first detect corner, and partition.
I just ignore the part in their method, and use our result.

# Method
![sync example]({{ site.url }}/images/cornu_overview.png)
*Cornucopia overview*

### Resample

### Primitive Fitting - primitive candidate
With the samples, the method start to fit primitives to every subsequence samples, resulting in a set of overlapping primitives (see (c) in the overview figure).
Here, all three types of primitives, including **Line**, **Arc** and **Clothoid** will be fitted.

| Primitive type| fitted analytic form|
| ------------- |:-------------:|
| line          | yes |
| arc           | no, use approximation      |
| clothoid      | no, use numerical fitting      |

### Graph Construction
The graph is constructed as follow:

- **node** : each node correspond to each fitted primitive. And we can set the node cost to allow/disallow certain type of primitive appear in the result.

- **edge** : edges are constructed for every possible transition between primitives, i.e. a primitive $C$ is connected to all other primitives ${C}'$ whose starting point is sufficiently close to the end point of $C$.
Edge encodes transition ($G^0$, $G^1$, or $G^2$)

### Shortest Path
Perform shortest path on the graph.
The output are a sequence of curve primitives and continuity constraints between them.
Note that the primitives do not satisfy the constraints.


### Merge Optimization
To obtain the final curve, we solve for the parameters of all parameters simultaneously, by minimizing the sum of squared distance from all samples to their curve primitives **subject to continuity constraints**.

# Rasterize contraint enforecement ([0-1] range)
1. Ignore [0-1] constraint initially, and still fit multiple primitives as the **Primitive Fitting** process before.
After we got those primitives, we encode the [0-1] constraints into the cost in **Graph construction**, and apply same shortest path to select the final output.

2. Get the output from the original method, and add a second optimization.
Like the merge optimization, they did a global optimization, that consider all the primitives they got after graph optimization.
We can design a optimization, with the goal as : alter the parameters as little as possible, but to obey the [0-1] range constraints.

For both approaches, we all need a metric that can measure how the primitive deviate from [0-1] range constraint.
More specifically, imho, we should decide **where to evaluate** this constraint on the primitive.
Also, for evaluating it, we might need the analytic form of every primitives.
