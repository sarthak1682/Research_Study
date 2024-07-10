---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/repr-of-so-3/","noteIcon":""}
---

---
What is SO(3)
his is the group of all rotations about the origin of three-dimensional Euclidean space R3R3. Each element of SO(3)SO(3)is a 3×33×3 orthogonal matrix with determinant 1. This group captures all possible rotations in 3D space.


What does it mean to represent a Group in general? 
A **representation** of a group G on a vector space V is a way of expressing the elements of G as linear transformations (matrices) acting on V. More formally, it's a homomorphism from G to the general linear group GL(V) of invertible linear transformations on V. This means that each group element corresponds to an invertible matrix, and the group operation (e.g., composition) corresponds to matrix multiplication.

p: SO(3) -> GL(V)

In three dimensions, the most straightforward representation is V=R3V=R3 itself, where each rotation R∈SO(3)R∈SO(3) acts on a vector v∈R3v∈R3 by matrix multiplication: v↦Rvv↦Rv.


Repr. of SO(3)?
To say a space or function is a representation of SO(3)SO(3) means that the space or function can accommodate the symmetries and transformations described by SO(3)SO(3)

[[Coursework/SoSe24/dl4science/GemNet/wigner-D matrix\|wigner-D matrix]]

Certainly! Let's delve into the exact differences between the 2-sphere \( S^2 \) and the rotation group \( SO(3) \).

### Definitions

- **\( S^2 \) (2-Sphere)**:
  - **Definition**: \( S^2 \) is the set of all points in three-dimensional space that are at a fixed distance (radius) from a central point. Mathematically, it is defined as:
    \[
    S^2 = \{ (x, y, z) \in \mathbb{R}^3 \mid x^2 + y^2 + z^2 = 1 \}
    \]
  - **Dimension**: \( S^2 \) is a 2-dimensional manifold embedded in 3-dimensional space.
  - **Properties**: \( S^2 \) has the topology of a sphere, meaning it is a surface with no edges and is finite in extent. It is a curved, closed surface.

- **\( SO(3) \) (Special Orthogonal Group in 3 Dimensions)**:
  - **Definition**: \( SO(3) \) is the group of all rotations about the origin of three-dimensional Euclidean space. Each element of \( SO(3) \) is a 3x3 orthogonal matrix \( R \) with determinant 1, representing a rotation:
    \[
    SO(3) = \{ R \in \mathbb{R}^{3 \times 3} \mid R^T R = I, \det(R) = 1 \}
    \]
  - **Dimension**: \( SO(3) \) is a 3-dimensional Lie group.
  - **Properties**: \( SO(3) \) describes rotational symmetries in three-dimensional space. It is non-Abelian, meaning the group operation (matrix multiplication) is not commutative.


SO(3) vs S^2

### Key Differences

1. **Nature**:
   - \( S^2 \) is a **manifold**, specifically a 2-dimensional surface.
   - \( SO(3) \) is a **Lie group**, which is a group that is also a differentiable manifold. It represents the symmetries (rotations) in three-dimensional space.

2. **Dimensionality**:
   - \( S^2 \) is 2-dimensional.
   - \( SO(3) \) is 3-dimensional.

3. **Mathematical Representation**:
   - Points on \( S^2 \) are represented by coordinates \((x, y, z)\) satisfying \( x^2 + y^2 + z^2 = 1 \).
   - Elements of \( SO(3) \) are represented by 3x3 orthogonal matrices with determinant 1.

4. **Topology**:
   - \( S^2 \) has the topology of a sphere.
   - \( SO(3) \) has the topology of a real projective space \( \mathbb{RP}^3 \), which can be thought of as a 3-dimensional sphere with antipodal points identified.

5. **Role in Physics**:
   - \( S^2 \) is often used to represent the set of directions or orientations of a vector in three-dimensional space.
   - \( SO(3) \) represents the group of rotations and is used to describe how objects or coordinate systems can be rotated in three-dimensional space.

### Relationship Between \( S^2 \) and \( SO(3) \)

There is an important relationship between \( S^2 \) and \( SO(3) \). A rotation in \( SO(3) \) can act on points on \( S^2 \). Specifically, any rotation in \( SO(3) \) moves points on \( S^2 \) to other points on \( S^2 \), preserving the spherical structure.

Additionally, while \( SO(3) \) can be thought of as parameterizing all possible orientations of an object in 3D space, \( S^2 \) can be thought of as parameterizing all possible directions for a given vector. Each element of \( SO(3) \) acts as a rotation that moves a vector on \( S^2 \) to another vector on \( S^2 \).

### Summary

- **\( S^2 \)** is a 2-dimensional manifold representing the set of points equidistant from a center in 3D space.
- **\( SO(3) \)** is a 3-dimensional Lie group representing all rotations in 3D space.
- They differ in dimensionality, nature (manifold vs. group), and their roles in mathematics and physics.
- \( SO(3) \) can act on \( S^2 \), demonstrating the relationship between rotations and directions in three-dimensional space.