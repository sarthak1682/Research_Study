---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/how-is-it-connected-to-gn-ns/","noteIcon":""}
---

---
We can connect this model to GNNs by interpreting these directions as directed edge embeddings. For example, the embedding direction of atom a would be defined by atom c, resulting in the edge embedding eca. Updating the spherical representation of atom a based on atom b then corresponds to two-hop message passing between the edges eca and edb via eba, with atoms c and d defining the embedding directions. This message passing formalism naturally allows us to obtain the molecule’s full geometrical information (distances, angles, and dihedral angles), and the direct correspondence proves the model’s universality. 

We call this edge-based two-hop message passing scheme geometric message passing, and [[propose multiple structural enhancements to improve the practical performance of this formalism\|propose multiple structural enhancements to improve the practical performance of this formalism]]. 

Based on these changes we develop the [[highly accurate\|highly accurate]] and [[sample-efficient geometric message passing neural network (GemNet)\|sample-efficient geometric message passing neural network (GemNet)]]. We furthermore show that [[Coursework/SoSe24/dl4science/GemNet/stabilizing the variance of GemNet’s activations with predetermined scaling factors yields significant improvements over regular normalization layers.\|stabilizing the variance of GemNet’s activations with predetermined scaling factors yields significant improvements over regular normalization layers.]] 
