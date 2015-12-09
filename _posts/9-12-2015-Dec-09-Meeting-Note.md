---
layout: post
title : Dec 09, 2015 Meeting note
category: meeting
use_math: true
---

## Notes

- Feature problem:
	- the window size matters :
		- how large the window size can help us to identify  singularity visually?
		- can the larger window size make the feature separable in the high dimensional space?
	- some small hacks during the singularity point transfer process
		- pick the closest point that is not on the flat region, i.e. always assign the singular label to either concave or convex corner...
		- think about the problem: if the two neighbouring samples are very similar, but one is labeled as positive and one is not, it will be very hard to separate them with classifier..
	- feature augment:
		- one possible direction is to augment the feature with pixel value in the local window.
	- The evaluation should focus on doing the reasonable thing for a big shape set, not particularly on a single shape..

## Todos
- come up visual results and comparisons for evaluating window size for local shape pattern...
- do the small additional step for transferring the singular points.
- experiment with the context less shape feature.
- collect more shapes, and generate results automatically.
- try to augment the current feature..