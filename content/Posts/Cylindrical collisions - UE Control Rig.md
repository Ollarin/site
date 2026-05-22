---
date: 2026-04-26T20:59:00
tags:
  - math
  - rig
  - unreal
  - control_rig
draft: true
---
![[ue_cr_cylindrical_collision.gif]]

A few years ago, I saw this post on Twitter about skirt collisions (My original post: https://x.com/Ollarin/status/1703843501123792968), which looked really cool, but the author didn't share how it was done. Which inspired me to come up with a way to achieve similar results.

So here I'll go about documenting the method I ended up with, which seems to work relatively well for what it is. 

I've been asked a few times on how I set it all up, so I'm going to try and explain it below, implementing it in Maya nodes, Bifrost and control rig in unreal engine. 

# How does it work?

The core of the setup is done using just using some simple Dot products and Cross products to calculate when to start colliding with the object we wanted to move away, we used a simple dot product to calculate that, and for the angle of the twist while the "Cylinder" was moving through all the different plates.

$$
\begin{aligned}
R &= Original\ Rotation\ Matrix\\
R_{bend} &= Aim \ Matrix\\
Roll &= R*Bend^{-1}\\
A \cdot B\\
\end{aligned}
$$



# Implementation

pass

###  Maya Nodes
Pass

### Maya Bifrost
pass

### Unreal Engine Control rig
Pass
