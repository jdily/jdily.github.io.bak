---
layout: post
title : Energy discussion
category: draft
use_math: true
---
### normalization problem
I think we may have problem with our current energy due to non-equal spacing.
For the local smoothing operation, i.e. only term1

$$  \sum_{e_i} W_1(e_i)\| e_i - (e_{i-1}+e_{i+1})/2\| _2^2 $$ 

we are trying to minimize the distance of blue arrow in the figure below (i.e. minimizing curvature) by encouraging flatten.

![minimize curvature]({{ site.url }}/images/mini_curvature.png)

In this case, straight line should minimize this energy. However, I think that only happens when the spacing is equal. 

If all our results (e_i's) are lying on the same line, as shown below:

![spacing comparison](https:https://drive.google.com/file/d/0B-_yFoUkpgf1LWdRaDM0NDVfcWM/view?usp=sharing)

As we can see in the figure, if the spacing is not equal, then even straight line can not minimize this energy, even though the curvature is already minimized..
So I think the energy may need to be modified as taking the edge length proportion into consideration..

### angle version!?