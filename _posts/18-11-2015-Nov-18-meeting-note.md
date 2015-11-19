---
layout: post
title : Nov 18, 2015 Meeting note
category: meeting
use_math: true
---
## Notes
- There are mainly two parts in today's discussion:
	- parameter learning for single shape.
	- parameter learning for multiple shape.

### For single shape
- check the parameter learning optimization on some other example shapes.
- compare the learned parameter with manually set parameter after several iterations..
	- This is to prove that the parameter learning is useful that we can get results more similar to ground truth shape.
- check whether we should keep doing parameter learning iteration by iteration. To check this, we can compare:
	- multiple iterations of reconstructions with fixed parameters learned from single iteration parameter learning.
	- multiple iterations of reconstructions with updated parameters.
- We also have to check whether the convergence of both reconstruction optimization (i.e. optimize t), and parameter learning optimization (i.e. optimize $\sigma_L$, $\sigma_B$, and $C$)
 
### For multiple shape
Assume for each shape, we get corresponding parameters  ($\sigma_L$, $\sigma_B$, and $C$), or parameter sets (multiple $\sigma_L$, $\sigma_B$, and $C$ across different iteration.), how we combine these information, and for a new shape, we can come up new parameters for it?

#### Learning approaches
We can utilize multi-class classification algorithm like linear classification or SVM, classify some template shape we have, with their corresponding parameters. 
And for each new shape, we can predict the possibilities of them being different classes, and use that as confident to weighted average the parameters.

####  Feature space
For learning parameters across different shapes, we need to find the right parameter spaces for **global** or **local** structure.
One possible direction is to extract the histogram of curvature, or the laplacian vectors.

## TODO 
1. run the parameter learning only 1 iteration for different shapes, and see the behaviour.
2. do the parameter learning for multiple iterations, and compare the reconstruct result with 
    - fix parameter (only one iteration parameter learning) and 
    - manually set parameter.
3. after getting the above steps, I can  start to work on learning from multiple shapes, both training and testing step...
 


