---
layout: post
title : Rotation issue
category: draft
use_math: true
---

I think I found some interesting examples that bothers me in the beginning, about the rotation issue we discussed today.
We still take circle as example, and look the following example:
All the four points in this figure have the same feature vectors.

![sync example]({{ site.url }}/images/sync_example.png)
and their laplacian vectors are listed as follow:

|  index | laplacian  | 
|:--:|:---:|
| 16 | (-0.00243961, -0.00294993) |
| 61 | ( -0.00294993, 0.00243915 ) |
| 106 | ( 0.00243915, 0.00294946 ) |
|151| ( 0.00294946, -0.00243961 ) |

After aligning all of them to face downward, the rotated laplacian vectors are 

|  index | laplacian  | 
|:--:|:---:|
| 16 |( 0.00243961, 0.00294993 )  |
| 61 |( 0.00243961, 0.00294946 ) |
| 106 | ( 0.00243915, 0.00294993 ) |
|151| ( 0.00243915, 0.00294946 ) |

where all of them aligns pretty well.

However, there are some other exceptions :
All the four points in the next figures have the same feature vector
![unsync example]({{ site.url }}/images/unsync_example.png)
 
|  index | laplacian  | 
|:--:|:---:|
| 3 | ( 4.92395e-07, 1.19333e-07 ) |
| 48 | ( 1.19333e-07, 9.97721e-07 ) |
| 93 | ( 9.97721e-07, 1.37078e-06 ) |
|138| ( 1.37078e-06, 4.92395e-07 ) |

After aligning all of them to face downward, the rotated laplacian vectors are 

|  index | laplacian  | 
|:--:|:---:|
| 3 | ( -4.92395e-07, -1.19333e-07 ) |
| 48 | ( 9.97721e-07, -1.19333e-07 ) |
| 93 |( 9.97721e-07, 1.37078e-06 )  |
|138| ( -4.92395e-07, 1.37078e-06 ) |

Most of these kinds of laplacian vectors have values very close to 0, and most of all the bigger value laplacian vectors are well aligned.
