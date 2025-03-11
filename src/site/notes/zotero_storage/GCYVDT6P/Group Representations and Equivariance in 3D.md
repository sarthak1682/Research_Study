---
{"dg-publish":true,"permalink":"/zotero-storage/gcyvdt-6-p/group-representations-and-equivariance-in-3-d/","noteIcon":""}
---

---
# Group Representations and Equivariance in 3D: A Comprehensive Explanation

## 1. Group Representations

A **group representation** $D$ is a mathematical structure that maps elements of a group $G$ to square matrices, preserving the group's structure. Specifically, for any elements $g, h \in G$:

$$D(g)D(h) = D(gh)$$

This property ensures that the matrix multiplication mirrors the group operation, making the representation ==a homomorphism from the group to the space of square matrices.==

## 2. Equivariance

A function $\mathcal{L}: \mathcal{X} \rightarrow \mathcal{Y}$ between vector spaces is **equivariant** with respect to a group $G$ and representations $D^{\mathcal{X}}$ and $D^{\mathcal{Y}}$ if for all $g \in G$:

$$\mathcal{L} \circ D^{\mathcal{X}}(g) = D^{\mathcal{Y}}(g) \circ \mathcal{L}$$

This means that applying a transformation to the input and then the function gives the same result as applying the function first and then transforming the output. In other words, the function "respects" the group transformations.

### 2.1 Invariance as a Special Case

**Invariance** is a specific type of equivariance where the output representation $D^{\mathcal{Y}}(g)$ is the identity matrix for all $g$. This means the output of the function doesn't change when transformations are applied to the input.

## 3. 3D Symmetry Operations

In the context of 3D space, we are concerned with symmetry operations including:

- Rotations (changing orientation)
- Translations (changing position)
- Permutations (reordering points)

## 4. Composition Property

When two equivariant networks $\mathcal{L}_1$ and $\mathcal{L}_2$ are composed, the result $\mathcal{L}_2 \circ \mathcal{L}_1$ is also equivariant. This is a powerful property because it means:

1. We can build complex equivariant networks by stacking equivariant layers
2. Proving equivariance for individual layers is sufficient to guarantee equivariance of the entire network

## 5. Group Composition

If a network is equivariant with respect to transformations $g$ and $h$, then it is also equivariant to their composition $gh$. This means that demonstrating equivariance to basic transformations (rotation, translation, permutation) individually is sufficient to prove equivariance to all possible combinations of these transformations.

## 6. Tensor Field Networks

Tensor field networks operate on points with associated features:

- They take a set $S$ of vectors in $\mathbb{R}^3$ (points in 3D space)
- Each point has an associated feature vector in space $\mathcal{X}$
- The network outputs a vector in space $\mathcal{Y}$ for each point

This can be expressed as:

$$\mathcal{L}(\vec{r}_a, x_a) = (\vec{r}_a, y_a)$$

where:

- $\vec{r}_a \in \mathbb{R}^3$ are the point coordinates
- $x_a \in \mathcal{X}$ are the input feature vectors
- $y_a \in \mathcal{Y}$ are the output feature vectors
- $a$ is an indexing scheme over the points in set $S$

The combination of 3D coordinates with feature vectors can be represented as $\mathbb{R}^3 \oplus \mathcal{X}$, where $\oplus$ denotes concatenation.


## 8 Types of Equivariance in 3D Neural Networks
### 8.1 Permutation Equivariance

**Condition**: $\mathcal{L} \circ \mathcal{P}_\sigma = \mathcal{P}_\sigma \circ \mathcal{L}$

Where $\mathcal{P}_\sigma(\vec{r}_a, x_a) := (\vec{r}_{\sigma(a)}, x_{\sigma(a)})$ and $\sigma$ permutes the points to which the indices refer.

Permutation equivariance means that the output of the network should not depend on the arbitrary ordering of the input points. This is achieved by treating point clouds as unordered sets of points, rather than ordered lists.

