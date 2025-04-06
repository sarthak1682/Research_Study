---
{"dg-publish":true,"permalink":"/deepchem/featurizer-for-tf-ns/","noteIcon":""}
---

---


## Examples of Model-Specific Featurizers

- AtomicConvFeaturizer: Designed for the AtomicConvModel

- WeaveFeaturizer: Designed for the WeaveModel

- MolGraphConvFeaturizer: Designed for graph convolutional models

- EquivariantGraphFeaturizer: Designed for SE(3)-equivariant models


## Why TFNs Need a Specialized Featurizer

- Tensor Order Representation:

- Unlike SE(3) Transformers which primarily use scalar (degree 0) and vector (degree 1) features, TFNs can efficiently handle higher-order tensors (degree 2+)

- Need to extract and represent these higher-order geometric features from molecular structures

- Local Reference Frames:

- TFNs benefit from having well-defined local reference frames for each atom

- These frames provide a basis for representing directional information that transforms correctly under rotation

- Critical for capturing bond orientations and molecular shape

- Multi-Scale Representation:

- TFNs can process information at multiple scales simultaneously

- Need features that capture both local (bonding) and non-local (conformational) information

- Enables learning hierarchical representations of molecular structure

- Spherical Tensor Algebra:

- TFNs use spherical tensor algebra for equivariant operations

- Featurizer needs to provide inputs in a form compatible with these operations

- Requires careful handling of geometric information to ensure proper transformation properties