---
layout: post
title : Oct 14, 2015 Meeting note
category: meeting
use_math: true
---
# Notes##
![meeting sketch]({{ site.url }}/images/note-20131014.png)

-  there is no need to keep both laplacian and bi-laplacian in the same time if we add **data-driven** bias term.
	-  In the sketch figure, basically if we keep both terms and use weights to control the local behavior, it's basically similar to use only one term with spatial-varying bias term. 

- we can get two things from ground truth (and those are things that we can possibly infer from data), please see triangle in the figure:
	- laplacian vector
	- weights for weighted laplacian ($w_p$ and $w_n$)
	
And we have two strategies to tackle this problem:

1. learn all those values (3 values in 2D, including 2-dim laplacian vector, and one scalar weight ($w_p+w_n=1.0$) ).
2. only learn laplacian vector, and use alternative optimization to optimize $w_p$ and $w_n$.	
