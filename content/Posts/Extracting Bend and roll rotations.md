---
date: 2015-09-23T00:00:00
tags:
  - maya
  - math
  - rig
draft: true
---
# Overview

Distinguishing and extracting 'Swing' (bending rotations) from 'Twist' (rolling rotations) can be beneficial in areas like physics, engineering, and computer animation. 'Swing' refers to bending rotations, while 'Twist' indicates a spin around the object's own axis. Separating these rotations allows for more precise and controlled movement, useful in many applications.

Bend will contain the yaw and pitch rotations, while the roll will only contain roll. 


$$
\begin{aligned}
R &= \text{Original Rotation Matrix} \\
B &= \text{Aim Matrix}
\end{aligned}
$$

# Bend driving twist

$$
\begin{aligned}
R &= Original\ Rotation\ Matrix\\
Bend &= Aim \ Matrix\\
Roll &= R*Bend^{-1}\\
\end{aligned}
$$

<aside>
<img src="https://www.notion.so/icons/info-alternate_green.svg" alt="https://www.notion.so/icons/info-alternate_green.svg" width="40px" /> What we’re doing here is taking the original rotation matrix and removing the bend rotations from it. Leaving us with the remainder that is the roll rotations.

</aside>

---

### Constraints

Leverage constraint nodes to do this calculations, you’re going to manually make connections and not let Maya do it. 

```python
from maya import cmds

```

### Matrix Nodes

Leverage constraint nodes to do this calculations, you’re going to manually make connections and not let Maya do it. 

```python
from maya import cmds

```

### Bifrost

Leverage constraint nodes to do this calculations, you’re going to manually make connections and not let Maya do it. 

```python
from maya import cmds

```

# Roll driving bend

$$
\begin{align}
R &= Original\ Rotation\ Matrix\\
RawBend &= Aim \ Matrix\\
Roll &= R*B^{-1}\\
CleanBend &= R*Roll^{-1}
\end{align}
$$

<aside>
<img src="https://www.notion.so/icons/info-alternate_green.svg" alt="https://www.notion.so/icons/info-alternate_green.svg" width="40px" /> What we’re doing here is essentially taking the original rotation matrix, and removing the bend rotations from it. Leaving us with the remainder that is the roll rotations.

</aside>