---
layout: post
title : Dec 16, 2015 Meeting note
category: meeting
use_math: true
---

## Notes
- Threshold for likelihood prediction
	- We should do some maximum suppression method here, that decide the local maximum, instead of using a global threshold for deciding the hard singular points from predicting likelihood
	- also, we can do a experiment : set the threshold manually, case-by-case, and observe whether the singular points are as expected..
- Likelihood prediction
	- visualize the predicted likelihood on the polylines
	- for each case, observe the peak in the plotting for different resolution (do at least 2 resolution for each shape, and compare.)
- New feature (context-less feature) that encode the neighbouring corners:
	- check the magnitude, and normalize it first before doing high dimensional plotting (because the plotting for ncontx feature and concatenate feature are similar..)
	- Sanity check for this feature-> use several simple primitives, like squares, rotated it...
- Find spatial feature
	- try to incorporate spatial information, using raw pixel value or shape context features..
- The curvy straight line around corner :
	- overlay the low-resolution image beneath, we should understand whether the low resolution input constrain us...
	- To debug, we can try to fix position of corner points, and try to do the optimization, observe the output straight line..
- bilaplacian term formulation
	- for soft weight, should also try to down weight the biliaplacian terms around the corner


## Todos
- visualize the likelihood values on polylines after prediction...
- observe the peak for different resolution, check out whether resolution can help to identify the singular points..
- find a way to identify local maximum (maximum suppression) as singular points.
- debug for the curvy line : (a) vis the low resolution beneath.
- debug for the curvy line : (b) find a simple case and fix positions for debugging.
- down weight biliaplacian terms for soft weight optimization..
- normalize the new feature, and check whether it helps for regression.
- add spatial feature, e.g. shape context feature descriptors..
