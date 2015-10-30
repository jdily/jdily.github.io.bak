---
layout: post
title : Feature illustration
category: draft
use_math: true
---
For each shape, in both training and testing phase, we start from the low-resolution image, 

- we start from sampling points at the center of each open edge (the red dot in the figure below).
- After this step, we already got the initial connectivity (or say topology) of the desired shape (the green line in the figure).

In my understanding, our problem can be viewed as given this topology, we want to refine the shape to match some properties, e.g. desired curvatures in our current case.
![raw representation]({{ site.url }}/images/topology.png)

With the fixed topology, what remain to decide is the positions of the vertices.

For each sample location, we open a window (like the figure below), and the **raw representation** of this place is the relative coordinates we used right now.
So far, we feed these locations w/o any further information, and expect the network to extract some hidden information base on this.
![raw representation]({{ site.url }}/images/local_window.png)

And what I am trying to think is that if we can extract some information from this initial shape.
Say, treat it also as a shape, and extract the curvature value using $ \| \mathcal{L}(e_i) \|_2$, where $\mathcal{L}$ is the laplacian operator.
And this is correspond to Zhaowen's manually extract some information.








