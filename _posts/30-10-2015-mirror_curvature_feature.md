---
layout: post
title : Curvature, mirror feature discussion
category: draft
use_math: true
---
I try to draw some diagrams to describe my idea and combine the mirror idea that Nathan mentioned in the morning.
The window size used in the figure below is 9, i.e. 4 on each directions.
There are two parts in this draft:

### Feature with laplacian or curvature value

#### training 
we feed several $(F_i, R_i)$ pairs to network, and try to learn the regression function for the laplacian vector.

#### testing
use $F_i$ as query and infer the learned regression function for target $R_i$ (result laplacian vector from ground truth).

Here I focus on discussion of the **feature vector** ($F_i$) part, and the result vector ($R_i$) is still a laplacian vector from ground truth shape. 
I try to come up some new thoughts for feature vectors, and I summarize some thoughts here (please see the figure below).
We begin from the low-resolution shape image, and we have local raw representation (the red dots in the figure connected by the green arrows) in the figure: 

* laplacian vector feature : use local raw representation to compute local laplacian vector $$ \mathcal{L}(e_i)$$, resulted in a 18-dim vector.
Please noted that the blue dots in the figure means zero vectors.
* curvature value feature : local curvature measured by $$ \| \mathcal{L}(e_i) \|_2$$, results in a 9-dim vector.
The 3 in the figure is just a example non-zero curvature number.

The black arrows in the figure represent $R_i$ (ground truth laplacian vector).

### Mirror feature

For the example in the figure, I draw three different versions of them:

* $M_y$: mirror of y-axis 
* $M_x$: mirror of x-axis
* $M_x M_y$: mirror of y-axis and then x-axis

![illustration]({{ site.url }}/images/curvature_feature_mirror.png)

### Discussion

#### result ambuiguity
 
Originally I am thinking if we can extract some real-value only and use them as feature, which is curvature value feature.
However, if I insert the original feature (0 0 3 0 3 0 0 0 0) into database, and  then I want to also insert Mirror x version into database,
it lead to an ambiguity.
Both of them share the same feature vector (0 0 3 0 3 0 0 0 0), however, the desired result laplacian vectors are not in the same direction.
So I think I will use the **laplacian vector feature** instead.

#### Avoid direction inference

Right now, we try to infer both the direction and the magnitude in both x and y direction of the laplacian vector.
(So we may get (-0.2, 0.5), (0.2, -0.5), (-0.2, -0.5), (0.2, 0.5) so on...)
I am  thinking about if we can reduce the burden of the inference, say, only ask it for magnitude of both x and y direction.
And we decide the direction based on some local geometry, e.g. try to compute the normal at each sample location.





 
