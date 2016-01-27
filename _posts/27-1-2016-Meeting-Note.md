---
layout: post
title : Jan 27, 2015 Meeting note
category: meeting
use_math: true
---
## Notes
- detect corner
	- $C_1$ discontinuity
	- $C_2$ discontinuity
- make sure the rasterized results from the reconstructed curve is the same as the input.
- We can change to clothoid curve fitting instead of current fitting...
- One possible direction is to infer the hidden structure (global information) after segments reconstruction.
	- we can try to extrapolate the curve, and check whether the end points intersect with other segments.
	In this way, we can do a consistency optimization (update) after segment optimization.

## Todo
- try to use the clothoid code (cornucopia) , and apply it on our constrained curve reconstruction.
- detect C2 discontinuity.
- finish the entire pipeline.
- 