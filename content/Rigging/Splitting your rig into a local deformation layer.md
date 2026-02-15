---
date:
tags:
  - maya
  - rig
draft: false
---

## Overview

Here's a quick solution to a problem that rears it's head when you try moving an object that's deforming really far from origin and the vertices start to jitter. There's a great discussion ongoing regarding this on CGtalk ([http://forums.cgsociety.org/showthread.php?f=7&t=1305633](http://forums.cgsociety.org/showthread.php?f=7&t=1305633))

This is caused due to the vertex transformations being stored as floats, so when you start moving really far from origin (since the mesh transform stays at origin and your deformers are moving the vertices) you start running into floating point precision errors.

## The problem

![Untitled](Untitled.png)

Autodesk has a solution, which is to basically allow your mesh to move with the root, that way the vertex transformations aren't being calculated from massive distances. This will cause double transformations of course, so you'll need to negate the roots transforms from the skincluster ([http://knowledge.autodesk.com/support/maya/troubleshooting/caas/sfdcarticles/sfdcarticles/SkinCluster-deformations-at-large-distances-from-origin.html](http://knowledge.autodesk.com/support/maya/troubleshooting/caas/sfdcarticles/sfdcarticles/SkinCluster-deformations-at-large-distances-from-origin.html)).

Which is great, though you potentially have to negate a lot of influences (and this problem occurs for other deformers from what I've seen).

One quick solution is to split your deformations into a separate layer from your control hierarchy. It's not a new technique, it's quite a common technique to fix this problem in my experience and there have been DVD's explaining it in the past (I can't for the life of me remember which one, but it dated back to the mid 2000s I think).

So, how does this work? Basically you need to create another hierarchy which is a duplicate of the control/deformation hierarchy.

![Splitting the hierarchy into two layers](Untitled%201.png)

Splitting the hierarchy into two layers

Your control hierarchy will have direct connections back into the deformation layer for each influence. The only difference is your root won't be moving, this will ensure all your deformations aren't moving very far from origin.

Now, you have the geometry deforming at origin, great! Now what? Well, your render geometry (the geometry that will finally be rendered and moving with the root) should be parent under your root and inheriting transforms. To inherit the local deformations from deformation layer, you can either connect your shape nodes directly or you can do a blendshape (set to local space).

![Control hierarchy connecting into deformation layer](Untitled%202.png)

Control hierarchy connecting into deformation layer

Perfect, now you have all your deformations on origin and you're able to move the control root as far as you'd like without any jittering.

![Moved a billion units from origin.](Untitled%203.png)

Moved a billion units from origin.

That's pretty much it, it's a pretty simple solution, but it works well. Of course, there are some cases where this won't work well, like games, since the geometry can't be split into layers for a game rig. As well as some simulations that need to be performing while the character is moving through world space (though this works quite well for certain simulations that don't need to worry about that)