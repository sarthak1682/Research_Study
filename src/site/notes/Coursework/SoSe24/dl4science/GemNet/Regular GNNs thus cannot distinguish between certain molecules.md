---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/regular-gn-ns-thus-cannot-distinguish-between-certain-molecules/","noteIcon":""}
---

---
Well-known examples of molecules that regular Graph Neural Networks (GNNs) struggle to distinguish include:

1. Graphs with different chirality: Molecules like enantiomers or diastereomers, which have the same connectivity but different spatial arrangements of atoms, can be challenging for regular GNNs to differentiate.

"the neighborhoods of chiral centers in enantiomers are usually structurally equivalent, making it difficult for GNNs"

"Enantiomers **differ only in the three-dimensional arrangement of their atoms in space, but their two-dimensional graph representations, which regular GNNs operate on, are identical**. This is why regular GNNs cannot distinguish between enantiomers or different chiralities of the same molecule."


2. Graphs with identical substructures in different orientations: Molecules with identical functional groups or substructures arranged in different orientations or conformations may not be distinguished effectively by standard GNNs.

3. Graphs with different ring conformations: Molecules with different ring conformations, such as chair vs. boat forms in cyclohexane derivatives, can pose difficulties for regular GNNs in distinguishing between them.

These examples highlight the limitations of regular GNNs in capturing fine-grained structural differences in molecules, especially when such differences are subtle and involve spatial arrangements or conformations.