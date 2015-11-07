---
layout: post
title : Data investigation
category: draft
use_math: true
---
I did a comparison for the laplacian inference using trained laplacian regression function, using linear regression, nearest neighbour and network.
You can find some comparison results in the following webpage (including numerical and shape comparison, ).
<http://www.cs.ubc.ca/~ichaos/research/nbview/exp4-val-linear-sound.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/exp4-val-linear-guitar.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/exp4-val-linear-mickey.html>
<http://www.cs.ubc.ca/~ichaos/research/nbview/exp4-val-linear-flag.html>

There are some confusion about the shape shown in the webpage, they are results of nearest neighbours, if needed I can also show all the results using different methods.

#### Thoughts

But the conclusion for the comparison is : **there are no huge differences between all these methods**.
The good thing is I think our problem formulation, in the beginning, already help us to reach a good point (the zero predict in the previous results show that even without inferred laplacian value, we can already get a fairly good overall shape.)
What we want to achieve is to infer good local structures (geometry feature) that captured in the data.

So I decided to do some investigation of our input data, especially the training data, with some visualization.

### Data distribution - output laplacian value

First thing that I tried to visualize is the distribution of the ground truth laplacian values in the training set.
I mentioned this before, but never try to visualize them, so here we go.
![ground truth laplacian distribution]({{ site.url }}/images/value_distribution.png)
Figure on the left hand side (green bars) is the distribution of **x-component**, and right hand side is the distribution of **y-component**.
According to the figures, I found out that most of our output values are very close to 0.
And there are very few laplacians are with bigger scale, but I think those bigger laplacians are the thing that we care about (because they represent the local feature.).

### Prediction value distribution
Next thing I did is I plot the distribution of both x- and y-components of output laplacian values in 2D (see the following fig).
(x-axis is for x-components, and y-axis is for y-components).
![output value distribution]({{ site.url }}/images/output_val_plot.png)
The blue dots are the ground truth points, the green dots are the predicted results using linear regression, and the red dots are predicted results using network.
As you can see, most of the predictions from both methods gather up close to the center (which is (0, 0) ), and fail to capture the bigger laplacians on the outside.

### Feature attributes and Predict value
I haven't have a very concrete idea of how to show this, but I also plotted something out, so I think it still ok to show it.
In the following two figs, I plotted some dimensions of the input features with a output dimension (e.g. dim 0 in the feature pair with dim 0 in result laplacian.)

This figure shows the relationship between different dimension in features and x-component in result laplacian.
![pair-x]({{ site.url }}/images/data_predict_plot_x.png)

This figure shows the relationship between different dimension in features and y-component in result laplacian.
![pair-y]({{ site.url }}/images/data_predict_plot_y.png)

So far, these figures just reveal the same thing with the previous figure, that all the predict values gather at centre area.


