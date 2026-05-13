---
date: 2026-04-26T20:59:00
tags:
  - maya
  - math
  - rig
draft: true
---
A few years ago, I saw this post on Twitter about skirt collisions (My original post: https://x.com/Ollarin/status/1703843501123792968), which looked really cool, but the author didn't share how it was done. Which inspired me to come up with a way to achieve similar results. 



# How does it work?

I ended up with just using some simple Dot and Cross products to calculate when to start colliding with the object we wanted to move away, we used a simple dot product to calculate that, and for the angle of the twist while the "Cylinder" was moving through all the different plates.

$$
\begin{aligned}
R &= Original\ Rotation\ Matrix\\
R_{bend} &= Aim \ Matrix\\
Roll &= R*Bend^{-1}\\
A \cdot B\\
\end{aligned}
$$

pass

# Implementation

pass

###  Maya Nodes
Pass

### Maya Bifrost
pass

### Unreal Engine Control rig
Pass
