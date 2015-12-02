---
layout: post
title : Dec 02, 2015 Meeting note
category: meeting
use_math: true
---
## Notes

- Sampling problem : First I raised some issues that I also talked about in the email. And the reason why the [0,1] range is not guaranteed.
	- possible solution is to always find diagonal points as reference, but with ambiguities.
- The fitting curve : The current fitted curve are too rough, we have to finely fitted it by increase the detail of the fitting curve.
- Generate data for labeling singularity:
	- direct labeling on the resampled polygon is not right, it's not clear which points should be assigned as singularity.
	- The singularity should be labeled on fitted polygon, and then try to transfer to resampled polygon.
		- one method to do is find the closest sample in the resampled polygon.
	- singularity should be judged directly on the bezier curve.
- Some notes:
	- we should be careful about choosing the resolution. The resolution should be high enough to capture the geometry detail in the original shape.
		- one check is that if we singular points on the continuous shape results in a single sample, then it means we don't have enough resolution..
	
## Todos
- fitted a smoother curve to the original shape
- try to automatically pick the discontinuities on the bezier curves..
- transfer these discontinuities to the resampled polygon as label...
- extract feature and label to train classifier, train like a face detector (discuss with Zhaowen in detail.)
 

