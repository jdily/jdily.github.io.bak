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

For each sample location, we open a window (like the figure below, the size in this example is 11, 5 for each direction), and the **raw representation** of this place is the relative coordinates we used right now.
So far, we feed these locations w/o any further information, so the current feature $$f_{i} \in \mathcal{R}^{20}$$is 

$$ 
f_{i} = (\mathit{P}_{-5}(x, y), \mathit{P}_{-4}(x, y), \mathit{P}_{-3}(x, y), \mathit{P}_{-2}(x, y), \mathit{P}_{-1}(x, y), \\
 \mathit{P}_{1}(x, y),  \mathit{P}_{2}(x, y),  \mathit{P}_{3}(x, y),  \mathit{P}_{4}(x, y),  \mathit{P}_{5}(x, y))
$$

and expect the network to extract some hidden information base on this.
![raw representation]({{ site.url }}/images/local_window.png)

And what I am trying to think is that if we can extract some information from this initial shape.
Say, treat it also as a shape, and extract the curvature value using $$ \| \mathcal{L}(e_i) \|_2$$, where $\mathcal{L}$ is the laplacian operator.
So in this case, our feature vector $$\tilde{f}_{i} \in \mathcal{R}^{11}$$ will become like:

$$ 
\tilde{f}_{i} = (\mathit{K}_{-5}, \mathit{K}_{-4}, \mathit{K}_{-3}, \mathit{K}_{-2}, \mathit{K}_{-1}, \mathit{K}_{0},  
 \mathit{K}_{1},  \mathit{K}_{2},  \mathit{K}_{3},  \mathit{K}_{4},  \mathit{K}_{5})
$$

And this is correspond to Zhaowen's manually extract some information.

### Discussion about add four training set for each location..

[![Thumbnail](http://CoSketch.com/SavedImages/pvaXBa2Y.thumb.png "Click to enlarge")](http://CoSketch.com/Saved/pvaXBa2Y)










