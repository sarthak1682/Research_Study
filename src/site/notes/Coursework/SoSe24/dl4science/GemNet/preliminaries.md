---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/preliminaries/","noteIcon":""}
---

---
We consider a 3D Point cloud. [[Coursework/SoSe24/dl4science/GemNet/Point Cloud Models\|Point Cloud Models]] with n points (atoms), each associated with a position and a set of rotationally invariant features (e.g. atom types), defined as 
$$ X\in \mathbb{R}^{3*n}, H_{in} \in \mathbb{R}^{h*n}   $$

In this section we define model classes by sets of functions F. As a first step, we are interested in proving that the set F defining our model is equal to the full set of functions G′ that are invariant to the group of translations T3 and rotations SO(3), and equivariant to the group of permutations Sn. (Translation Invariance, Rotational Invariance, Perm. Equiv.)
	intro to group theory here? 

We denote the codomain of functions in G′ as W n T , where WT is some representation of SO(3). We denote a vector’s norm by x = ‖x‖2, its direction by ˆ x = x/x, and the relative position by xba = xb − xa. Proofs are deferred to the appendix. Note that this section is not intended as an introduction to the SO(3) group.