### 8.2 Translation Equivariance

**Condition**: $\mathcal{L} \circ \mathcal{T}_t = \mathcal{T}_t \circ \mathcal{L}$

Where $\mathcal{T}_t(\vec{r}_a, x_a) := (\vec{r}_a + \vec{t}, x_a)$. This condition is analogous to the translation equivariance condition for Convolutional Neural Networks (CNNs).

Translation equivariance means that shifting all input points by a vector $\vec{t}$ should result in outputs that are shifted by the same vector.

Translation equivariance is achieved when the network only uses relative positions (differences between points $\vec{r}_i - \vec{r}_j$) rather than absolute positions. This ensures that the network's behavior doesn't change when the entire point cloud is translated in space.

### 8.3 Rotation Equivariance

**Condition**: $\mathcal{L} \circ [R(g) \oplus D^{\mathcal{X}}(g)] = [R(g) \oplus D^{\mathcal{Y}}(g)] \circ \mathcal{L}$

Where:

- $SO(3)$ is the group of 3D rotations (a 3-dimensional manifold)
- $R(g)$ represents the action of rotation $g \in SO(3)$ on coordinates $\vec{r} \in \mathbb{R}^3$
- $D^{\mathcal{X}}(g)$ is the representation of $SO(3)$ acting on the input feature space $\mathcal{X}$
- $D^{\mathcal{Y}}(g)$ is the representation of $SO(3)$ acting on the output feature space $\mathcal{Y}$

The condition expanded means: $[R(g) \oplus D^{\mathcal{X}}(g)] (\vec{r}_a, x_a) = (R(g)\vec{r}_a, D^{\mathcal{X}}(g)x_a)$

Rotation equivariance is achieved by:

1. Using convolution filters with special forms
2. Decomposing features into types (scalars, vectors, higher tensors) based on how they transform under rotation
3. Using irreducible representations of $SO(3)$

The irreducible representations of $SO(3)$ have dimensions $2l + 1$ for $l \in \mathbb{N}$ (including $l = 0$) and are unitary. The "rotation order" $l$ corresponds to how features transform:

- $l = 0$: Scalars (invariant under rotation)
- $l = 1$: Vectors in 3-space (transform like coordinates)
- $l = 2$: Symmetric traceless matrices (transform like quadrupoles)

The group elements are represented by $D^{(l)}$, called Wigner D-matrices:

- For scalars: $D^{(0)}(g) = 1$ (identity, no change under rotation)
- For 3-space vectors: $D^{(1)}(g) = R(g)$ (rotates like coordinates)

This mathematical formulation ensures that when input points and features are rotated, the output features transform according to the appropriate representation of the rotation group.


# Tensor Field Network Layers: Detailed Explanation

## 1. Overview of Tensor Field Networks

Tensor Field Networks (TFNs) are specialized neural network architectures designed to process point clouds while maintaining equivariance to 3D transformations. The key characteristics of TFNs are:

- Each layer processes a set of points in ℝ³
- Each point has an associated feature vector in a representation of SO(3)
- The network maintains equivariance to permutation, translation, and rotation

## 2. Feature Representation

### 2.1 Irreducible Representations

Features in TFNs are organized according to how they transform under rotation:

- Features are decomposed into irreducible representations of SO(3)
- Multiple instances of each rotation-order (l) can exist, analogous to channels in CNNs
- Features are encoded in a structure denoted as $V^{(l)}_{\text{in/out}}$, implemented as a dictionary with:
    - Key: tuple (point_index, channel_index, representation_index)
    - Value: corresponding feature vector of dimension (2l+1)

This structure allows the network to track how different feature types transform under rotation.

### 2.2 Feature Types by Rotation Order

- **l=0**: Scalar features (dimension 1) - invariant to rotation
- **l=1**: Vector features (dimension 3) - transform like spatial vectors
- **l=2**: Tensor features (dimension 5) - transform like quadrupoles

## 3. Layer Equivariance Properties

