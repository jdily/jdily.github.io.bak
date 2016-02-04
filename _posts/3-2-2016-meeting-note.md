---
layout: post
title : Feb 03, 2015 Meeting note
category: meeting
use_math: true
---
## Notes
- A top-down approach to fit primitives, (ref : GlobFit @ SIGGRAPH 2011) :
    - GlobFit got global info, and Cornucopia use local info, and we want to combine both...
    - we want to fit a family of primitives within our **interval**..
        - line, arc, clothoid, hermit...
    - simultaneously, we expect that the number of primitives as small as possible..
    - The process should be like the following: (I will write down a pseudocode like thing in another document that we can discuss algorithm):
        0. fit initial primitive to entire samples, it one fit, e.g. one circle fit, then done.
        1. detect sharp corners, and get segments...
        2. fit regular primitives to a segment (span)
        3. see whether the same fit (parameter of the primitive) can be fit else where.. (global relationship, e.g. parallel or orthogonal for line...)
        4. if unmatch for all primitive -> consider further segment -> fit primitive or smooth curves...
        5. consolidate and see whether we can reduce the primitive set smaller..
- identify the joint between    
    - line v.s. arc
    - arc v.s. arc
    - arc v.s. clothoid ..etc..


## Todos
- start to fitting the basic primitive:
    - line
    - arc
    - clothoid - find the fitting method..
- write down the algorithm and optimization part and discuss and refine with all..
- read the reference including:
    - GlobFit
    - Conjoining Gestalt Rules for Abstraction of Architectural Drawings
