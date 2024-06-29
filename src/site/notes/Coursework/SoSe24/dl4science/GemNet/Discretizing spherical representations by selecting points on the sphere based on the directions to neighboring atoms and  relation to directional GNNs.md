---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/discretizing-spherical-representations-by-selecting-points-on-the-sphere-based-on-the-directions-to-neighboring-atoms-and-relation-to-directional-gn-ns/","noteIcon":""}
---

---
We can connect this model to GNNs by interpreting these directions as [[Coursework/SoSe24/dl4science/GemNet/Directed Edge Embeddings\|Directed Edge Embeddings]]. For example, the embedding direction of atom a would be defined by atom c, resulting in the edge embedding eca. Updating the spherical representation of atom a based on atom b then corresponds to two-hop message passing between the edges eca and edb via eba, with atoms c and d defining the embedding directions. This message passing formalism naturally allows us to obtain the molecule’s [[full geometrical information (distances, angles, and dihedral angles)\|full geometrical information (distances, angles, and dihedral angles)]], and the direct correspondence proves the model’s universality.

We call this edge-based two-hop message passing scheme geometric message passing

![Screenshot 2024-06-28 at 21.09.57.png](/img/user/Attachments/Screenshot%202024-06-28%20at%2021.09.57.png)

