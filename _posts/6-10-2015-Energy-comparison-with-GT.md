---
layout: post
title: GT energy comparison
category: progress
use_math: true
---
### Compare energy with ground truth (L2)

I set both weighting 0.5, however, because I think the scale of two terms may not be equal.
So maybe they are not contributing equally.

|  data | type  | term1  | term2  | total |
|:--:|:---:|:---:|:---:|:---:|
| bubble  | gt | 7.16217|18.774 |25.93617 |
|   |  optimized | 2.13518|2.47112|4.6063|
|  circle109 | gt |7.29661|22.6688|29.96541|
|   | optimized |2.38505 |3.17509 |5.56014 | 
|  heart298| gt |11.3842|36.7804|48.1646| 
|  | optimized |1.89751|2.03962|3.93713| 
|  phone-hang-up| gt |4.8908|12.161|17.0518| 
| | optimized|1.31873|1.2576|2.57633| 
|  rect1| gt | 0.698162|0.745405|1.443567 | 
|  | optimized | 0.309573|0.066709|0.376282 | 
|  triangle36| gt |8.25513|21.9114|30.16653 | 
| | optimized | 2.50129|3.12958|5.63087| 

### Discussion
I think one interesting thing to think about is that, our ground truth, are not necessary be the optimal for this energy, right?
So for most cases (well, for all of these 6 examples), the optimized energies are lower than the energies from gt.

One intriguing result to me is about circle109...
Both terms from gt are higher than the optimized results (which is a wavy result, please see <https://www.cs.ubc.ca/~ichaos/research/nbview/solver%20viz-circle109.html>)