All TFN layers are designed to maintain three types of equivariance:

1. **Permutation equivariance**: Reordering input points results in correspondingly reordered outputs
2. **Translation equivariance**: Shifting input points results in shifted outputs
3. **Rotation equivariance**: Rotating input points and their features results in appropriately rotated output features

## 4. Point Convolution Layer

The point convolution is the core operation in TFNs, generalizing standard convolutions to irregular point clouds.

### 4.1 Operation

For each point a:

- Considers all other points as inputs
- Uses both relative locations and feature values
- Applies a rotation-equivariant filter to the relative positions

### 4.2 Spherical Harmonics

Spherical harmonics $Y^{(l)}_m$ are crucial to achieving rotation equivariance:

- They are functions mapping points on a sphere to complex or real numbers
- For l=0: $Y^{(0)}(r̂) ∝ 1$ (scalar, invariant to rotation)
- For l=1: $Y^{(1)}(r̂) ∝ r̂$ (transforms like a vector)

These functions are equivariant to SO(3), meaning for all $g ∈ SO(3)$ and unit vector $r̂$:

$$Y^{(l)}_m(R(g)r̂) = \sum_{m'} D^{(l)}_{mm'}(g)Y^{(l)}_{m'}(r̂)$$

Where $D^{(l)}_{mm'}(g)$ are the Wigner D-matrices representing the rotation.

### 4.3 Rotation-Equivariant Filters

To achieve rotation equivariance, filters in TFNs must have a specific form:

$$F^{(l_i,l_j)}_{ln}(r̂) = R^{(l_i,l_j)}_l(r)Y^{(l_n)}_n(r̂)$$

Where:

- $l_i$ and $l_j$ are the rotation orders of input and filter
- $R^{(l_i,l_j)}_l(r): \mathbb{R}_{≥0} → \mathbb{R}$ are learned radial functions
- $Y^{(l_n)}_n(r̂)$ are spherical harmonics evaluated at the unit direction $r̂$

This structure ensures that the filters inherit the transformation properties of spherical harmonics. The approach is analogous to using circular harmonics in 2D CNNs, with additional complexity due to the non-commutativity of 3D rotations.

## 5. Combining Representations using Tensor Products

### 5.1 Tensor Product Definition

A tensor product combines two representations $D^A$ and $D^B$ to create a new representation $D^A ⊗ D^B$ over the vector space $A ⊗ B$. The crucial property is that the tensor product is itself equivariant:

$$D^A ⊗ D^B = D^{A⊗B}$$

### 5.2 Clebsch-Gordan Coefficients

For irreducible representations of orders $l_1$ and $l_2$, the tensor product is calculated using Clebsch-Gordan coefficients:

$$(u ⊗ v)^{(l)}_m = \sum_{m_1=-l_1}^{l_1} \sum_{m_2=-l_2}^{l_2} C^{(l,m)}_{(l_1,m_1)(l_2,m_2)} u^{(l_1)}_{m_1} v^{(l_2)}_{m_2}$$

Where:

- $C^{(l,m)}_{(l_1,m_1)(l_2,m_2)}$ are the Clebsch-Gordan coefficients
- The tensor product produces non-zero values only for $l$ between $|l_1-l_2|$ and $(l_1+l_2)$ inclusive

For simple cases (l=0 and l=1), the coefficients reduce to familiar operations:

- For scalar × scalar → scalar: $C^{(0,0)}_{(0,0)(0,0)} ∝ δ_{ij}$ (simple multiplication)
- For scalar × vector → vector: $C^{(1,i)}_{(0,0)(1,i)} ∝ ϵ_{ijk}$ (scaling the vector)

## 6. Network Architecture

A complete TFN consists of:

1. Input layer that converts raw point cloud data into the tensor field representation
2. Multiple equivariant convolution layers using the specialized filters described above
3. Operations for combining features across different rotation orders using tensor products
4. Output layer that produces the desired equivariant or invariant outputs

## 7. Practical Considerations

- TFNs are more computationally intensive than standard point cloud networks
- The specialized structure guarantees equivariance properties without needing to learn them
- The use of spherical harmonics and Clebsch-Gordan coefficients requires careful implementation
- This approach enables strong generalization across 3D transformations with fewer parameters

The mathematical formalism provides a principled way to construct neural networks that respect the symmetries of 3D Euclidean space, making them particularly suitable for applications in physics, chemistry, computer vision, and graphics.


---

# Equivariant Neural Networks: Mathematical Foundation

This document explains the key mathematical concepts in the provided research paper on equivariant neural networks.

## 1. Layer Definition (Section 4.1.3)

Equivariant neural networks are designed to respect symmetries in the data. The paper defines a comprehensive pointwise convolution layer that preserves these symmetries.

### Core Equation

$$C^{(l,j)}_{(\vec{r}, m)}(\vec{x}, {f^{(l')}_{m'}}) := \sum_{m',m''} C^{(l,j,m_c)}_{(l',m')(l'',m'')} \sum_{k,S} F^{(l'',L)}_{km''}(\vec{r}_k)V^{(l')}_{km'}$$

Where:

- $\vec{r}_k = \vec{r} - \vec{r}_k$ (vector between positions)
- Subscripts $l$, $l'$, and $l''$ denote the representations of input, filter, and output
- Point convolution of an $l'$ filter on an $l$ input yields outputs at rotation orders $l''$
- $l''$ can be any integer between $|l-l'|$ and $l+l'$ (inclusive)

### Design Flexibility

When designing a network, not all possible output rotation orders need to be calculated, giving flexibility in the architecture design.

## 2. Self-Interaction Layers (Section 4.2)

Self-interaction layers are a critical component inspired by Schütt et al. (2018). They serve multiple purposes:

1. Scale feature vectors elementwise
2. Mix components of feature vectors at each point
3. Functionally equivalent to 1×1 convolutions
4. Act like scalar filters ($l=0$)

### Mathematical Representation

$$\sum_l W^{(l)}V^{(l)}$$

### Key Properties

- **Different weights for different rotation orders**: Each rotation order may have different numbers of channels, requiring different weight matrices
- **Weight sharing across $m$**: For a given order, the same weights are used for every $m$ to maintain equivariance
- **Bias terms**: For $l=0$ channels, bias terms may be included
- **Commutation property**: The $D$-matrices commute with the weight matrix $W$ because there's no representation index
- **Equivariance**: This layer is equivariant for $l>0$, and for $l=0$ the equivariance is trivial since $D^{(0)}=1$

## 3. Nonlinearity Layers (Section 4.3)

The nonlinearity layer applies transformations differently depending on the channel type:

### For $l=0$ channels (scalars)

$$\eta^{(l)}(V^{(l)} + b^{(l)})$$

### For $l>0$ channels (vector-like)

$$\eta^{(l)}(||V^{(l)}||_2 + b^{(l)})V^{(l)}_m$$

Where:

- $||V^{(l)}||_2 := \sqrt{\sum_m |V^{(l)}_m|^2}$ is the L2 norm across the $m$ dimension
- $\eta^{(l)}: \mathbb{R} \to \mathbb{R}$ are nonlinear functions that can differ for each $l$
- $b^{(l)}$ are bias terms

### Equivariance Property

This layer preserves equivariance because $D$ is a unitary representation: $$||D^{(l)}V^{(l)}|| = ||V^{(l)}||$$

Therefore, this layer performs a scalar transformation in the representation index $m$, maintaining equivariance.

## Significance in Network Design

The paper emphasizes that the equivariance of these layers is the core of their theoretical result. By carefully designing each layer component to maintain equivariance properties, the entire network inherits these symmetry-preserving characteristics.

This mathematical construction enables neural networks that can recognize patterns regardless of rotational orientation, which is particularly valuable in domains like molecular modeling, computer vision, and physical simulations where orientation should not affect predictions.